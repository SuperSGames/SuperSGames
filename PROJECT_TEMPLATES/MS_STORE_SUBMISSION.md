# Microsoft Store 제출 공통 절차

## [최우선] 최신 버전 원본 고정 규칙

- 사용자가 명시적으로 이전 버전으로 돌아가라고 지시하지 않았다면 **무조건 검증된 최신 소스/배포본**을 기준으로 수정·제작·HTML/AIT 변환·빌드·테스트·배포한다. 과거 버전으로 임의로 되돌리지 않는다.
- 최신 GitHub 커밋과 실제 테스트 웹 내용을 대조한다. 사용자가 지정한 URL/빌드(특히 `/toss`)를 다른 경로나 예전 파일로 대체하지 않는다. 원본이 확인되지 않으면 최신이라고 주장하거나 임의 수정하지 않는다.
- 기존의 UI·기능·에셋·설정·광고·결제·진동을 모두 유지한 채 요청한 부분만 변경한다. 작업 기준 버전과 검증 상태를 명시한다. 상세 규칙은 각 프로젝트의 `AGENTS.md`를 최우선으로 따른다.


이 문서는 이 게임을 Microsoft Store에 제출할 때 사용하는 공통 절차다.
실제 화면·실제 공개 주소·실제 첨부 패키지에서 확인한 값만 사용하고 추측하지 않는다.

## 1. Toss용과 Microsoft 심사용 분리

- Toss용 버전과 Microsoft 심사용 버전은 기능·주소·패키지를 섞지 않는다.
- Toss용: 유료 결제, 광고, 광고 보상 등 Toss용으로 확정한 수익 기능을 유지한다.
- Microsoft 심사용: 유료 결제 UI를 제거 또는 비활성화하고, 광고 및 광고 보상 기능을 제거하며, 광고를 보고 단서를 찾는 기능도 제거한다.
- Microsoft 심사용: 랭킹 버튼과 랭킹 아이콘을 제거한다.
- Microsoft 심사용: 무료 플레이와 기본 게임 진행만 남기고 심사에 불필요한 외부 수익·경쟁 기능을 넣지 않는다.
- Microsoft 패키지는 반드시 Microsoft 심사용 주소와 소스에서 생성한다.
- Toss 패키지는 반드시 Toss용 주소와 소스에서 생성한다.
- 두 버전의 HTML, manifest, 아이콘, 패키지 파일을 한 폴더에 섞어 업로드하지 않는다.
- 수정 전 이름을 `Toss용` 또는 `Microsoft 심사용`으로 명확히 표시하고, 패키지 생성 직전에 다시 확인한다.

## 2. Microsoft 제출 패키지 기본값

- 기본 제출 패키지는 검증된 `.msixbundle` 1개로 한다.
- `.classic.appxbundle`은 실제 구형 Windows 호환 요구가 확인될 때만 추가한다.
- MSIX와 Classic을 이유 없이 함께 올리지 않는다. 같은 Identity·버전·아키텍처가 겹치면 중복 오류가 난다.
- 기존 submission에 오래된 패키지가 남아 있으면 새 패키지와 충돌 여부를 확인하고, 삭제 선택 후 반드시 Save로 확정한다.
- 노란 권한 경고와 빨간 validation error를 구분한다. 빨간 오류가 있으면 제출하지 않는다.

## 3. 제출 전 공개 게임 확인

Microsoft 심사용 공개 주소에서 다음을 확인한다.

- HTTPS 주소가 열린다.
- 첫 화면이 빈 화면이나 검은 화면으로 멈추지 않는다.
- 기본 퍼즐 조작이 작동한다.
- 새로고침 후 다시 표시된다.
- 고양이·상점·설정 등 주요 메뉴가 열린다.
- 심사용 버전에 광고, 유료 결제, 광고 보상, 광고 단서찾기, 랭킹 버튼·아이콘이 남아 있지 않다.
- 게임 제목과 manifest 이름이 일치한다.

확인하지 못한 항목은 테스트 완료라고 보고하지 않는다.

## 4. Partner Center Product identity

