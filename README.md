# 1주차 미션 - 내 컴퓨터에 개발자용 작업실 꾸미기

## 1. 프로젝트 개요
### 1-1. 미션 목표
개발에 필요한 기본 환경을 직접 구축하고, 터미널, Docker, Git/GitHub의 기본적인 사용법을 익히는 것을 목표로 한다.
단순히 도구를 설치하는 것에 그치지 않고, 직접 명령어를 실행하고 결과를 확인하면서 개발 환경의 구성 원리와 각 도구의 역할을 이해하고자 한다.
### 1-2. 주요 수행 내용
* 터미널을 활용한 디렉토리 및 파일 생성, 이동, 복사, 삭제 실습
* 파일 및 디렉토리 권한 확인과 변경
* Docker 설치 및 이미지와 컨테이너 실행·관리
* Dockerfile을 활용한 커스텀 웹 서버 이미지 제작
* 포트 매핑을 통한 웹 서버 접속 확인
* 바인드 마운트 및 Docker 볼륨을 활용한 데이터 관리 실습
* Git 설정 및 GitHub 저장소 생성, VSCode 연동
* 각 실습 과정과 검증 결과를 README에 기록

## 2. 실행 환경
### 2-1. 운영체제 및 터미널
```
sw_vers
ProductName:		macOS
ProductVersion:		26.5.2
BuildVersion:		25F84
echo $SHELL
/bin/zsh
```
- OS: macOS 26.5.2
- Terminal: macOS Terminal
- Shell: Zsh (/bin/zsh)
### 2-2. Git 버전
```
git --version
git version 2.50.1 (Apple Git-155)
```
- Git 버전: 2.50.1
### 2-3. Docker 버전
```
docker --version
Docker version 29.9.3, build 5457199
```
- Docker 버전: 29.9.3

## 3. 수행 체크리스트
- [x] GitHub 저장소 생성

- [x] 터미널 기본 명령어 실행

- [x] 파일 및 디렉토리 권한 확인/변경

- [x] Docker 설치 및 실행 확인

- [ ] Docker 이미지 다운로드 및 확인

- [ ] hello-world 실행

- [ ] Ubuntu 컨테이너 실행

- [ ] 컨테이너 실행/중지/종료 확인

- [ ] Docker 로그 및 리소스 확인

- [ ] Dockerfile 작성 및 커스텀 이미지 빌드

- [ ] 포트 매핑 및 웹 서버 접속 확인

- [ ] 바인드 마운트 변경 사항 반영 확인

- [ ] Docker 볼륨 데이터 영속성 확인

- [ ] Git 사용자 정보 및 기본 브랜치 설정

- [ ] GitHub 및 VSCode 연동

- [ ] 트러블슈팅 2건 이상 정리

## 4. 터미널 기본 명령어 실습
### 4-1. 현재 위치 및 파일 목록 확인
```현재 위치 확인
pwd
/Users/mirim
```
- pwd 명령어를 통해 현재 작업 디렉토리의 위치가 /Users/Mirim임을 확인했습니다.
```
ls
Applications			Downloads			Parallels
Applications (Parallels)	Library				Pictures
Desktop				Movies				Public
Documents			Music
```
- ls 명령어를 통해 현재 디렉토리 내에 존재하는 파일 및 폴더 목록을 확인했습니다.
### 4-2. 디렉토리 및 파일 생성
```
mkdir codyssey-practice
cd codyssey-practice
```
- mkdir 명령어로 codyssey-practice라는 디렉토리를 만들고, cd 명령어로 생성한 디렉토리로 이동했습니다.
```
touch memo.txt
ls
memo.txt
```
- touch 명령어로 memo.txt 파일을 생성하였습니다.
- ls 명령어를 통해 파일이 정상적으로 생성되었음을 확인했습니다.
### 4-3. 파일 복사, 이름 변경, 이동, 삭제
```
cp memo.txt memo-copy.txt
ls
memo-copy.txt	memo.txt
```
- cp 명령어를 사용하여 memo.txt 파일을 memo-copy.txt라는 이름으로 복사했습니다.
- ls 명령어를 통해 원본 파일과 복사된 파일이 모두 존재하는 것을 확인했습니다.
```
mv memo-copy.txt new-memo.txt
ls  
memo.txt	new-memo.txt
```
- mv 명령어를 사용하여 memo-copy.txt 파일의 이름을 new-memo.txt로 변경했습니다.
- ls 명령어를 통해 파일 이름이 정상적으로 변경된 것을 확인했습니다.
```
mkdir backup
mv new-memo.txt backup/
ls
backup		memo.txt
ls backup
new-memo.txt
```
- 먼저 mkdir 명령어로 backup 디렉토리를 생성했습니다.
- mv 명령어를 사용하여 new-memo.txt 파일을 backup 디렉토리로 이동했습니다.
- ls 명령어를 통해 파일이 backup 디렉토리로 이동하고 기존 디렉토리에서 사라진 것을 확인했습니다.
```
rm backup/new-memo.txt
ls backup
(출력 사항 없음)
```
- rm 명령어를 사용하여 backup 디렉토리 안에 있는 new-memo.txt 파일을 삭제했습니다.
- ls 명령어를 통해 해당 디렉토리 내 파일이 삭제된 것을 확인했습니다.
### 4-4. 파일 내용 확인
```
echo "Hello Codyssey" > memo.txt 
cat memo.txt
Hello Codyssey
```
- echo 명령어와 > 기호를 사용하여 memo.txt 파일에 "Hello Codyssey" 라는 텍스트를 저장했습니다.
- cat 명령어를 사용하여 파일에 저장된 내용을 확인했습니다.
### 4-5. 실행 결과 및 배운 점
- 터미널에서도 마우스 없이 명령어만으로 파일과 디렉토리를 생성하고 관리할 수 있다는 사실을 배웠습니다. 또한 각 명령어의 기능과 차이를 직접 실행해 보면서 이해할 수 있었습니다.

