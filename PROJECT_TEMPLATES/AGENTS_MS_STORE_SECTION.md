## Microsoft Store 제출 공통 규칙

## [최우선] 최신 버전 원본 고정 규칙

- 사용자가 명시적으로 이전 버전으로 돌아가라고 지시하지 않았다면 **무조건 검증된 최신 소스/배포본**을 기준으로 수정·제작·HTML/AIT 변환·빌드·테스트·배포한다. 과거 버전으로 임의로 되돌리지 않는다.
- 최신 GitHub 커밋과 실제 테스트 웹 내용을 대조한다. 사용자가 지정한 URL/빌드(특히 `/toss`)를 다른 경로나 예전 파일로 대체하지 않는다. 원본이 확인되지 않으면 최신이라고 주장하거나 임의 수정하지 않는다.
- 기존의 UI·기능·에셋·설정·광고·결제·진동을 모두 유지한 채 요청한 부분만 변경한다. 작업 기준 버전과 검증 상태를 명시한다. 상세 규칙은 각 프로젝트의 `AGENTS.md`를 최우선으로 따른다.


- 제출 전 `MS_STORE_SUBMISSION.md`를 먼저 읽는다.
- Toss용과 Microsoft 심사용 주소·소스·manifest·패키지를 분리한다.
- Microsoft 심사용에는 유료 결제, 광고, 광고 보상, 광고 단서찾기, 랭킹 버튼·아이콘을 넣지 않는다.
- Package ID, Publisher ID, 제품명, 버전, 실행 주소는 실제 화면과 실제 패키지에서 확인한다.
- 기본 제출은 검증된 `.msixbundle` 1개로 한다. Classic 패키지는 실제 호환성 요구가 있을 때만 추가한다.
- 빨간 validation error가 있으면 제출하지 않는다. 노란 권한 경고와 빨간 오류를 구분한다.
- 새 프로젝트는 `SuperSGames/SuperSGames`의 `NEW_PROJECT_BOOTSTRAP.md`와 `PROJECT_TEMPLATES/MS_STORE_SUBMISSION.md`를 복사한다.