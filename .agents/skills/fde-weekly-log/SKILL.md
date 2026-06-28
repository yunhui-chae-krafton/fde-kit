---
name: fde-weekly-log
description: Space & Property FDE 주간 로그와 AX Impact 금요일 통합 진행현황 업데이트 초안을 Confluence FDEWORK, krafton-slack-mcp, GitHub MCP/Repo, SharePoint Excel 증빙 기반으로 작성하거나 재작성한다. 특정 기간의 FDE weekly log, FDE_통합진행현황.xlsx 행 초안, S0~S6 단계 산정, 바텀업 과제 분류, Meetings/Project/Slack/GitHub 근거 수집, 임팩트 과제와 규격 외 인입 요청 분리가 필요할 때 사용한다.
---

# FDE Weekly Log

## 개요

이 스킬은 Space & Property FDE 주간 로그를 짧고 근거 있게 작성하기 위한 기준이다. 기간 안에 실제로 한 일을 확인하고, 승인된 임팩트 과제와 규격 외 인입 요청을 분리하며, Confluence/Slack/GitHub/앱/Repo/회의록 링크를 함께 남긴다.

Confluence 접근이 필요하면 Atlassian/Confluence MCP 조회 도구를 사용한다.

## 출력 원칙

- Confluence MCP는 자료 조회용으로만 사용한다.
- Confluence MCP로 페이지를 생성, 수정, stage, preview, commit 하지 않는다.
- 최종 결과물은 사용자가 검토 후 copy & paste할 수 있는 Markdown 초안으로 채팅에 제공한다.
- 사용자가 별도로 요청하지 않아도, 주간 로그 본문은 복사하기 쉬운 Markdown 형태로 제공한다.
- 사용자가 Confluence 반영까지 요청하더라도, 이 스킬에서는 먼저 Markdown 초안을 제공하고 사용자 검토를 거치도록 안내한다.

## 소스 확인 순서

1. Space & Property Confluence 맥락을 확인한다.
   - `SP-00 Overview` / `AX 과제 요약`
   - `SP-02 Meetings` 및 그 하위 회의록
   - Space & Property 아래 Project 하위 페이지
2. Meetings는 페이지 수정일이 아니라 실제 회의 일시 기준으로 필터링한다. 요청 기간 안에 진행된 회의만 포함한다.
3. Project 하위 페이지는 요청 기간 안에 실제 진행, 변경, 산출물이 있는 경우만 반영한다.
4. `krafton-slack-mcp`로 Slack 흔적을 확인한다.
   - Codex에서 도구가 노출될 때는 보통 `mcp__krafton_slack_mcp.slack_search_messages`, `mcp__krafton_slack_mcp.slack_get_messages`, `mcp__krafton_slack_mcp.slack_connect_workspace` 형태로 보인다.
   - Slack 검색 전에 `krafton-slack-mcp`가 OAuth 인증되어 있는지 확인한다.
   - `OAuth authorization required`, `invalid_auth_token` 등 인증 오류가 나면 Slack 근거를 임의로 대체하지 말고, 초안에 `Slack 확인 필요`로 표시한다.
   - 필요하면 사용자 Slack ID를 먼저 찾는다.
   - 해당 기간 동안 사용자가 남긴 메시지를 검색한다.
   - 해당 기간 동안 사용자가 멘션된 메시지를 검색한다.
   - 포함 기간은 `after:시작일 before:종료일+1일` 형태로 검색한다.
   - Slack 내용은 메시지 자체가 완료를 명확히 말하지 않는 한 `추정 가능한 활동` 근거로 취급한다.
   - 개인 DM, group DM, private channel 등 공개적으로 공유하기 어려운 Slack permalink는 최종 로그에 직접 남기지 않는다.
   - 비공개 Slack 근거는 `Slack 기준으로 확인됨`, `Slack DM 기준으로 확인됨`, `비공개 Slack 기준으로 확인됨`처럼 링크 없이 표현한다.
   - public channel이고 로그 독자가 접근할 수 있는 증빙일 때만 Slack permalink를 남긴다.