## 5. 파일 및 디렉토리 권한 실습
### 5-1. 파일 권한 변경 전/후
```
ls -l memo.txt
-rw-r--r--  1 mirim  staff  15 11월 19 22:50 memo.txt
```
- ls -l 명령어로 memo.txt 파일의 상세 정보와 권한을 확인했습니다.
- 현재 소유자는 읽기와 쓰기가 가능하며, 그룹 사용자와 기타 사용자는 읽기만 가능합니다.
```
chmod 600 memo.txt
```
- chmod 명령어로 접근 권한을 변경하였습니다. 소유자는 읽기(4)와 쓰기(2)가 가능하도록 6, 그룹 사용자와 기타 사용자들은 기존 권한을 없애기 위해 각각 0으로 설정하였습니다.
```
ls -l memo.txt
-rw-------  1 mirim  staff  15 11월 19 22:50 memo.txt
```
- 다시 권한 확인 결과, 소유자만 파일을 읽고 수정할 수 있도록 권한이 변경되었습니다.
### 5-2. 디렉토리 권한 변경 전/후
```
ls -ld backup
drwxr-xr-x  2 mirim  staff  64 11월 19 22:36 backup
```
- ls -ld backup 명령어를 사용하여 backup 디렉토리 자체의 상세 정보와 현재 설정된 접근 권한을 확인하였습니다. 현재 소유자는 읽기, 쓰기, 실행 권한을 모두 가지고 있으며, 그룹 사용자와 기타 사용자는 읽기와 실행 권한만 가지고 있습니다.
```  
chmod 700 backup
```
- chmod 명령어로 backup 디렉토리의 접근 권한을 변경하였습니다. 소유자는 읽기(4) 쓰기(2) 실행(1) 권한을 모두 가질 수 있도록 4+2+1=7, 그룹 사용자와 기타 사용자는 모든 권한을 제거하기 위해 각각 0으로 설정하였습니다.
```
ls -ld backup
drwx------  2 mirim  staff  64 11월 19 22:36 backup
```
- 다시 backup 디렉토리의 권한을 확인한 결과, 소유자만 디렉토리 내부를 확인하고 파일을 생성하거나 삭제할 수 있도록 권한이 변경되었습니다.
### 5-3. 권한(r/w/x, 755, 644)의 의미
기본 권한의 의미

- r (Read): 파일 내용을 읽거나 디렉토리 내부 목록을 확인할 수 있는 권한
-  w (Write): 파일 내용을 수정하거나 디렉토리 내부에 파일을 생성 및 삭제할 수 있는 권한
-  x (Execute): 파일을 실행하거나 디렉토리에 접근하고 내부 항목을 탐색할 수 있는 권한

숫자로 표현하는 권한

각 권한은 숫자로 표현할 수 있으며, 여러 권한을 조합할 때는 해당 숫자를 더하여 사용합니다.

- r = 4
- w = 2
- x = 1

755 권한

