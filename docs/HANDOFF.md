# 이어받기 문서 (HANDOFF) — Defect Simulator

## 상태
- 프로토타입. `index.html` 하나(외부 의존성 없음). QA·코드 리뷰 전이며 사용자가 "수정할 부분이 많다"고 함 → 사용자 피드백을 받아 개선.
- 출발점: WEBC Simulator(https://github.com/rydberg0-droid/webc-simulator)의 엔진·데이터를 **복사**해 만들었다. 두 저장소의 엔진/데이터(CLN_DB, ETCH, SLURRY_DB 등)는 자동 동기화되지 않는다. 필요해지면 공통 엔진을 별도 파일로 분리한다.

## 구조
- `PLAYER`: 재생·스크러버·속도·그룹 이동·캡션·녹화(MediaRecorder webm).
- `INNER`: 2D 셀 격자(가로 2.5nm × 세로 5nm) 재료 맵. hole pitch/CD(예시 160/120nm), Mold 대표 8겹(실제 쌍 수 라벨), 이방성 식각(taper·bowing est), conformal 증착, 재료별 선택비는 WEBC 데이터 재사용(데이터 없음 = 정지+경고).
- `DEFECT`: 결함 단계 type 'defect'(시점·x 위치·크기·성분) → 이후 공정에서 bump/micro-masking/hole not-open·blocked 판정.
- 저장 파일: `.webc.json` format 'webc-recipe' **version 4**(defect 단계 포함). WEBC 본체(v3)와 호환 안 됨.

## 지켜야 할 결정
- 보안: 외부 전송·외부 API 사용 안 함, 문헌/예시 값만, 사내 데이터는 사내 git에만(외부→사내 단방향, `docs/INTERNAL_WORKFLOW.md`).
- 색: Oxide 파랑, Nitride 녹색, Carbon 보라, W 은색, Cu 구리색.

## 알려진 한계 / 남은 작업
- 격자 해상도로 5nm 미만 막은 근사, taper가 계단으로 보임.
- 가정: hole 패턴은 이미 인쇄됨, 식각은 대상 막 소진까지, bowing은 단순 부풀림, ONOP 시 ACL 잔존.
- 결함 단계는 층 수 상한 검사에서 제외됨, '떨어지는 시점' 선택이 현재 단계를 따라가지 않음.
- 실제 브라우저에서 녹화(webm)·재생 애니메이션 수동 확인 필요.
- 향후: SEM 이미지 기반 원인 추정(위치·EDX·검사 단계 + 시뮬레이터 규칙 기반 → 학습형) 검토.
