# Ledger API

## Contents
1. Import and start
2. Batches and assessments
3. Full texts and decisions
4. Workbooks and recovery

## Import and start

Use bundled `scripts/screening_chat.py` with local Python/openpyxl. It has no network/model calls. It validates structure, exact quotes and counts, not the semantic correctness of a review.

```python
import importlib.util
spec = importlib.util.spec_from_file_location('ledger', '/actual/skill/path/scripts/screening_chat.py')
L = importlib.util.module_from_spec(spec)
spec.loader.exec_module(L)
records, info = L.import_records('/actual/upload.nbib')
s = L.new_project(records, criteria, question=question, scope=actual_scope,
                  search_log=actual_search_log, language='en', tutorial=False)
candidates = L.duplicate_candidates(s['records'])
s = L.confirm_duplicates(s, user_confirmed_mapping, user_text=actual_confirmation)
s = L.start_screening(s, user_text=actual_start_confirmation)
L.save_state(s, '/working/chat-state.json')
```

Criteria: `{'id':'C01','kind':'include'|'exclude','text':actual_approved_criterion}`. At least one inclusion criterion is required. Preserve IDs after normalization. Duplicate map: `{removed_record_id: retained_record_id}`. Same-study report links belong separately in `link_studies`.

CSV supports common English/Korean title, abstract, authors, year, DOI, PMID and record_id headers. NBIB/PubMed text and RIS continuation lines are supported. IDs are assigned only when missing. Duplicate supplied IDs and missing titles are rejected rather than silently dropping records. Identify non-UTF-8 encoding before explicitly converting to a separate UTF-8 copy; preserve the original.

`new_project` is preparation, not user approval. `start_screening` freezes records, protocol and duplicates. Do not mutate them after starting. All mutating functions return a **new state**: always assign it, then save.

## Batches and assessments

```python
# First show only the actual titles/abstracts. The student records privately.
L.write_student_form(s, 'tiab', ids, '/working/private-decisions.xlsx')  # optional
s = L.prepare_batch(s, 'tiab', ids, user_text=actual_confirmation)
# waive=True only for an explicit request to see AI before private recording.
```

One assessment per approved criterion:

```python
assessments = [
    {'criterion_id': 'C01', 'status': 'met', 'basis': 'direct',
     'evidence': actual_short_verbatim_quote, 'location': 'abstract',
     'explanation': actual_explanation},
    {'criterion_id': 'C02', 'status': 'unclear', 'basis': 'insufficient',
     'evidence': '', 'location': None, 'explanation': what_is_missing},
]
s = L.record_ai(s, 'tiab', rid, assessments, student_seen='no',
                previous_stage_seen='no', model=None, context_note=actual_context)
```

Stage 1 locations: `title`, `abstract`, `year`, `authors`, `doi`, `pmid`. Stage 2 location: actual 1-based PDF page number as integer or string. `met/not_met` need a quote present in the field/page and `direct/counterevidence`. `unclear` uses empty quote/location and `insufficient`. A quotation's presence does not prove a different fact: an English abstract does not prove the full text's language.

```python
s = L.record_ai_issue(s, stage, rid, actual_error)
# Save progress and continue other IDs. An execution error is not an AI Hold.
```

After AI results have been saved and shown, receive the prewritten student answers:

```python
s = L.record_student(s, 'tiab', rid, 'include', actual_reason,
                     user_text=actual_statement, prewritten='yes')
s = L.record_final(s, 'tiab', rid, 'include', actual_final_reason,
                   user_text=actual_final_confirmation)
```

Canonical decisions: `include`, `maybe` (Hold), `exclude`. Exclusions require an approved `criterion_id` and concrete reason. Use the actual student statement; never fabricate one to satisfy validation. `prewritten`: yes/no/unknown. If answers arrive before AI, record as received; `record_ai` forces `student_seen=yes` when student answers are already in that row. Report any other actual exposure too.

`confirm_matching(s, stage, ids, user_text=...)` atomically confirms only unfinalized include/include or exclude/exclude pairs. Show the exact list and evidence first. It preserves individual reasons and criteria. Holds and previously finalized rows are not eligible.

## Full texts and decisions

```python
s = L.start_fulltext(s, user_text=actual_transition_confirmation)
s = L.set_material(s, rid, retrieval='retrieved', filename=actual_filename,
                   identity='confirmed', read_status='complete',
                   pages=[{'page': 1, 'text': actual_page_1_text},
                          {'page': 2, 'text': actual_page_2_text}])
s = L.prepare_batch(s, 'fulltext', batch_ids, user_text=actual_private_reading_confirmation)
# record_ai / record_student / record_final now use stage='fulltext'.
```

Targets derive exclusively from completed Stage 1 final inclusions. Use pending/partial/error accurately. Complete requires actual identification and reading of the full relevant text, tables and appendices; the code cannot inspect an unseen PDF or verify that the first page is the whole paper.

```python
s = L.set_material(s, rid, retrieval='not_retrieved', note=actual_reason,
                   user_text=actual_user_confirmation)
```

Missing full text is separate from eligibility; no AI/final eligibility decision can coexist with not_retrieved. A later acquired PDF can replace pending/missing material before AI/final evaluation. Replacing evaluated material or initial student/AI decisions requires a separate documented round retaining the earlier workbook.

Final decisions may change with explicit student statements; history stores before/after. Stage 1 locks once Stage 2 starts. `link_studies(s, verified_mapping, user_text=confirmation)` records verified report-to-study identities. Unknown links leave the included-study count blank.

## Workbooks and recovery

```python
counts = L.summary(s)
name = 'literature-screening-chat-results.xlsx' if counts['complete'] else 'literature-screening-chat-progress.xlsx'
L.save_state(s, '/working/chat-state.json')
L.write_workbook(s, '/working/' + name)
s, edits = L.read_workbook('/actual/uploaded-progress.xlsx')
```

Inspect `edits` before continuing. All visible sheets, including criteria, records and both stages, are compared with the saved ledger. Changes are not automatically applied. Confirm actual final-decision edits then use `record_final`; protected source/criteria/initial/AI changes need a new project or round retaining the old file. Row/column reordering is supported when IDs and headers remain unchanged. Added/deleted/renamed rows, IDs, sheets, headers and formulas are rejected for reconciliation. Preserve the uploaded edits; do not bypass guards or silently discard them.

The hidden state is compressed/checksummed against accidental damage, not signed, access-controlled or evidence of independence. Export validates an exact round trip. Formula-like source strings are written as literal text. Long visible cells are labelled as shortened; full values remain in the ledger. Do not call a shortened display the whole source.

The optional student form has no resume ledger. Read a completed form as actual student answers and match IDs to the batch. If it arrives before AI, record that exposure. It is not an independently sealed response file.

Assistant-only CLI: `python screening_chat.py import INPUT OUTPUT.json`, `workbook STATE.json OUTPUT.xlsx`, `inspect WORKBOOK.xlsx`. Never ask students to run these commands.
