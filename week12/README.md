# 12주차 GitHub Actions 실습

## 진행 내용
- PR과 main 푸시에서 실행되는 GitHub Actions 워크플로 작성
- Ruff 린트와 방명록 앱 테스트 실행
- 검사 통과 후 이미지를 GHCR에 게시
- 새 이미지로 Kubernetes guestbook 배포 후 화면의 `new` 확인
- 문법 오류, 린트 오류, 테스트 오류를 넣어 CI 실패 확인 후 수정
- main 브랜치에 PR과 build 검사 필수 규칙 설정
- 직접 푸시 차단과 실패한 PR의 병합 차단 확인

## 결과
- PR #3: 워크플로 추가 및 이미지 게시
- PR #4: 오류별 CI 실패와 수정 확인
- PR #5: 보호 규칙 적용 후 실패한 PR 수정 및 병합
