## Microsoft Store 제출 공통 규칙

- 제출 전 `MS_STORE_SUBMISSION.md`를 먼저 읽는다.
- Toss용과 Microsoft 심사용 주소·소스·manifest·패키지를 분리한다.
- Microsoft 심사용에는 유료 결제, 광고, 광고 보상, 광고 단서찾기, 랭킹 버튼·아이콘을 넣지 않는다.
- Package ID, Publisher ID, 제품명, 버전, 실행 주소는 실제 화면과 실제 패키지에서 확인한다.
- 기본 제출은 검증된 `.msixbundle` 1개로 한다. Classic 패키지는 실제 호환성 요구가 있을 때만 추가한다.
- 빨간 validation error가 있으면 제출하지 않는다. 노란 권한 경고와 빨간 오류를 구분한다.
- 새 프로젝트는 `SuperSGames/SuperSGames`의 `NEW_PROJECT_BOOTSTRAP.md`와 `PROJECT_TEMPLATES/MS_STORE_SUBMISSION.md`를 복사한다.