5. 코드/앱 산출물이 주간 로그에 포함되는 경우 GitHub MCP 또는 로컬 `git`/`gh`로 Repo 흔적을 확인한다.
   - GitHub MCP가 노출되어 있으면 `mcp__github.search_pull_requests`, `mcp__github.search_commits`, `mcp__github.search_code`, `mcp__github.search_issues`를 우선 사용한다.
   - GitHub MCP 인증 오류, 권한 오류, repo not found가 나면 내용을 임의로 대체하지 말고 `GitHub 확인 필요` 또는 `GitHub MCP 권한 확인 필요`로 표시한다.
   - 검색 범위는 repo, 작성자, 기간 기준으로 제한한다. 기간은 요청 기간과 동일하게 `YYYY-MM-DD..YYYY-MM-DD` 범위를 사용한다.
   - GitHub commit/PR/issue는 산출물 근거로 사용하되, Confluence/Slack/회의 근거 없이 commit만으로 임팩트 과제 성과를 확정하지 않는다.
   - private repo, 개인 fork, 권한 제한 링크는 로그 독자가 접근할 수 있는 경우에만 URL을 남긴다. 접근성이 불확실하면 repo명, PR 번호, commit hash, 제목 중심으로 요약한다.
   - GitHub write 도구(PR 생성, comment, merge 등)는 주간 로그 작성 중 사용하지 않는다. 사용자가 명시적으로 요청한 경우에만 별도 확인 후 사용한다.

## 임팩트 과제 허용 목록

`## 임팩트 과제 진행 현황`에는 현재 `SP-00 Overview`의 `AX 과제 요약`에 있는 과제만 넣는다.

현재 Space & Property 임팩트 과제 허용 목록은 다음과 같다.

| Priority | 과제 |
| --- | --- |
| P1 | 외부인 방문 프로세스 개편 |
| P1 | 식당 원가 상시 모니터링 |
| P2 | 급여공제/정산 자동화 |
| P2 | 복리후생 Seamless Care |

활동이 위 목록 중 하나에 직접 연결되지 않으면 `## 임팩트 과제 진행 현황`에 넣지 않는다. 대신 `## 규격 외 인입 요청`, `## 온보딩 / 환경 세팅`, 또는 생략으로 처리한다.

다음은 명시적으로 연결되지 않는 한 임팩트 과제로 넣지 않는다.

- AI 해커톤 사전 미팅 또는 행사 참가팀 지원
- Google Form, 설문조사용 웹, 단발성 웹 제작
- GitHub, KP, 노트북, GPU, API 비용 관련 환경 세팅
- FDE 요청 가이드 공유
- OCR 또는 AI 실패 사례 수집

## 고정 헤딩

기본적으로 아래 순서와 제목을 유지한다.

```markdown
## N주차 · MM/DD – MM/DD

### 주간 요약

### 임팩트 과제 진행 현황

### 시행착오 / 막힌 것

### 규격 외 인입 요청

### Meetings

### Project / 산출물

### AIT 신호
```

주차 제목은 `1주차 · 06/01 – 06/07`처럼 `N주차 · MM/DD – MM/DD` 형식으로 쓴다. 본문 표와 문장 안의 날짜는 혼동을 줄이기 위해 `2026-06-10`처럼 연도를 포함한 절대 날짜를 사용한다.

해커톤, 행사 지원, Slack, 기타 요청을 별도 상위 섹션으로 만들지 않는다. 해당 내용은 필요하면 `### 규격 외 인입 요청` 표의 행으로 넣는다.

## 섹션 작성 규칙

### 주간 요약

2-4문장으로 작성한다. 담당 조직, 승인된 임팩트 과제 진행, 주요 규격 외 인입 요청을 함께 언급한다. 근거 없는 포괄적 표현은 피한다.

