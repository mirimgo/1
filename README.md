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
- [ ] GitHub 저장소 생성

- [ ] 터미널 기본 명령어 실행

- [ ] 파일 및 디렉토리 권한 확인/변경

- [ ] Docker 설치 및 실행 확인

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

## 6. Docker 설치 및 기본 점검
### 6-1. Docker 버전 확인
### 6-2. Docker 실행 상태 확인
### 6-3. Docker 이미지 목록 확인
### 6-4. 컨테이너 실행 및 관리
### 6-5. 로그 및 리소스 확인

## 7. 컨테이너 실행 실습
### 7-1. hello-world 실행
### 7-2. Ubuntu 컨테이너 실행
### 7-3. 컨테이너 종료 및 유지 방식 비교

## 8. Dockerfile 작성 및 커스텀 이미지 제작
### 8-1. 프로젝트 구조
### 8-2. Dockerfile 내용
### 8-3. 커스텀 이미지 빌드
### 8-4. 컨테이너 실행 결과
### 8-5. 커스텀 내용 및 목적

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
### 11-1. Git 사용자 정보 설정
### 11-2. 기본 브랜치 설정
### 11-3. GitHub 저장소 생성 및 연동
### 11-4. VSCode GitHub 로그인 및 연동

## 12. 트러블슈팅
### 12-1. 문제 상황 1
### 12-2. 문제 상황 2

## 13. Git과 GitHub의 역할 차이

## 14. 미션 수행 후기 및 배운 점

## 15. 제출 링크 및 참고 자료
