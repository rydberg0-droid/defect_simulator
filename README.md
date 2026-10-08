# Defect Simulator (prototype)

Inner(셀 영역) 패턴 단면(채널 hole, Mold ON 적층, ACL 하드마스크, ONOP liner)에서 공정 flow를 **동영상처럼 재생**하고, 특정 시점·위치에 **결함을 떨어뜨려** 이후 공정에서 어떤 형상(bump, hole not-open, blocked 등)이 되는지 보는 단일 HTML 도구입니다.

- 실행: `index.html`을 브라우저로 열기 (외부 의존성·네트워크 없음) · https://rydberg0-droid.github.io/defect_simulator/
- 기본 예시: Mold flow 9개 그룹(pre cln → BSO → Mold → PES·ash·strip → BSO 교체 → ACL → mask etch → HARC → ONOP)
- 결함 예시: (a) ACL 전 W 파티클 → hole not-open, (b) HARC 후 hole 입구 SiN 조각 → ONOP 시 hole 막힘
- 재생/정지·속도·그룹 이동·녹화(webm), Edge 단면 탭(WEBC 엔진)

**추정 모델 프로토타입**입니다. 패턴 치수·식각 형상(taper, bowing)·레시피 값은 예시·추정이며 QA·리뷰 전입니다.

## 관련
- Edge 단면 시뮬레이터: https://github.com/rydberg0-droid/webc-simulator
- 이어받기: `docs/HANDOFF.md` · 사내(외부→사내 단방향): `docs/INTERNAL_WORKFLOW.md`
