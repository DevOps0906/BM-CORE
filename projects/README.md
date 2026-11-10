# projects — 제품·사업 아이템별 BM 결과

사업 아이템마다 폴더를 하나 만들고, 사업계획서를 쓸 때 이 폴더의 파일을 근거로 씁니다.

| 파일 | 내용 | 만드는 법 |
|---|---|---|
| `<아이템>/BM.md` | BM 7단계 결과(고객·가치·가격·단위경제·파트·린 검증·점수) | nomad-agent-os `/bm <아이템>`. 숫자는 `bm-calc`로 계산 |
| `<아이템>/bm-input.json` | `bm-calc` 입력(가격·변동비·이탈률·고정비·시나리오·점수) | `bm-calc --init <아이템>/bm-input.json` 후 수정 |
| `<아이템>/canvas.md` | 비즈니스 모델 캔버스 9블록 | [`../canvas/BMC_TEMPLATE.md`](../canvas/BMC_TEMPLATE.md)를 복사해 채움 |
| `<아이템>/evidence/` | 인터뷰 기록·결제 내역 같은 증거(등급 A~E 표기) | 실험할 때마다 추가 |
| `<아이템>/business-plan.md` | 사업계획서 초안 | [`../business-plan/PSST_MAPPING.md`](../business-plan/PSST_MAPPING.md) 순서로 위 파일을 옮겨 씀 |

규칙
- 방법은 [`../method/BM_METHOD.md`](../method/BM_METHOD.md)를 따릅니다.
- 계산값은 손으로 쓰지 않고 `bm-calc` 출력을 붙입니다.
- 증거 등급 E(가정)를 사업계획서에 쓸 때는 "가정"이라고 적습니다.
- 개인정보가 담긴 인터뷰 원문은 이 저장소(공개)에 올리지 않고 요약만 둡니다.

아직 등록된 아이템은 없습니다.
