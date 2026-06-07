---
name: fde-reference
description: FDE AI 위키의 가이드라인을 Confluence MCP로 로드하여 작업 및 위키 작성 시 참고. FDE 작업, 위키 작성, FDEWORK 스페이스 관련 작업 시 사용.
---

# FDE Reference

FDE AI 위키 페이지를 Confluence MCP로 로드하여 가이드라인을 참고하는 스킬.

## 워크플로우

### 1. 위키 페이지 로드
Confluence MCP를 사용해 FDE AI 위키를 로드:
- `mcp_confluence_get_page` 또는 `mcp_confluence_get_page_outline` 호출
- 페이지 ID: 1057405082
- 스페이스: FDEWORK

### 2. 일일 작업 참고
- 위키의 가이드라인, 포맷, 네이밍 컨벤션 등을 파악
- 현재 작업에 가이드라인 적용
- 작업 내용이 위키와 충돌하지 않는지 확인

### 3. 위키 작성 시 참고
- FDE AI 위키의 구조와 포맷을 따름
- 새 위키 작성 전 기존 위키의 섹션 구조, 스타일, 메타데이터 참고
- 위키 업데이트 시 `mcp_confluence_stage_page_section_update` → `mcp_confluence_preview_page_section_update` → `mcp_confluence_commit_pending_page_update` 워크플로우 사용

## 참고

핵심 가이드라인은 `docs/fde-ai-guidelines.md`에 단일 소스로 관리됨.
스킬은 Confluence MCP 접근이 필요한 경우에만 로드.
