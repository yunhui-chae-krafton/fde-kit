# FDE AI Guidelines

FDE AI 위키의 핵심 가이드라인 참조 문서.

## 위키 정보

- **Confluence 스페이스**: FDEWORK
- **위키 페이지 ID**: 1057405082
- **위키 URL**: https://krafton.atlassian.net/wiki/spaces/FDEWORK/pages/1057405082/FDE+AI

## 일일 작업 참고

- 위키의 가이드라인, 포맷, 네이밍 컨벤션 등을 파악하고 적용
- 현재 작업이 위키 가이드라인과 충돌하지 않는지 확인
- 작업 전 위키의 최신 내용을 참조하여 기준에 맞게 수행

## 위키 작성 시 참고

- FDE AI 위키의 기존 구조와 포맷을 따름
- 새 위키 작성 전 기존 위키의 섹션 구조, 스타일, 메타데이터 참고
- 섹션 구조, 헤딩 레벨, 표 포맷 등 기존 컨벤션 유지

## Confluence MCP 워크플로우 (opencode / Claude Code)

위키 접근이 필요한 경우:

1. `mcp_confluence_get_page` 또는 `mcp_confluence_get_page_outline` 호출 (페이지 ID: 1057405082)
2. 위키 업데이트 시 `mcp_confluence_stage_page_section_update` → `mcp_confluence_preview_page_section_update` → `mcp_confluence_commit_pending_page_update` 워크플로우 사용
3. 직접 create/update 권한은 제한됨 (stage → preview → commit 프로세스 필수)