- 소유자: 읽기(4) + 쓰기(2) + 실행(1) = 7
- 그룹 사용자: 읽기(4) + 실행(1) = 5
- 기타 사용자: 읽기(4) + 실행(1) = 5

644 권한

- 소유자: 읽기(4) + 쓰기(2) = 6
- 그룹 사용자: 읽기(4) = 4
- 기타 사용자: 읽기(4) = 4

755는 소유자에게 모든 권한을 부여하고, 그룹 사용자와 기타 사용자에게는 읽기 및 실행 권한을 부여합니다. 반면 644는 소유자에게 읽기 및 쓰기 권한을 부여하고, 나머지 사용자에게는 읽기 권한만 부여합니다.

## 6. Docker 설치 및 기본 점검
### 6-1. Docker 버전 확인
```
docker --version
Docker version 29.9.3, build 5457199
```
- docker --version 명령어로 docker 설치 여부와 버전을 확인하였습니다.
### 6-2. Docker 실행 상태 확인
```
docker info
Client:
 Version:    29.9.3
 Context:    desktop-linux
 Debug Mode: false

Server:
 Containers: 0
  Running: 0
  Paused: 0
  Stopped: 0
 Images: 0
 Server Version: 29.9.3
```
- docker info 명령어를 사용하여 Docker의 전반적인 실행 상태를 확인하였습니다. Client와 Server 정보가 정상적으로 출력되었고, Server의 버전 정보를 통해 Docker Engine이 정상적으로 연결되어 작동하고 있음도 확인했습니다.
- 전체 출력 결과 중 실습과 직접적인 관련이 없는 세부 정보는 제외했으며, 해당 정보는 스크린샷에서 확인하실 수 있습니다.
### 6-3. Docker 이미지 목록 확인
```
docker images
IMAGE   ID   DISK USAGE   CONTENT SIZE   EXTRA
```
- docker images 명령어로 로컬에 저장된 Docker 이미지 목록을 확인하였습니다. 이미지 목록은 비어있으며 현재 다운로드하거나 생성한 Docker 이미지가 없음을 확인할 수 있습니다.
### 6-4. 컨테이너 실행 및 관리
```
docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```
- docker ps 명령어를 사용하여 현재 실행중인 컨테이너 목록을 확인하였습니다. 현재 실행 중인 컨테이너는 없습니다.
```
docker ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```
- docker ps -a 명령어를 사용하여 실행 중인 컨테이너와 중지된 컨테이너를 포함한 전체 목록을 확인하였습니다. 현재 생성된 컨테이너, 중지된 컨테이너 모두 없습니다.
### 6-5. 로그 및 리소스 확인
```
docker logs
docker: 'docker logs' requires 1 argument
Usage:  docker logs [OPTIONS] CONTAINER
```
- docker logs 명령어로 컨테이너 로그 확인을 시도했습니다. 해당 명령어는 로그를 확인할 컨테이너 ID 또는 이름이 필요하며, 현재 생성된 컨테이너가 없어 로그를 조회할 수 없음을 확인했습니다.
```
docker stats
CONTAINER ID   NAME      CPU %     MEM USAGE / LIMIT   MEM %     NET I/O   BLOCK I/O   PIDS
```
- docker stats 명령어로 실행 중인 컨테이너의 리소스 사용량을 확인하였습니다. 현재 실행 중인 컨테이너가 없어 리소스 사용량이 표시되지 않음을 확인했습니다.
```
docker system df
TYPE            TOTAL     ACTIVE    SIZE      RECLAIMABLE
Images          0         0         0B        0B
Containers      0         0         0B        0B
Local Volumes   0         0         0B        0B
Build Cache     0         0         0B        0B
```
- docker system df 명령어를 사용하여 Docker의 전체 디스크 사용량을 확인했습니다. 모든 항목의 사용량이 0으로 표시되었으며, 현재 저장된 이미지나 컨테이너 등이 없음을 확인하였습니다.

