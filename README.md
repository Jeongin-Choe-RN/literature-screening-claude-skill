# Literature Screening & PRISMA Flow Diagram — Claude Skill

문헌고찰을 위한 문헌선별을 Claude에서 안내하는 학생용 스킬입니다. 학생이 문헌을 먼저 읽고 판단한 뒤 AI 평가와 비교합니다. 1차 제목·초록 선별은 화면에서, 2차 원문 선별은 채팅에서 진행하고 최종 결과를 엑셀로 저장합니다. 선별을 마치면 그 결과가 미리 채워진 PRISMA 2020 흐름도 입력 화면이 열리고, 흐름도 그림(PNG·Word)을 만듭니다.

Claude Skill · Student Version 3.0

[literature-screening-flow-diagram.skill 다운로드](https://github.com/rnrnrnn1234/literature-screening-flow-diagram/raw/main/literature-screening-flow-diagram.skill)

## 주요 기능

- **선별 기준 확인** — 연구질문과 포함·제외 기준을 정리하고 중복 문헌 후보를 확인
- **1차 제목·초록 선별** — 화면에서 한 편씩 읽고 포함·보류·제외를 선택
- **학생·AI 판정 비교** — 최초 판정과 AI 평가의 차이를 확인하고 학생이 최종 판단을 확정
- **2차 원문 선별** — 채팅에 PDF를 첨부해 AI 평가를 받고, 미리 기록한 학생 판정과 비교
- **엑셀 결과 저장** — 학생 최초·AI·최종 판정, 기준별 근거와 쪽수, 제외 사유, 검색 기록과 PRISMA 집계를 보존
- **PRISMA 2020 흐름도 작성** — 최종 엑셀을 받은 뒤 선별 결과가 자동 반영된 입력 화면이 열리고, 값을 확인·수정해 흐름도를 PNG·Word로 저장
- **흐름도만 따로 만들기** — 선별 없이 흐름도만 요청하면 빈 입력 화면에서 직접 입력
- **한글/English 전환** — 1차 선별 화면 상단 버튼으로 화면 언어 변경
- **가상 문헌으로 연습** — 질문·기준·문헌 5편·가상 원문이 준비된 튜토리얼로 사용 순서를 연습

## 다운로드 및 사용 방법

1. 위의 다운로드 링크로 `literature-screening-flow-diagram.skill` 파일을 저장합니다.
2. Claude의 **스킬 관리 → 스킬 업로드**에서 다운로드한 파일을 업로드하고 활성화합니다.
3. 새 대화에 검색 보고서와 문헌 목록(NBIB·CSV·RIS 등)을 첨부하고 다음과 같이 입력합니다.

   > literature-screening-flow-diagram 스킬로 첨부한 문헌의 선별을 시작해 주세요.

   먼저 연습하려면 "문헌선별을 가상 문헌으로 연습하고 싶어요."라고 요청합니다.
4. 화면에서 연구질문·포함/제외 기준·중복 문헌을 확인합니다.
5. **1차**: 제목과 초록을 읽고 판정합니다. 내 판정을 확정한 뒤 AI와 비교하고 최종 판단을 기록합니다. 포함·제외가 일치한 문헌은 근거 확인 후 함께 확정할 수 있습니다.
6. **2차 시작**: '2차는 채팅에서 계속'을 눌러 시작 자료를 한 번 저장해 대화에 첨부합니다. 내려받기가 안 되면 '시작 내용 복사'를 사용합니다.
7. **2차 진행**: 원문을 읽고 자신의 판정·근거를 메모장이나 개인 엑셀에 먼저 적어 둡니다. 아직 그 답을 보내지 말고 PDF를 대화 입력창에 첨부해 AI 평가를 받습니다. 이후 미리 적은 학생 판정을 보내 비교하고 최종 판단을 알려 줍니다.
8. **최종 결과 엑셀**을 확인하고 저장합니다. 2차의 AI 답변이나 최종 결과를 화면에 다시 입력할 필요는 없습니다.
9. **PRISMA 흐름도**: 최종 엑셀이 나온 뒤 이어서 열리는 입력 화면에서 불러온 값을 확인합니다. DB별 검색 건수처럼 선별 기록에 없는 칸은 직접 입력하고 '승인하고 생성'을 누르면 PNG·Word 파일을 받습니다.

### 흐름도만 만들기

- 선별 없이 흐름도만 필요하면 "PRISMA 흐름도 만들어 주세요."라고 요청하고, 빈 입력 화면에 값을 직접 넣습니다.
- 진행 중 저장한 엑셀만 있을 때는 그 파일을 첨부하고 "이 엑셀로 PRISMA 흐름도를 만들어 주세요."라고 요청합니다.

## 저장하고 이어가기

- **1차 화면**: 지원되는 환경에서는 자동 임시저장됩니다. 작업을 마칠 때는 '진행 저장' 파일도 보관하고, 다음에는 '문헌 목록 불러오기'로 엽니다.
- **2차 채팅**: "현재 진행을 엑셀로 저장해 주세요."라고 요청합니다. 다음에는 최신 엑셀을 첨부해 이어갑니다. 새 대화에서 필요한 원문이 없으면 해당 PDF를 다시 첨부합니다.
- 화면의 자동 임시저장은 채팅의 2차 결과까지 저장하지 않습니다. 엑셀에서 직접 수정한 값은 재개할 때 확인한 뒤 반영합니다.

## 사용 시 유의사항

- 학생이 먼저 판단하고 최종 결정합니다. AI 평가는 학습과 검토를 돕는 자료이며, 실제 기준과 원문에서 근거를 확인하세요.
- 1차의 포함은 원문 검토 대상이라는 뜻입니다. 정보 부족은 보류하고, 원문 미확보나 PDF 읽기 오류를 적격성 제외로 처리하지 않습니다.
- AI 평가 전에 학생 답을 보내면 그 노출 사실을 기록합니다. 판정 일치율은 정확도나 검증된 독립 평가의 지표가 아닙니다. 보류끼리 일치한 경우와 비교 대기 문헌을 함께 확인하세요.
- 화면 안 AI 평가·PDF 읽기·파일 생성 가능 여부는 Claude 환경에 따라 다릅니다. 1차 화면에 AI 연결이 없으면 요청·답변을 복사하는 안내를 따릅니다. 여러 PDF는 처리 가능한 범위로 나누어 진행할 수 있습니다.
- 엑셀과 흐름도 산출물에는 코드 실행 및 파일 생성 기능이 필요합니다. 설치 환경은 Claude 공식 스킬 안내를 참고하세요.
- 흐름도의 값은 선별 기록에서 불러온 초안입니다. 제외 사유 라벨과 건수를 직접 확인하고, 기록에 없는 값은 본인이 입력하세요.
- 영어 화면에서도 입력한 연구질문·기준·제외 사유, 저장 파일, AI 평가 요청문은 한글 원문으로 유지됩니다.
- PDF 비교 보고서는 필요할 때 추가로 요청할 수 있습니다.

## PRISMA 출처

Page MJ, McKenzie JE, Bossuyt PM, et al. The PRISMA 2020 statement: an updated guideline for reporting systematic reviews. BMJ 2021;372:n71. doi:10.1136/bmj.n71

흐름도 양식은 PRISMA 2020 template(CC BY 4.0, [prisma-statement.org](https://www.prisma-statement.org))을 따릅니다.

## 라이선스

별도의 오픈소스 라이선스는 지정하지 않았습니다. 재배포·수정본 배포 등 이용 허락이 필요한 경우 저장소의 Issues에서 문의해 주세요.

## 제작자

- **최정인 (Jeongin Choe)** — 문헌선별 스킬 설계·개발 · nncj91@snu.ac.kr
- **박소연 (Soyeon Park)** — PRISMA 흐름도 연계, 검토·개선 · rnsy1029@snu.ac.kr

## 지도교수

우경미 (Kyungmi Woo) — 서울대학교 간호대학 부교수

ANDA Lab: https://andalab.snu.ac.kr/

## 감사의 말

이 도구는 생성형 AI 도구를 활용하여 개발되었습니다.

# Literature Screening & PRISMA Flow Diagram — Claude Skill

A student-oriented Claude skill that guides literature screening for literature reviews. Students read each record and make their own decision first, then compare it with the AI assessment. Stage 1 (title and abstract) screening runs on an interactive screen, stage 2 (full-text) screening runs in chat, and the final results are saved to Excel. When screening is finished, a PRISMA 2020 flow diagram input screen opens with the results already filled in and produces the diagram (PNG and Word).

Claude Skill · Student Version 3.0

[Download literature-screening-flow-diagram.skill](https://github.com/rnrnrnn1234/literature-screening-flow-diagram/raw/main/literature-screening-flow-diagram.skill)

## Key Features

- **Screening criteria check** — Organize the research question and inclusion/exclusion criteria, and check duplicate candidates
- **Stage 1: title and abstract screening** — Read one record at a time on screen and choose Include, Maybe or Exclude
- **Student–AI decision comparison** — Review differences between the initial decision and the AI assessment; the student confirms the final decision
- **Stage 2: full-text screening** — Attach PDFs in chat for AI assessment and compare it with the student's pre-recorded decision
- **Excel results** — Keeps the student's initial, AI and final decisions, evidence and page numbers by criterion, exclusion reasons, the search log and PRISMA counts
- **PRISMA 2020 flow diagram** — After the final Excel file, an input screen opens with the screening results filled in; check and edit the values, then save the diagram as PNG and Word
- **Flow diagram only** — Request just the diagram without screening and enter the values on a blank input screen
- **Korean/English switch** — Change the screen language with the button at the top of the stage 1 screen
- **Practice with sample records** — A tutorial with a prepared question, criteria, five records and sample full texts

## Download and Usage

1. Save `literature-screening-flow-diagram.skill` from the download link above.
2. In Claude, go to **Manage skills → Upload skill**, upload the file and turn it on.
3. In a new chat, attach your search report and record list (NBIB, CSV, RIS, etc.) and type:

   > Please start screening the attached records with the literature-screening-flow-diagram skill.

   To practice first, ask: "I'd like to practice literature screening with sample records."
4. On the screen, check the research question, inclusion/exclusion criteria and duplicate records.
5. **Stage 1**: Read the title and abstract and decide. Lock your decisions, compare them with the AI, and record your final decisions. Records agreed as include or exclude can be finalized together after checking the evidence.
6. **Starting stage 2**: Press "Continue stage 2 in chat", save the start file once and attach it to the chat. If the download does not work, use "Copy start content".
7. **Stage 2**: Read the full text and write your decision and rationale in a notepad or your own Excel file first. Do not send that answer yet; attach the PDFs in the chat box to get the AI assessment. Then send your pre-written decisions to compare, and tell Claude your final decisions.
8. Check and save the **final results Excel file**. You do not need to re-enter stage 2 AI replies or final results on the screen.
9. **PRISMA flow diagram**: Check the values loaded into the input screen that opens after the final Excel file. Enter fields that are not in the screening records yourself, such as the number of records per database, then press "승인하고 생성" (Approve and generate) to receive the PNG and Word files.

### Flow diagram only

- If you only need the diagram, ask "Please make a PRISMA flow diagram." and enter the values on the blank input screen.
- If you only have an in-progress Excel file, attach it and ask "Please make a PRISMA flow diagram from this Excel file."

## Saving and Resuming

- **Stage 1 screen**: Drafts are saved automatically where the environment supports it. When you finish, also keep a "Save progress" file and open it next time with "Import record list".
- **Stage 2 chat**: Ask "Please save the current progress to Excel." Next time, attach the latest Excel file to continue. If a needed full text is missing in a new chat, attach that PDF again.
- The automatic draft on the screen does not include stage 2 results from chat. Values edited directly in Excel are checked with you before being applied when you resume.

## Notes on Use

- The student decides first and makes the final decision. The AI assessment is a learning and review aid; check the evidence against the actual criteria and full text.
- Include at stage 1 means the record goes on to full-text review. Mark insufficient information as Maybe, and do not treat a full text that could not be retrieved or a PDF reading error as an eligibility exclusion.
- If the student's answer is sent before the AI assessment, that exposure is recorded. The agreement rate is not a measure of accuracy or of a verified independent assessment. Check maybe–maybe agreements and records awaiting comparison as well.
- Whether on-screen AI assessment, PDF reading and file creation are available depends on your Claude environment. If the stage 1 screen has no AI connection, follow the guide for copying the request and reply. Several PDFs can be processed in smaller groups.
- Excel and flow diagram outputs require code execution and file creation. See Claude's official skill documentation for setup.
- The values in the flow diagram are a draft loaded from the screening records. Check the exclusion reason labels and counts yourself, and enter any values not in the records.
- On the English screen, the research question, criteria and exclusion reasons you entered, saved files and the AI assessment request remain in the original Korean.
- A PDF comparison report can be requested separately when needed.

## PRISMA Source

Page MJ, McKenzie JE, Bossuyt PM, et al. The PRISMA 2020 statement: an updated guideline for reporting systematic reviews. BMJ 2021;372:n71. doi:10.1136/bmj.n71

The flow diagram follows the PRISMA 2020 template (CC BY 4.0, [prisma-statement.org](https://www.prisma-statement.org)).

## License

No open-source license has been specified. For permission to redistribute or distribute modified versions, please ask in the repository's Issues.

## Authors

- **Jeongin Choe (최정인)** — Design and development of the literature screening skill · nncj91@snu.ac.kr
- **Soyeon Park (박소연)** — PRISMA flow diagram integration, review and improvement · rnsy1029@snu.ac.kr

## Advisor

Kyungmi Woo (우경미) — Associate Professor, College of Nursing, Seoul National University

ANDA Lab: https://andalab.snu.ac.kr/

## Acknowledgments

This tool was developed with the help of generative AI tools.
