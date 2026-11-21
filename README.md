# Mosigame Management

Mosigame의 공지·점검·푸시 알림 관리용 정적 웹 콘솔입니다.

## 제공 범위

- 최근 공지(A)와 서버 점검(B)의 다국어 내용·표시 여부 관리
- TEST 서버와 모시겜 본 서버를 페이지 안에서 즉시 전환
- 선택한 Firebase에 최근 60일 안에 등록된 휴대폰 전체로 다국어 푸시 알림 발송
- 발송 성공·실패 기기 수와 최근 이력 확인
- Firebase Authentication Google 로그인
- Firebase Custom Claim `operationsAdmin`을 가진 사용자만 저장 가능
- TEST Firebase: **`ban-pick-simulator`**
- 모시겜 본 서버 Firebase: **`project0000-ec01e`**

각 Firebase 앱의 인증·Firestore 구독·Functions 호출은 서로 분리됩니다. 푸시 발송은
`sendOperationsPushNotification` callable이 허용된 두 프로젝트 중 하나인지와
`operationsAdmin` 권한을 다시 검사한 뒤 실행합니다. 본 서버 저장과 발송은 추가 확인을
거치며, 기기 토큰은 화면과 발송 이력에 저장하거나 노출하지 않습니다.

## 배포

`main` 브랜치에 푸시하면 GitHub Actions가 GitHub Pages에 자동 배포합니다.
배포 후 GitHub Pages 주소의 도메인을 Firebase Authentication 허용 도메인에
추가해야 Google 로그인이 동작합니다.

두 Firebase 프로젝트 모두 GitHub Pages 도메인을 Authentication 허용 도메인에 등록하고,
사용할 운영자 계정에 `operationsAdmin` custom claim을 부여해야 합니다.