### 임팩트 과제 진행 현황

아래 표를 사용한다.

| 과제 | 이번 주 진행 | 상태 | 리스크 / Gate | 다음 액션 |
| --- | --- | --- | --- | --- |

요청 기간 안에 실제 활동이 있었던 허용 목록 과제만 남긴다.

### 시행착오 / 막힌 것

임팩트 과제 또는 의미 있는 기술/권한/정책 블로커만 작성한다. 가능한 경우 근거 링크를 붙인다. 모르는 값은 `X` 대신 `확인 필요`라고 쓴다.

### 규격 외 인입 요청

이 제목을 정확히 사용한다. 임팩트 과제에 포함되지 않는 단발성 요청, 지원, 행사 참가팀 사전 정렬, 설문, 가이드 공유, 운영/환경 세팅을 이 섹션에 넣는다.

아래 표를 사용한다.

| 날짜 | 요청/대상 | 이번 주 진행 | 산출물 / 증빙 | 상태 | 다음 액션 |
| --- | --- | --- | --- | --- | --- |

`AI 해커톤`은 섹션 제목으로 쓰지 않는다. 행 내용에서 맥락상 필요할 때만 언급한다.

### Meetings

Space & Property 아래 Confluence 회의록 중 실제 회의일이 요청 기간에 들어가는 것만 넣는다.

아래 표를 사용한다.

| 날짜 | 미팅 | 참석자 | 로그 반영 내용 |
| --- | --- | --- | --- |

회의가 맥락만 제공하고 실제 액션이나 산출물로 이어지지 않았다면, Meetings에는 넣되 임팩트 과제 진행으로 억지 반영하지 않는다.

### Project / 산출물

요청 기간에 실제로 만졌거나 산출물 근거가 되는 Project 페이지와 링크를 넣는다.

- Confluence Project 페이지
- 앱 URL
- GitHub/KP/Core 링크
- GitHub MCP 또는 로컬 `git`/`gh`로 확인한 PR, commit, issue, repo 링크
- 스크린샷 또는 아카이브 링크
- Slack permalink는 public channel이고 로그 독자가 접근할 수 있는 증빙일 때만 사용
- 개인 DM, group DM, private channel 링크는 남기지 말고 `Slack DM 기준으로 확인됨` 또는 `비공개 Slack 기준으로 확인됨`으로 표현

### AIT 신호

명시적 근거가 없으면 `이번 주 해당 없음.`이라고 쓴다. 여러 조직에서 반복되는 제약, 정책/인프라 필요, 보안/권한 병목, AIT 흡수 후보가 확인될 때만 작성한다.

## Slack 검색 패턴

`krafton-slack-mcp`의 `slack_search_messages`를 우선 사용한다. 연결이 필요하면 `slack_connect_workspace`를 시도하고, 연결 도구도 인증 오류로 실패하면 Slack 확인 불가 상태를 명시한다.

아래 검색을 출발점으로 사용한다.

```text
from:<@USER_ID> after:YYYY-MM-DD before:YYYY-MM-DD+1
<@USER_ID> after:YYYY-MM-DD before:YYYY-MM-DD+1
from:<@USER_ID> 외부인
from:<@USER_ID> KissFlow
from:<@USER_ID> 사번
from:<@USER_ID> 설문
from:<@USER_ID> forms.gle
from:<@USER_ID> Google Form
from:<@USER_ID> KP
from:<@USER_ID> GitHub
from:<@USER_ID> 노트북
from:<@USER_ID> GPU
from:<@USER_ID> API
```

검색 도구가 OR 조건을 안정적으로 지원하지 않으면 키워드를 나누어 검색한다. Slack 기반 내용은 필요하면 `Slack 기준으로 확인됨` 또는 `Slack 기준으로 추정됨`으로 표현한다. 개인 DM, group DM, private channel 검색 결과는 링크를 남기지 않는다.