## 7. 컨테이너 실행 실습
### 7-1. hello-world 실행
```
docker run hello-world
```
- docker run hello-world 명령어를 실행하여 hello-world 이미지를 기반으로 컨테이너를 생성하고 실행하는 실습입니다.
```
Unable to find image 'hello-world:latest' locally
```
- 현재 컴퓨터에 hello-world 이미지가 없어 Docker가 이미지를 다운로드하기 시작했습니다.
```
latest: Pulling from library/hello-world
```
- Docker Hub의 hello-world 이미지 중 latest(이미지의 버전을 구분하는 태그)가 지정된 이미지를 가져오기 시작했습니다.
```
58dee6a49ef1: Pull complete 
c3bdf82c34d1: Download complete
```
- 이미지를 구성하는 데이터들이 정상적으로 다운로드되었습니다.
```
Digest: sha256:1e4c05b897a751332ce85c7e9449da2d93514ea2dea6dbb0e2753c9e949b2bfa
Status: Downloaded newer image for hello-world:latest
```
- Status를 통해 hello-world 이미지 다운로드가 완료되었음을 확인하였습니다.
```
Hello from Docker!
This message shows that your installation appears to be working correctly.
```
- Hello from Docker! 메시지가 출력되면서 컨테이너가 정상적으로 실행되었음을 확인했습니다.
### 7-2. Ubuntu 컨테이너 실행 후 간단 명령 수행
```
docker run -it ubuntu bash
```
- Ubuntu 이미지를 기반으로 새로운 컨테이너를 만들고 실행하는 실습입니다.
```
Unable to find image 'ubuntu:latest' locally
```
- 현재 컴퓨터에 Ubuntu 이미지가 없어 Docker가 이미지를 다운로드하기 시작했습니다.
```
latest: Pulling from library/ubuntu
```
- Docker Hub에서 Ubuntu 이미지를 가져오고 있습니다.
```
cedc468d06b2: Pull complete 
7f2c2ca81066: Pull complete 
9d297c90b98f: Download complete
```
- Ubuntu 이미지를 구성하는 데이터들을 다운로드하는 중입니다.
```
Status: Downloaded newer image for ubuntu:latest
```
- Ubuntu 이미지 다운로드가 완료되었습니다.
```
root@e7bd23a814bb:/#
```
| 구성 요소 | 의미 |
|-----------|------|
| `root` | 현재 접속한 사용자의 이름 |
| `e7bd23a814bb` | 컨테이너 ID의 일부 |
| `/` | 현재 위치가 최상위 디렉토리임을 의미 |
| `#` | root 권한으로 명령어w 입력할 수 있다는 표시 |
- Ubuntu 컨테이너 내부로 정상적으로 진입했음을 확인하였습니다.
```
ls
bin   dev  home  media  opt   root  sbin  sys  usr
boot  etc  lib   mnt    proc  run   srv   tmp  var
```
- ls 명령어를 통해 Ubuntu 컨테이너의 최상위 디렉토리(`/`)에 있는 기본 폴더 목록을 확인하였습니다.
```
echo "Hello Ubuntu!"
Hello Ubuntu!
```
- echo 명령어로 입력한 문자열이 터미널에 정상적으로 출력되는지 확인하였습니다.
### 7-3. 컨테이너 종료 및 유지 방식 비교
```
exit
exit
```
- exit 명령어로 Ubuntu 컨테이너 내부에서 빠져나왔습니다. 실행 중이던 bash 프로세스가 종료되면서 컨테이너도 종료되었습니다.
```
docker ps -a
CONTAINER ID   IMAGE    COMMAND   STATUS
e7bd23a814bb   ubuntu   "bash"    Exited (0)
```
- Exited (0) 상태를 통해 Ubuntu 컨테이너가 오류 없이 정상적으로 종료되었음을 확인했습니다.
```
docker run -d --name ubuntu-keep ubuntu sleep infinity
c08eca8c6aea6cb6afd1da6408b260da6f13f947b8b18676ff6ff25317ccdbf5
docker ps
CONTAINER ID   IMAGE     COMMAND            CREATED         STATUS         PORTS     NAMES
c08eca8c6aea   ubuntu    "sleep infinity"   7 seconds ago   Up 6 seconds             ubuntu-keep
```
- 유지 실습을 위해 새 컨테이너를 만들고, --name 옵션을 사용하여 이름을 ubuntu-keep으로 지정했습니다.
- sleep infinity 명령어를 통해 컨테이너 내부에서 프로세스가 계속 실행되도록 하여 컨테이너가 종료되지 않고 유지되도록 했습니다.
```
docker exec -it ubuntu-keep bash
exit
docker ps
CONTAINER ID   IMAGE     COMMAND            STATUS         NAMES
c08eca8c6aea   ubuntu    "sleep infinity"   Up 4 minutes   ubuntu-keep
```
- docker exec 명령어를 사용하여 실행 중인 ubuntu-keep 컨테이너 내부에 진입한 후, exit으로 빠져나왔습니다.
- docker ps로 상태를 다시 확인한 결과, 컨테이너가 여전히 Up 상태로 유지되는 것을 확인했습니다.
## 8. Dockerfile 작성 및 커스텀 이미지 제작
### 8-1. 프로젝트 구조
```
cd ~/codyssey-practice
mkdir app
codyssey-practice % ls -a
.		..		app		backup		memo.txt
touch app/index.html
ls -la app
total 0
-rw-r--r--  1 mirim  staff    0 11월 22 18:07 index.html
```
- 웹 서버에서 제공할 정적 HTML 파일을 관리하기 위해 기존 디렉토리인 codyssey-practice 안에 app 디렉토리를 생성하고, 해당 디렉토리 내부에 index.html 파일을 생성하였다.
```
codyssey-practice/
│
├── backup/
├── memo.txt
│
└── app/
    └── index.html
```
### 8-2. 베이스 이미지 선정
```
docker pull nginx:latest
...
Status: Downloaded newer image for nginx:latest
docker.io/library/nginx:latest
docker images
IMAGE                ID             DISK USAGE   CONTENT SIZE   EXTRA
nginx:latest         84f7876d21d1        261MB         65.1MB
```
- 커스텀 웹 서버 이미지를 제작하기 위한 베이스 이미지로 NGINX 공식 이미지를 선정하였다.
- NGINX는 HTML, CSS, JavaScript 등의 정적 콘텐츠를 제공할 수 있는 웹 서버로, 별도의 복잡한 서버 프로그래밍 없이 간단한 웹 서버를 구축할 수 있다는 장점이 있다. 또한 Docker Hub에서 공식 이미지를 제공하므로 기존 이미지를 활용하여 효율적으로 커스텀 이미지를 제작할 수 있다.
### 8-3. Dockerfile 및 웹 서버 소스코드 작성
```
cat > app/index.html <<'EOF'
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>My Docker Web Server</title>
</head>
<body>
    <h1>Hello, Docker!</h1>
    <p>This is my first custom web server.</p>
    <p>Powered by NGINX.</p>
</body>
</html>
EOF
```
- index.html 안에 NGINX 웹 서버에서 표시할 HTML 소스코드를 입력했습니다.
- 기존에 open -e app/index.html 명령어로 텍스트 편집기를 열어 해당 내용을 입력할 계획이었으나 문제가 발생했습니다. 해당 문제는 목차 12 트러블슈팅에 기술하였습니다.
```
touch Dockerfile
open -e Dockerfile
```
- touch 명령어로 Dockerfile 생성 후, Dockerfile을 텍스트 편집기로 열어 아래 코드를 입력하였습니다.
```
FROM nginx:latest
COPY app/index.html /usr/share/nginx/html/index.html
EXPOSE 80
```
- FROM nginx:latest : NGINX 최신 버전을 기반 이미지로 지정하였습니다.
- COPY : 직접 작성한 HTML 파일을 NGINX의 기본 웹 페이지 저장 경로(/usr/share/nginx/html/index.html)에 복사하도록 설정하였습니다. 이를 통해 NGINX의 기존 기본 환영 페이지를 직접 제작한 웹 페이지로 교체하여 정적 콘텐츠를 커스터마이징하였습니다.
- EXPOSE 80 : 컨테이너에서 사용할 포트 번호를 80번으로 지정하였습니다.
### 8-4. 커스텀 이미지 빌드
```
docker build -t my-web-server .
[+] Building 1.3s (7/7) FINISHED   
```
- 작성한 Dockerfile을 기반으로 my-web-server라는 이름의 Docker 이미지를 생성하였습니다.
- 빌드 과정이 오류 없이 완료되어 커스텀 이미지 생성에 성공하였습니다.
### 8-5. 컨테이너 실행 및 결과 확인
```
docker run -d -p 8080:80 --name my-web-container my-web-server
```
- 앞서 생성한 my-web-server 이미지를 이용하여 my-web-container라는 이름의 컨테이너를 실행하였습니다.
- -p 8080:80 옵션을 사용하여 호스트의 8080번 포트와 컨테이너의 80번 포트를 연결하였습니다.
- 웹 브라우저에서 http://localhost:8080에 접속한 결과, 직접 작성한 HTML 콘텐츠인 Hello, Docker!, This is my first custom web server., Powered by NGINX.가 화면에 정상적으로 표시되는 것을 확인하였습니다.
- 이를 통해 커스텀 이미지로 컨테이너를 실행하고, 직접 제작한 정적 콘텐츠가 정상적으로 적용되었음을 확인하였습니다.

