# supabase

`bm` 스키마 DB: 마이그레이션(2700대), seed, RLS 테스트.

| 항목 | 내용 |
|---|---|
| 책임 | `migrations/`(2700~2740), `seed.sql`, `tests/`(RLS 스모크·보안 회귀) |
| 금지 | `core.*` ALTER, 코어 테이블 신규 생성(organizations·org_members·subscriptions·credit_ledger·jobs·audit_log) |
| 담당 작업 ID | BM-06-003, 004, 005, 006, 034 |
| 근거 문서 | [ARCHITECTURE.md#2](../docs/ARCHITECTURE.md), [AGENT_PLAN.md#1](../docs/AGENT_PLAN.md), [DATABASE.md#9](../docs/DATABASE.md) |

상태: 기획 승인 전, 코드 없음