## GitHub 검색 패턴

GitHub MCP가 노출되어 있으면 코드/앱 산출물 확인에 사용한다. GitHub MCP가 없거나 권한이 부족하면 로컬 `git log`, `git remote -v`, `gh pr list`, `gh pr view`로 가능한 범위만 확인한다.

출발점은 아래 패턴을 사용한다.

```text
repo:OWNER/REPO author:USER author-date:YYYY-MM-DD..YYYY-MM-DD
repo:OWNER/REPO committer-date:YYYY-MM-DD..YYYY-MM-DD
author:USER updated:YYYY-MM-DD..YYYY-MM-DD
repo:OWNER/REPO is:pr author:USER updated:YYYY-MM-DD..YYYY-MM-DD
repo:OWNER/REPO is:issue author:USER updated:YYYY-MM-DD..YYYY-MM-DD
repo:OWNER/REPO "프로젝트명 또는 앱 이름"
```

GitHub commit search는 기본 브랜치 기준으로 제한될 수 있으므로, 결과가 없더라도 로컬 브랜치/태그/원격 브랜치에 커밋이 있을 수 있다. 이 경우 로컬 `git log --all --since ... --until ... --author ...` 결과와 함께 판단한다.

## AX Impact Friday Update

매주 금요일 SharePoint `FDE_통합진행현황.xlsx` 업데이트 초안을 만들 때 사용한다.

- SharePoint/Excel 도구가 노출되어 있으면 파일을 조회해 `범례`, `StatusTable`, `AXITable`, `통합 진행현황표` 헤더를 먼저 확인한다.
- Excel에는 기본적으로 직접 쓰지 않는다. 먼저 사용자가 검토할 수 있는 `StatusTable` 행 단위 Markdown 표를 제공한다.
- 사용자가 명시적으로 Excel 업데이트까지 요청하면, 변경할 행과 값을 다시 요약해 확인한 뒤 MS365 Excel write 도구를 사용한다.
- `StatusTable` 기본 열은 `본부`, `담당자`, `시민개발자 주도`, `프로덕트명`, `프로덕트 형태`, `구분`, `성격`, `접속 링크`, `관련 임팩트 과제`, `PRD / MD`, `단계`, `완성도`, `일정`, `코멘트(변경·이슈)` 순서로 맞춘다.
- 중앙 `AXI 2026 과제` 또는 `SP-00 Overview` 허용 목록에 있는 과제는 `구분=AXI 과제`로 둔다.
- 중앙 목록 밖의 현업/시민개발자 주도 아젠다는 `구분=바텀업`으로 둔다. FDE가 직접 만든 공통 도구/인프라는 `구분=FDE개발`로 둔다.
- `시민개발자 주도`는 현업이 직접 만든 HTML/앱/대시보드 또는 운영 주도권이 현업에 있으면 `Y`로 쓴다. FDE 주도 구현이면 비워둔다.

### 단계 산정

단계는 증빙 기준으로 보수적으로 산정한다.

| 단계 | 기준 |
| --- | --- |
| `S0` | 발굴/기획. 아이디어, pain point, 담당자 후보만 있음. |
| `S1` | 설계·프로빙. 업무 흐름, 요구사항, 정책/권한 검토, 자료 요청이 진행됨. |
| `S2` | PoC. 로컬 HTML, 샘플 데이터, 수동 테스트, 부분 동작 검증이 있음. |
| `S3` | MVP 구현(shadow). MVP가 구현되어 실제/샘플 데이터로 shadow 검증 중이나 배포 또는 현업 접근은 아직 제한적임. |
| `S4` | 클라우드 배포. MVP가 배포되었거나 고정 URL/접근 경로가 있고, 현업 테스트 진입 전 또는 접근/권한 확인 중임. |
| `S5` | 현업 테스트(UAT). 배포된 MVP를 현업 담당자가 직접 테스트하거나 피드백을 주는 중임. |
| `S6` | 무인/프로덕션 운영. 정기 운영, 무인 처리, 운영 DRI 핸드오프가 확인됨. |
| `중단` | 보안, 권한, 데이터, 정책 선행조건 때문에 폐기/중단 또는 장기 hold 상태임. |

