# Literature Screening — Claude Skill

문헌고찰을 위한 문헌선별을 Claude에서 안내하는 학생용 스킬입니다. 학생이 문헌을 먼저 읽고 판단한 뒤 AI 평가와 비교합니다. 1차 제목·초록 선별은 화면에서, 2차 원문 선별은 채팅에서 진행하고 최종 결과를 엑셀로 저장합니다.

![Claude Skill](https://img.shields.io/badge/Claude-Skill-orange.svg)
![Student Version 3.0](https://img.shields.io/badge/Student-v3.0-blue.svg)

**[literature-screening-student.skill 다운로드](https://github.com/Jeongin-Choe-RN/literature-screening-claude-skill/raw/refs/heads/main/literature-screening-student.skill)** · [파일 내용 보기](docs/literature-screening-student.md)

## 주요 기능

- **선별 기준 확인** — 연구질문과 포함·제외 기준을 정리하고 중복 문헌 후보를 확인
- **1차 제목·초록 선별** — 화면에서 한 편씩 읽고 포함·보류·제외를 선택
- **학생·AI 판정 비교** — 최초 판정과 AI 평가의 차이를 확인하고 학생이 최종 판단을 확정
- **2차 원문 선별** — 채팅에 PDF를 첨부해 AI 평가를 받고, 미리 기록한 학생 판정과 비교
- **엑셀 결과 저장** — 학생 최초·AI·최종 판정, 기준별 근거와 쪽수, 제외 사유, 검색 기록과 PRISMA 집계를 보존
- **가상 문헌으로 연습** — 질문·기준·문헌 5편·가상 원문이 준비된 튜토리얼로 사용 순서를 연습

## 다운로드 및 사용 방법

1. 위의 **literature-screening-student.skill 다운로드** 링크로 파일을 저장합니다.
2. Claude의 **스킬 관리 → 스킬 업로드**에서 다운로드한 `literature-screening-student.skill`을 업로드하고 활성화합니다.
3. 새 대화에 검색 보고서와 문헌 목록(NBIB·CSV·RIS 등)을 첨부하고 다음과 같이 입력합니다.

   > literature-screening-student 스킬로 첨부한 문헌의 선별을 시작해 주세요.

   먼저 연습하려면 “문헌선별을 가상 문헌으로 연습하고 싶어요.”라고 요청합니다.

4. 화면에서 연구질문·포함/제외 기준·중복 문헌을 확인합니다.
5. **1차:** 제목과 초록을 읽고 판정합니다. 내 판정을 확정한 뒤 AI와 비교하고 최종 판단을 기록합니다. 포함·제외가 일치한 문헌은 근거 확인 후 함께 확정할 수 있습니다.
6. **2차 시작:** ‘2차는 채팅에서 계속’을 눌러 시작 자료를 한 번 저장해 대화에 첨부합니다. 내려받기가 안 되면 ‘시작 내용 복사’를 사용합니다.
7. **2차 진행:** 원문을 읽고 자신의 판정·근거를 메모장이나 개인 엑셀에 먼저 적어 둡니다. 아직 그 답을 보내지 말고 PDF를 대화 입력창에 첨부해 AI 평가를 받습니다. 이후 미리 적은 학생 판정을 보내 비교하고 최종 판단을 알려 줍니다.
8. 최종 결과 엑셀을 확인하고 저장합니다. 2차의 AI 답변이나 최종 결과를 화면에 다시 입력할 필요는 없습니다.

## 저장하고 이어가기

- **1차 화면:** 지원되는 환경에서는 자동 임시저장됩니다. 작업을 마칠 때는 ‘진행 저장’ 파일도 보관하고, 다음에는 ‘문헌 목록 불러오기’로 엽니다.
- **2차 채팅:** “현재 진행을 엑셀로 저장해 주세요.”라고 요청합니다. 다음에는 최신 엑셀을 첨부해 이어갑니다. 새 대화에서 필요한 원문이 없으면 해당 PDF를 다시 첨부합니다.
- 화면의 자동 임시저장은 채팅의 2차 결과까지 저장하지 않습니다. 엑셀에서 직접 수정한 값은 재개할 때 확인한 뒤 반영합니다.

## 사용 시 유의사항

- **학생이 먼저 판단하고 최종 결정합니다.** AI 평가는 학습과 검토를 돕는 자료이며, 실제 기준과 원문에서 근거를 확인하세요.
- 1차의 포함은 원문 검토 대상이라는 뜻입니다. 정보 부족은 보류하고, 원문 미확보나 PDF 읽기 오류를 적격성 제외로 처리하지 않습니다.
- AI 평가 전에 학생 답을 보내면 그 노출 사실을 기록합니다. 판정 일치율은 정확도나 검증된 독립 평가의 지표가 아닙니다. 보류끼리 일치한 경우와 비교 대기 문헌을 함께 확인하세요.
- 화면 안 AI 평가·PDF 읽기·파일 생성 가능 여부는 Claude 환경에 따라 다릅니다. 1차 화면에 AI 연결이 없으면 요청·답변을 복사하는 안내를 따릅니다. 여러 PDF는 처리 가능한 범위로 나누어 진행할 수 있습니다.
- 엑셀 산출물에는 코드 실행 및 파일 생성 기능이 필요합니다. 설치 환경은 [Claude 공식 스킬 안내](https://support.claude.com/en/articles/12512180-use-skills-in-claude)를 참고하세요.
- 엑셀의 **PRISMA집계**는 다음 흐름도 작성에 사용할 자료이며 완성된 흐름도 그림은 아닙니다. PDF 비교 보고서는 필요할 때 추가로 요청할 수 있습니다.

## 라이선스

별도의 오픈소스 라이선스는 지정하지 않았습니다. 재배포·수정본 배포 등 이용 허락이 필요한 경우 저장소의 Issues에서 문의해 주세요.

## 제작자

**최정인 (Jeongin Choe)**

[nncj91@snu.ac.kr](mailto:nncj91@snu.ac.kr)

## 지도교수

**우경미 (Kyungmi Woo)** — 서울대학교 간호대학 부교수

ANDA Lab: [https://andalab.snu.ac.kr/](https://andalab.snu.ac.kr/)

## 감사의 말

이 도구는 생성형 AI 도구를 활용하여 개발되었습니다. 사용 과정을 세심하게 검토하고 개선 의견을 주신 박소연 선생님(서울대학교 간호대학 박사과정)께 감사드립니다.

---

# Literature Screening — Claude Skill (English)

A Claude skill that helps students screen literature and compare their own judgments with AI assessments. Screen titles and abstracts in an interactive interface, review full texts in chat, and save the results as an Excel workbook.

**[Download literature-screening-student.skill](https://github.com/Jeongin-Choe-RN/literature-screening-claude-skill/raw/refs/heads/main/literature-screening-student.skill)** · [View contents](docs/literature-screening-student.md)

## Features

- **Screening criteria** — clarify the research question and eligibility criteria, and review potential duplicate records
- **Title and abstract screening** — read one record at a time and choose include, hold, or exclude
- **Student–AI comparison** — compare initial judgments with AI assessments before the student confirms final decisions
- **Full-text review in chat** — attach PDFs, obtain AI assessments, and compare them with judgments the student recorded beforehand
- **Excel results** — retain initial, AI, and final decisions; criterion-level evidence and page references; exclusion reasons; search records; and PRISMA counts
- **Fictional practice set** — learn the workflow using a prepared question, criteria, five records, and fictional full texts

## Download & Usage

1. Download `literature-screening-student.skill` using the link above.
2. In Claude’s skill management area, **upload the downloaded skill** and enable it.
3. Start a new conversation, attach the search report and reference list (e.g., NBIB, CSV, or RIS), and enter:

   > Please use the literature-screening-student skill to screen the attached references.

   To practise first, ask: “Please help me practise literature screening with fictional records.”

4. Confirm the research question, eligibility criteria, and duplicate records in the interface.
5. **Stage 1:** read the titles and abstracts and record your judgments. Confirm your initial judgments, compare them with AI, and record final decisions. Matching include/exclude decisions can be finalized together after reviewing the evidence.
6. **Start Stage 2:** use the button to continue full-text review in chat. Save the starting material and attach it to the conversation once, or copy its contents if downloading is unavailable.
7. **Stage 2:** read the full texts and privately record your judgments and reasons first. Attach the PDFs to obtain AI assessments before sending your own answers. Then provide your previously recorded judgments, compare the evidence, and confirm your final decisions.
8. Review and save the Excel workbook. Full-text AI responses and final decisions do not need to be pasted back into the interface.

## Save & Resume

- **Stage 1 interface:** temporary autosave is available in supported environments. Also save the progress file before finishing; use the reference-list import button to reopen it.
- **Stage 2 chat:** ask Claude to save the current progress as an Excel workbook. Attach the latest workbook to resume. Reattach any required PDFs that are unavailable in a new conversation.
- Browser autosave does not store subsequent full-text work performed in chat. Direct spreadsheet edits are checked when resuming.

## Usage Notes

- **Students judge first and make the final decisions.** AI supports learning and review; verify evidence against the agreed criteria and source publications.
- Inclusion at Stage 1 means the report should proceed to full-text review. Hold records when information is insufficient. Missing full texts and PDF-reading errors are not eligibility exclusions.
- Prior exposure to student answers is recorded. Agreement is not accuracy or proof of independent assessment. Review hold–hold matches and records awaiting comparison separately.
- In-interface AI evaluation, PDF reading, and file creation depend on the Claude environment. If AI is unavailable in the Stage 1 interface, follow the request-and-response copying instructions. PDFs may need to be processed in smaller groups.
- Excel delivery requires code execution and file creation. See the [official Claude skills guide](https://support.claude.com/en/articles/12512180-use-skills-in-claude) for setup. The screening interface is primarily in Korean.
- The workbook’s **PRISMA counts** are inputs for a subsequent flow diagram, not a completed diagram. A PDF comparison report can be requested separately.

## License

No separate open-source license has been specified. Please use this repository’s Issues for permission requests such as redistribution or distribution of modified versions.

## Author

**Jeongin Choe (최정인)**

[nncj91@snu.ac.kr](mailto:nncj91@snu.ac.kr)

## Advisor

**Kyungmi Woo (우경미)** — Associate Professor, College of Nursing, Seoul National University

ANDA Lab: https://andalab.snu.ac.kr/

## Acknowledgements

This tool was developed with the assistance of generative AI tools. We thank Soyeon Park, a doctoral student at the College of Nursing, Seoul National University, for carefully reviewing the usage process and providing suggestions for improvement.