## 9. 포트 매핑 및 웹 서버 접속
### 9-1. 포트 매핑 실행 명령어
### 9-2. 브라우저 접속 결과
### 9-3. 포트 매핑이 필요한 이유

## 10. 바인드 마운트 및 Docker 볼륨
### 10-1. 바인드 마운트 실행
### 10-2. 호스트 파일 변경 전/후 비교
### 10-3. Docker 볼륨 생성 및 연결
### 10-4. 컨테이너 삭제 전/후 데이터 비교
### 10-5. 바인드 마운트와 볼륨의 차이

## 11. Git 및 GitHub 연동
### 11-1. Git 사용자 정보 설정 및 기본 브랜치 설정
### 11-3. GitHub 저장소 생성 및 연동
### 11-4. VSCode GitHub 로그인 및 연동

## 12. 트러블슈팅
### 12-1. 문제 상황 1

8-3. Dockerfile 및 웹 서버 소스코드 작성 과정에서 index.html 파일에 다음과 같은 HTML 코드를 작성하고자 하였습니다.

```
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>My Docker Web Server</title>
</head>
<body>
    <h1>Hello, Docker!</h1>
    <p>This is my first custom web server.</p>
    <p>Powered by NGINX.</p>
</body>
</html>
```

그러나 cat app/index.html 명령어로 파일 내용을 확인한 결과, 작성한 코드가 아닌 TextEdit의 서식 정보가 포함된 HTML 문서가 아래처럼 출력되었습니다.

