## 1) 실행 환경
- OS: Ubuntu 26.04.1
- Shell: 5.3.9(1)-release
- Docker: 29.9.2
- Git: 2.53.0

## 2) 수행 체크리스트
- [o] 터미널 기본 조작 및 폴더 구성
- [x] 권한 변경 실습
- [x] Docker 설치/점검
- [x] hello-world 실행
- [x] Dockerfile 빌드/실행
- [x] 포트 매핑 접속(2회)
- [x] 바인드 마운트 반영
- [x] 볼륨 영속성
- [x] Git 설정 + VSCode GitHub 연동

## 3) 수행 로그(발췌)
 ### 터미널 기본 조작 및 폴더 구성
 - 현재 위치 확인
 ```
 hjh5466@GNIA-C201-H02:/mnt/c/Users/apple5466005466/hjh/hjh5466$ pwd
/mnt/c/Users/apple5466005466/hjh/hjh5466
```
 - 목록 확인(숨김 파일 포함)
 ```
 hjh5466@GNIA-C201-H02:/mnt/c/Users/apple5466005466/hjh/hjh5466$ ls -a
.  ..  .git  README.md
```
 - 이동
 ```
 hjh5466@GNIA-C201-H02:/mnt/c/Users/apple5466005466/hjh/hjh5466$ cd /
hjh5466@GNIA-C201-H02:/$ 
```
 - 생성
 ```
 hjh5466@GNIA-C201-H02:~$ mkdir hjh
hjh5466@GNIA-C201-H02:~$ ls
hjh
```
 - 복사
 ```
 hjh5466@GNIA-C201-H02:~$ cp test.txt copy.txt
hjh5466@GNIA-C201-H02:~$ ls
copy.txt  hjh  test.txt
```
 - 이동/이름변경
 ```
 hjh5466@GNIA-C201-H02:~$ mv copy.txt renamed.txt
hjh5466@GNIA-C201-H02:~$ ls
hjh  renamed.txt  test.txt
```
 - 삭제
 ```
 hjh5466@GNIA-C201-H02:~$ rm renamed.txt
hjh5466@GNIA-C201-H02:~$ ls
hjh  test.txt
```

   