Partner Center 제품 페이지에서 다음 값을 직접 복사한다.

- Package/Identity/Name
- Package/Identity/Publisher
- Package/Properties/PublisherDisplayName
- 예약된 제품 이름

Publisher ID, Package ID, PFN을 기억으로 입력하거나 임의로 고치지 않는다.
대문자·소문자·하이픈·문자 하나가 달라도 package validation이 실패할 수 있다.

## 5. PWABuilder 패키지 생성

Microsoft 심사용 공개 주소를 PWABuilder에 입력한다.

- Package ID: Partner Center의 Package/Identity/Name 그대로
- Publisher ID: Partner Center의 Package/Identity/Publisher 그대로
- Publisher display name: Partner Center의 PublisherDisplayName 그대로
- App name: 예약된 제품 이름
- App version: 기존 Partner Center 패키지보다 높은 버전

패키지 버전은 기존 업로드 버전보다 높아야 한다.
새 패키지는 반드시 Microsoft 심사용 버전인지 확인한 뒤 생성한다.

## 6. 생성된 실제 MSIX 검사

첨부하거나 다운로드한 정확한 `.msixbundle` 파일을 검사한다.

- Bundle 압축 무결성
- 내부 APPX 압축 무결성
- Identity Name
- Publisher
- Version
- DisplayName
- TargetDeviceFamily
- Microsoft Edge 런타임 의존성
- `app-fallback-url` 또는 실제 시작 주소
- 아이콘과 리소스 포함 여부

패키지 내부 실행 주소가 Microsoft 심사용 공개 주소와 다르면 업로드하지 않는다.
웹 주소를 확인했다고 해서 첨부된 패키지까지 확인한 것으로 보고하지 않는다.

## 7. Partner Center Packages

1. Packages 페이지에서 Microsoft 심사용 패키지를 업로드한다.
2. `Analyzing package`가 끝날 때까지 기다린다.
3. 빨간 validation error가 없고 `Validated`인지 확인한다.
4. Windows Desktop 장치군을 확인한다.
5. 실패한 패키지에 `Retry`를 반복하지 말고 오류 원인을 먼저 확인한다.
6. 삭제를 선택했으면 페이지 하단 `Save`로 삭제를 확정한다.
7. Packages 상태가 `Complete`인지 확인한다.

`runFullTrust` 같은 노란 restricted capability warning은 빨간 validation error와 다르다.
경고만으로 정상 패키지를 삭제하거나 Classic 파일을 추가하지 않는다.

## 8. 제출 전 전체 항목

다음 항목이 모두 Complete인지 확인한다.

- Pricing and availability
- Properties
- Age ratings
- Packages
- Store listings
- Submission options

Xbox를 대상으로 출시하지 않는 Windows PC 게임이면 Xbox Creators Program을 임의로 시작하지 않는다.

## 9. 최종 제출

다음 조건을 모두 확인한 뒤 사용자가 PC Chrome에서 `Submit for certification`을 누른다.

- Packages가 Complete
- 패키지가 Validated
- 빨간 오류 없음
- 스토어 등록정보와 등급 완료
- Microsoft 심사용 기능 분리 확인 완료

제출 후 `In certification`이면 정상적으로 심사에 들어간 상태다.
심사 중에는 `Cancel certification`을 누르지 않는다.

## 10. 제출 후

- Pre-processing
- Certification
- Publishing

상태를 순서대로 확인한다.
인증 실패 시에는 인증 보고서의 실제 오류 문구를 기준으로 수정한다.

## 절대 금지

- Package ID·Publisher ID 임의 입력
- Toss용 주소를 Microsoft 제출 패키지에 사용
- Microsoft 심사용 주소를 Toss용 패키지에 사용
- 기존 패키지와 새 패키지의 중복 업로드
- 오류 파일에 Retry 반복
- 검증하지 않은 실행 주소를 정상이라고 보고
- 웹 원본 테스트를 MSIX 설치 테스트로 둔갑
- 노란 경고만으로 정상 패키지 삭제
- 클래식 패키지를 필요성 확인 없이 추가
- 사용자 확인 없이 최종 제출 버튼 클릭