```
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<html>
<head>
  <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
  <meta http-equiv="Content-Style-Type" content="text/css">
  <title></title>
  <meta name="Generator" content="Cocoa HTML Writer">
  <meta name="CocoaVersion" content="2685.6">
  <style type="text/css">
    p.p1 {margin: 0.0px 0.0px 0.0px 0.0px; font: 12.0px Helvetica}
  </style>
</head>
<body>
<p class="p1">&lt;!DOCTYPE html&gt;</p>
<p class="p1">&lt;html lang="ko"&gt;</p>
<p class="p1">&lt;head&gt;</p>
<p class="p1"><span class="Apple-converted-space">    </span>&lt;meta charset="UTF-8"&gt;</p>
<p class="p1"><span class="Apple-converted-space">    </span>&lt;title&gt;My Docker Web Server&lt;/title&gt;</p>
<p class="p1">&lt;/head&gt;</p>
<p class="p1">&lt;body&gt;</p>
<p class="p1"><span class="Apple-converted-space">    </span>&lt;h1&gt;Hello, Docker!&lt;/h1&gt;</p>
<p class="p1"><span class="Apple-converted-space">    </span>&lt;p&gt;This is my first custom web server.&lt;/p&gt;</p>
<p class="p1"><span class="Apple-converted-space">    </span>&lt;p&gt;Powered by NGINX.&lt;/p&gt;</p>
<p class="p1">&lt;/body&gt;</p>
<p class="p1">&lt;/html&gt;</p>
</body>
</html>
```

Mac의 기본 텍스트 편집기인 TextEdit이 HTML 코드를 일반 텍스트로 저장하지 않고, 서식 있는 문서 형식으로 저장했기 때문입니다. 이 과정에서 입력한 HTML 코드가 일반 텍스트로 처리되어 별도의 HTML 문서 구조로 변환되었습니다.

해당 문제를 해결하기 위해, 터미널에 다음과 같이 입력했습니다.

```
cat > app/index.html <<'EOF'
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>My Docker Web Server</title>
</head>
<body>
    <h1>Hello, Docker!</h1>
    <p>This is my first custom web server.</p>
    <p>Powered by NGINX.</p>
</body>
</html>
EOF
```

cat > app/index.html: 지정한 파일에 새로운 내용을 작성하며, 기존 파일의 내용은 덮어씁니다.

<<'EOF': Here Document 문법으로, 지정한 종료 문자열이 나올 때까지 입력한 내용을 전달합니다.

EOF: 입력이 끝났음을 나타내는 종료 문자열입니다.

```
cat app/index.html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>My Docker Web Server</title>
</head>
<body>
    <h1>Hello, Docker!</h1>
    <p>This is my first custom web server.</p>
    <p>Powered by NGINX.</p>
</body>
</html>
```

다시 cat app/index.html로 확인한 결과, HTML 소스 코드가 의도한 형태로 정상 저장되었음을 확인하였습니다.

### 12-2. 문제 상황 2

