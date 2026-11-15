# SuperSGames 전체 게임 — 짧은 채팅 인계 (2026-11-15)

> **대화 길이 절약:** 매 요청에 모든 프로젝트 MD를 읽지 않는다. 먼저 정확한 대상 게임을 결정한 뒤 해당 게임의 `PROJECT_HANDOFF.md` → `AGENTS.md` → 요청 관련 문서 일부 순서로 필요한 내용만 조회한다.

## 프로젝트 위치
- 냥냥버블팡: `SuperSGames/bubble`
- 냥냥검사: `SuperSGames/sword`
- 냥냥 밀어냥/소코반: `SuperSGames/sokoban`
- 냥냥수비대: `SuperSGames/defense` 저장소가 남아 있지만 **사용자가 프로젝트 삭제를 밝혔다. 비활성/보관 기록**으로만 취급하고 명시적 재개 요청 없이 현재 개발 대상에 포함하거나 수정하지 않는다.
- 땅파기: `SuperSGames/dig`
- 너무 완벽한 내 남편: `SuperSGames/husband`
- 화투사천성: **별도 저장소** `SuperSGames/hwatu-sichuan`의 `public/index.html`과 `wrangler.toml`(`assets.directory = "./public"`)이 현재 확인된 배포 소스다. 중앙 저장소의 `hwatu/index.html`(약 3.1MB)은 **동일한 배포 입력 경로가 아니므로** 화투사천성 작업 시 임의로 편집·배포하지 않는다.
- 냥냥블리츠: 이 중앙 저장소의 `blitz/` 하위 폴더 (독립 저장소로 추측하지 않는다).
- 그 밖의 라이브러리 전용 프로젝트는 해당 프로젝트 MD와 실제 원본/배포 주소가 확인될 때만 처리한다.

## 공통 작업
- 사용자가 선택한 완성본·실제 최신 GitHub 커밋·테스트 웹·빌드를 대조하고 요청한 부분만 최소 수정한다.
- 승인 아트·UI/화면·코드/저장·밸런스·MS/Toss 분리를 보존한다. 상태 정보는 코드, 원화는 PNG/WebP. UI는 [공통 UI v4](PROJECT_TEMPLATES/UI.md)를 필요할 때 읽는다.
- Cloudflare 배포 성공·테스트 웹 최신 반영은 GitHub 커밋과 별도 검증한다. 문서만 수정할 때 코드를 변경하거나 게임 배포 완료라고 주장하지 않는다.
- 상세 계획·개발 이력·아카이브는 문제에 관련된 단락만 검색한다. 대화가 길어져도 작업 기준을 파일로 복구할 수 있게 한다.

## 백업
- 공통 문서 정리 전: `backup/docs-precleanup-2026-11-15` 브랜치.
- 추가 전수 검토/경량화 전: `backup/docs-before-full-audit-2026-11-15` 브랜치.

## 빠른 코드 탐색 지도 (2026-11-15)

- 냥냥블리츠: `blitz/index.html`(약 104KB), `blitz/assets/` — 이 폴더 작업에 **별개 `hwatu/index.html`(약 3.1MB)을 함께 읽지 않는다**.
- 공통 지침: `AGENTS.md`, `PROJECT_TEMPLATES/UI.md`. 게임별 최신 기준은 각 게임 저장소에서 찾는다.

- **작업 루틴:** ① 사용자 지정 기준본·실제 SHA 확인 ② 파일 목록/이름으로 구현 위치 파악 ③ 관련 함수·호출자·저장/이벤트 영향 분석 ④ 요청한 최소 차이만 변경 ⑤ 정적 검사·실행 테스트·배포 결과 구분. 대형 소스/문서 전문을 매번 대화로 출력하지 않는다.
