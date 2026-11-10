# apps/web

Next.js 웹 앱 루트. 화면·Route Handler·서버 라이브러리를 담는다(세부는 하위 폴더 README).

| 항목 | 내용 |
|---|---|
| 책임 | `app/`(화면·API), `features/`(화면별 훅·폼·차트), `lib/{platform,credits,entitlements,telemetry}`, `middleware.*`, `tests/e2e` |
| 금지 | 계산 로직·금액·점수 판정(엔진 몫), 브라우저에서 AI 제공자 직접 호출, 번들에 service role 키 |
| 담당 작업 ID | BM-06-011(lib/platform·middleware), 031(lib/credits), 035·038(tests/e2e), 037(lib/entitlements), 040(lib/telemetry) |
| 근거 문서 | [ARCHITECTURE.md#2](../../docs/ARCHITECTURE.md), [AGENT_PLAN.md#1](../../docs/AGENT_PLAN.md), [AGENTS.md](../../AGENTS.md) |

상태: 기획 승인 전, 코드 없음