- MVP 구현과 배포가 모두 확인되면 최소 `S4`로 둔다.
- 배포만으로 `S5`를 주지 않는다. 현업 담당자의 직접 사용, UAT, 피드백, 샘플 검증 참여가 확인될 때 `S5`로 올린다.
- 개인정보, 금융정보, HR 데이터가 포함된 과제는 현업 테스트가 있더라도 보안/권한 범위가 불명확하면 `S4→S5`처럼 전이 상태로 표현한다.
- 실제 운영, 정기 실행, 담당자 없는 무인 처리, 운영 DRI 인계가 확인되기 전에는 `S6`로 올리지 않는다.

### Space & Property 바텀업 후보

다음 유형은 기존 Space & Property 임팩트 과제와 분리해 `바텀업`으로 기록한다.

| 후보 | 기본 분류 | 단계 판단 |
| --- | --- | --- |
| 허주혜님 Space Planning 대시보드 HTML/MVP | `바텀업`, 현업 HTML 주도이면 `시민개발자 주도=Y` | MVP 구현+배포 완료면 `S4`, 허주혜님 또는 Space & Property 구성원이 직접 테스트/피드백 중이면 `S5` |
| 김재근님 대출/품의 제출 가드레일 자동화 | `바텀업`, FDE 구현 주도이면 `시민개발자 주도`는 비움 | MVP 구현+배포 완료면 `S4`, 김재근님이 실제/익명화 샘플로 테스트 중이면 `S4→S5` 또는 `S5` |

예시 행 초안:

```markdown
| Space & Property Center | 채윤희 | Y | Space Planning 대시보드 | 웹 대시보드 | 바텀업 | 신규 서비스 · 자동화 | 배포 URL | Space Planning 운영 기준 데이터 업데이트 | 260619 REQ / Slack 기준 확인 | S5 | MVP 구현 및 배포 완료, 현업 피드백 확인 중 | 미정 | 회의록 → 변경사항 감지 → 승인 → 기준 데이터 업데이트 → 대시보드 반영 흐름을 MVP로 구현/배포. 다음: Space & Property 구성원 접근 권한과 실제 운영 반영 범위 확정 |
| Space & Property Center | 채윤희 |  | 대출/품의 제출 가드레일 자동화 | 에이전트/워크플로우 | 바텀업 | 자동화 · 신규 서비스 · 문서작업 | 배포 URL | 대출/품의 자동화 | 260626 REQ | S4→S5 | MVP 구현 및 배포 완료, 현업 테스트 진입 | 미정 | 신청서·차용증서 오류를 제출 전 잡는 가드레일 MVP 구현/배포. 다음: 실제/익명화 샘플로 검증하고 운영 데이터·권한·보안 범위 확정 |
```

## 품질 기준

- 긴 일기형 로그보다 짧은 주간 증빙 로그를 우선한다.
- placeholder `X`를 남기지 않는다.
- 링크는 관련 주장 가까이에 둔다.
- 회의는 결정, 액션, 산출물이 있을 때만 진행 현황으로 계산한다.
- 규격 외 지원을 임팩트 과제 성과처럼 부풀리지 않는다.
- GitHub/commit 근거는 코드 산출물 증빙으로 쓰고, 임팩트 과제의 실제 완료 여부는 Confluence/Slack/회의/사용자 확인과 함께 판단한다.
- 주차 제목을 제외한 본문 날짜는 정확한 절대 날짜로 쓴다.
- 최종 답변에는 사용자가 바로 복사할 수 있는 Markdown 초안을 포함한다.
