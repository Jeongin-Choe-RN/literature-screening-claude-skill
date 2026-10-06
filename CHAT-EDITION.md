# Literature Screening — Chat Edition

**채팅 전용 · Chat 1.0**

처음부터 끝까지 Claude 대화에서 문헌을 선별하고 엑셀로 저장하는 학생용 스킬입니다. 별도 아티팩트 화면이나 JSON 복사 없이 **1차 제목·초록 → 2차 원문 PDF**를 진행합니다.

**[literature-screening-chat.skill 다운로드](https://github.com/Jeongin-Choe-RN/literature-screening-claude-skill/raw/refs/heads/main/literature-screening-chat.skill)** · [스킬 내용 보기](docs/literature-screening-chat/SKILL.md)

기존 [화면형 v3.0](README.md)은 그대로 사용할 수 있습니다. 두 스킬은 이름과 설치 파일이 다릅니다. 이번 대화에서 사용할 스킬을 이름으로 지정하세요.

## 사용 방법

1. `literature-screening-chat.skill`을 내려받아 Claude의 스킬 관리에서 업로드하고 활성화합니다.
2. 새 대화에 **검색 보고서·문헌목록(NBIB, PubMed 형식 TXT, RIS, CSV 등)**을 첨부하고 아래와 같이 입력합니다.

   > literature-screening-chat 스킬로 첨부한 문헌을 선별해 주세요. 아티팩트 없이 채팅에서 진행하고, 결과는 엑셀로 저장해 주세요.

3. 연구질문·포함/제외 기준·중복 후보·이번 선별 범위를 확인합니다.
4. **1차:** 제시된 제목·초록을 읽고 본인의 판정과 근거를 먼저 따로 적습니다. 아직 답을 보내지 말고 준비됐다고 알립니다. AI 평가를 받은 뒤 미리 적은 답을 제출하고 비교하여 최종 판단을 알려 줍니다.
5. **2차:** 같은 대화에서 원문을 검토합니다. PDF를 먼저 읽고 본인의 판정을 따로 기록한 뒤 대화 입력창에 PDF를 첨부합니다. AI 평가 후 학생 판정을 제출·비교하고 최종 판단을 알려 줍니다.
6. 묶음마다 제공되는 **진행 엑셀**을 저장합니다. 다음에는 최신 엑셀을 첨부하고 “이어서 해 주세요”라고 요청합니다. 필요한 PDF는 다시 첨부합니다.

한 번에 처리하는 수는 초록·원문 길이에 따라 조정합니다. 특정 PDF 수의 동시 처리 성공을 보장하지 않습니다. 한 문헌의 오류는 별도로 남기고 다른 문헌을 계속 검토합니다.

## 영어 사용·가상 연습

영어로 진행할 때:

> Use the literature-screening-chat skill to screen the attached records. Work entirely in chat, use English for the explanations and Excel labels, and save the progress as an Excel workbook.

이전 검색 영상과 같은 **간호대학생의 수면과 스트레스** 주제로 연습할 때:

> literature-screening-chat 스킬의 가상 문헌으로 사용 순서를 연습하고 싶어요.

내장 5편과 연습용 원문은 **실제 논문이 아닌 가상 자료**입니다. 실제 연구에 섞지 않습니다. 학생·AI 판정이 정답으로 미리 입력되어 있지 않습니다.

## 결과와 이어 하기

- `literature-screening-chat-progress.xlsx`: 진행 중인 기록
- `literature-screening-chat-results.xlsx`: 선언한 선별 범위의 기록이 완료된 결과
- 문헌 ID, 기준, 학생 최초·AI·학생 최종 판정, 기준별 근거·쪽수, 제외 사유, 검색 기록과 PRISMA 건수를 보존합니다.
- 직접 수정한 엑셀은 재개 시 변경 내용을 확인합니다. 최초·AI 판정과 기존 기준을 몰래 덮어쓰지 않습니다.
- 기존 화면형 v3.0의 진행 파일과 자동 호환된다고 가정하지 않습니다. 기존 작업은 기존 스킬에서 계속하고, 이 버전은 별도 작업으로 시작하세요.

## 유의사항

AI는 비교·검토를 돕고 학생이 최종 판단합니다. AI 전에 학생 답을 보내면 사전 노출을 기록합니다. 일치율은 정확도나 검증된 독립 평가를 뜻하지 않습니다. 정보 부족·읽기 오류·원문 미확보·적격성 제외를 구분합니다. PRISMA 건수 표는 이후 흐름도 작성에 사용할 자료이며 완성된 그림이 아닙니다.

실제 엑셀 생성에는 실행·파일 생성 기능이 필요합니다. 지원하지 않는 환경에서는 저장 완료를 주장하지 않고 미완료 상태와 가능한 표를 안내합니다. 설치 환경은 [Claude 공식 스킬 안내](https://support.claude.com/en/articles/12512180-use-skills-in-claude)를 참고하세요.

## 제작·이용 안내

제작: **최정인 (Jeongin Choe)** · 지도: **우경미 (Kyungmi Woo), 서울대학교 간호대학**

사용 과정을 검토하고 개선 의견을 주신 **박소연 선생님**께 감사드립니다. 생성형 AI 도구의 도움을 받아 개발했습니다. 별도의 오픈소스 라이선스는 지정하지 않았으며, 이용 허락 관련 문의는 저장소 Issues를 이용해 주세요.

---

# Literature Screening — Chat Edition (English)

**Chat 1.0** guides students through title-and-abstract screening and full-text review in a Claude conversation, with Excel records for saving and resuming. No interactive artifact or user-facing JSON transfer is required.

**[Download literature-screening-chat.skill](https://github.com/Jeongin-Choe-RN/literature-screening-claude-skill/raw/refs/heads/main/literature-screening-chat.skill)** · [View skill](docs/literature-screening-chat/SKILL.md)

The existing [interface-based v3.0](README.md) remains available. This edition has a separate skill name and installation file.

## Workflow

1. Upload and enable the `.skill` file in Claude's skill management area.
2. Attach the search report and actual reference list, then request `literature-screening-chat` by name.
3. Confirm the question, criteria, duplicate records, and screening scope.
4. Read the titles and abstracts and privately record your initial decisions. Tell Claude you are ready without sending those answers. After its assessment, submit your prewritten decisions, compare the evidence, and confirm your final decisions.
5. Continue full-text review in the same conversation. Read and privately record your decisions before viewing AI assessments; attach PDFs in the chat. Compare and make the final decisions.
6. Save the progress workbook after each batch. Attach the latest workbook to resume, along with any PDFs still needed.

Ask for English to receive English explanations and workbook labels. The optional practice set contains five **fictional** records about sleep and stress among undergraduate nursing students; it is not research evidence.

The workbook retains source IDs, criteria, initial/AI/final judgments, evidence, PDF pages, exclusion reasons, search history, and PRISMA counts. Direct edits are checked on resumption. Existing v3.0 progress files are not automatically migrated to this edition.

AI agreement is not accuracy or proof of independent assessment. Missing information, PDF errors, unavailable full texts, and eligibility exclusions remain distinct. Batch sizes depend on the actual files and environment. Excel delivery requires code execution and file creation. A PRISMA count table is not a finished flow diagram.

Author: **Jeongin Choe** · Advisor: **Kyungmi Woo, College of Nursing, Seoul National University**. We thank **Soyeon Park** for reviewing the workflow and suggesting improvements. Developed with generative AI assistance. No separate open-source license is specified; contact the repository through Issues for permission inquiries.
