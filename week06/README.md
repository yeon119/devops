# 6주차 - Dockerfile과 이미지 배포

## 배운 내용

### Dockerfile
- Dockerfile은 애플리케이션의 실행 환경과 이미지 생성 방법을 적은 파일이다.
- `FROM`은 기반 이미지를 지정하고, `WORKDIR`은 이미지 안의 작업 디렉터리를 정한다.
- `COPY`는 파일을 이미지에 복사하고, `RUN`은 이미지를 빌드할 때 명령어를 실행한다.
- `ENV`는 환경 변수의 기본값을 설정한다.
- `EXPOSE`는 컨테이너에서 사용할 포트를 문서화하지만, 호스트에 포트를 공개하지는 않는다.
- `CMD`는 컨테이너가 시작될 때 실행할 명령어를 지정한다.

### 이미지 빌드와 캐시
- `docker build`로 Dockerfile을 이용해 이미지를 만든다.
- 빌드 과정에서 변경되지 않은 단계는 캐시를 재사용할 수 있다.
- `requirements.txt`를 먼저 복사하고 라이브러리를 설치한 뒤 애플리케이션 코드를 복사하면, 코드만 수정했을 때 설치 단계를 다시 실행하지 않을 수 있다.

### 이미지 공유와 설정
- 이미지 이름은 레지스트리, 사용자 이름, 이미지 이름, 태그로 구성된다.
- 만든 이미지에 태그를 붙여 GHCR이나 Docker Hub에 올리고 다른 사람이 내려받아 실행할 수 있다.
- 앱의 설정값은 코드의 기본값, Dockerfile의 `ENV`, 컨테이너 실행 시의 `-e`로 지정할 수 있다. 이 수업의 방명록 앱에서는 `-e`가 `ENV`보다 우선하고, `ENV`가 코드의 기본값보다 우선한다.

## 새로 배운 명령어

| 명령어 | 하는 일 |
| --- | --- |
| `docker build -t guestbook:v1 .` | 현재 폴더의 Dockerfile로 이미지 빌드 |
| `docker images` | 로컬 이미지 목록 확인 |
| `docker run -d -p 8081:5000 --name gb guestbook:v1` | 만든 이미지를 컨테이너로 실행 |
| `docker logs gb` | 컨테이너 로그 확인 |
| `docker tag guestbook:v1 ghcr.io/사용자명/guestbook:v1` | 공유할 이미지 이름과 태그 지정 |
| `docker push ghcr.io/사용자명/guestbook:v1` | 이미지를 GHCR에 업로드 |
| `docker pull ghcr.io/사용자명/guestbook:v1` | GHCR에서 이미지 다운로드 |
| `docker history guestbook:v1` | 이미지의 생성 이력 확인 |
