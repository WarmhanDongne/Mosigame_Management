# Mosigame Management

Mosigame의 공지·점검 관리용 정적 웹 콘솔입니다.

## 제공 범위

- 최근 공지(A)와 서버 점검(B)의 다국어 내용·표시 여부 관리
- Firebase Authentication Google 로그인
- Firebase Custom Claim `operationsAdmin`을 가진 사용자만 저장 가능
- 대상 Firebase: **`ban-pick-simulator` 테스트 프로젝트**

일반 푸시 알림(FCM)은 아직 이 콘솔에서 발송하지 않습니다.

## 배포

`main` 브랜치에 푸시하면 GitHub Actions가 GitHub Pages에 자동 배포합니다.
배포 후 GitHub Pages 주소의 도메인을 Firebase Authentication 허용 도메인에
추가해야 Google 로그인이 동작합니다.

운영 Firebase로 전환할 때는 먼저 별도의 검토를 거쳐 Firebase 설정과 배포 대상을
명시적으로 바꿔야 합니다.
