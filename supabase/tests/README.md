# supabase/tests

RLS·권한 회귀 테스트(CI, 실패 시 머지 차단).

| 항목 | 내용 |
|---|---|
| 책임 | `rls_smoke.sql`(타 조직 0행·역할별 쓰기·함수 EXECUTE·상태 전이·잠금·승인 우회), `security/`(전 API 조직 간 차단) |
| 금지 | `core.*` ALTER(테스트 안에서도) |
| 담당 작업 ID | BM-06-006, 034(`security/`) |
| 근거 문서 | [DATABASE.md#4·#9](../../docs/DATABASE.md), [AGENT_PLAN.md#2](../../docs/AGENT_PLAN.md) |

상태: 기획 승인 전, 코드 없음
