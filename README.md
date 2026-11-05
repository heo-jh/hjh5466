## 1) 실행 환경
- OS: Ubuntu 26.04.1
- Shell: 5.3.9(1)-release
- Docker: 29.9.2
- Git: 2.53.0

## 2) 수행 체크리스트
- [o] 터미널 기본 조작 및 폴더 구성
- [o] 권한 변경 실습
- [o] Docker 설치/점검
- [x] Docker 기본 운영 명령 수행
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

### 권한 변경 실습
 - 파일 권한 변경
 ```
 hjh5466@GNIA-C201-H02:~$ ls -l
 total 4
 drwxr-xr-x 2 hjh5466 hjh5466 4096 Nov  5 15:48 hjh
 -rw-r--r-- 1 hjh5466 hjh5466    0 Nov  5 15:49 test.txt
 hjh5466@GNIA-C201-H02:~$ chmod 755 test.txt
 hjh5466@GNIA-C201-H02:~$ ls -l
 total 4
 drwxr-xr-x 2 hjh5466 hjh5466 4096 Nov  5 15:48 hjh
 -rwxr-xr-x 1 hjh5466 hjh5466    0 Nov  5 15:49 test.txt
 ```

 - 디렉토리 권한 변경
 ```hjh5466@GNIA-C201-H02:~$ ls -ld testdir
 drwxr-xr-x 2 hjh5466 hjh5466 4096 Nov  5 15:57 testdir
 hjh5466@GNIA-C201-H02:~$ chmod 700 testdir
 hjh5466@GNIA-C201-H02:~$ ls -ld testdir
 drwx------ 2 hjh5466 hjh5466 4096 Nov  5 15:57 testdir
 hjh5466@GNIA-C201-H02:~$ 
 ```

### Docker 설치/점검
 - Docker 설치 
 ```
 hjh5466@GNIA-C201-H02:~$ docker --version
 Docker version 29.9.2, build a82e528
 ```

 - Docker 기본 점검
 ```
 hjh5466@GNIA-C201-H02:~$ docker info
Client:
 Version:    29.9.2
 Context:    default
 Debug Mode: false
 Plugins:
  agent: Docker AI Agent Runner (Docker Inc.)
    Version:  v1.152.0
    Path:     /usr/local/lib/docker/cli-plugins/docker-agent
  ai: Docker AI Agent - Ask Gordon (Docker Inc.)
    Version:  v1.33.0
    Path:     /usr/local/lib/docker/cli-plugins/docker-ai
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.38.1
    Path:     /usr/local/lib/docker/cli-plugins/docker-buildx
  compose: Docker Compose (Docker Inc.)
    Version:  v5.6.1
    Path:     /usr/local/lib/docker/cli-plugins/docker-compose
  debug: Get a shell into any image or container (Docker Inc.)
    Version:  0.49.0
    Path:     /usr/local/lib/docker/cli-plugins/docker-debug
  desktop: Docker Desktop commands (Docker Inc.)
    Version:  4.98.0
    Path:     /usr/local/lib/docker/cli-plugins/docker-desktop
  dhi: CLI for managing Docker Hardened Images (Docker Inc.)
    Version:  v0.0.9
    Path:     /usr/local/lib/docker/cli-plugins/docker-dhi
  extension: Manages Docker extensions (Docker Inc.)
    Version:  v0.2.32
    Path:     /usr/local/lib/docker/cli-plugins/docker-extension
  init: Creates Docker-related starter files for your project (Docker Inc.)
    Version:  v1.4.1
    Path:     /usr/local/lib/docker/cli-plugins/docker-init
  mcp: Docker MCP Plugin (Docker Inc.)
    Version:  v0.44.2
    Path:     /usr/local/lib/docker/cli-plugins/docker-mcp
  model: Docker Model Runner (Docker Inc.)
    Version:  v1.2.9
    Path:     /usr/local/lib/docker/cli-plugins/docker-model
  offload: Docker Offload (Docker Inc.)
    Version:  v0.7.35
    Path:     /usr/local/lib/docker/cli-plugins/docker-offload
  pass: Docker Pass Secrets Manager Plugin (beta) (Docker Inc.)
    Version:  v0.3.2
    Path:     /usr/local/lib/docker/cli-plugins/docker-pass
  sandbox: "docker sandbox" is deprecated, use Docker Sandboxes instead (Docker Inc.)
    Version:  v0.13.0
    Path:     /usr/local/lib/docker/cli-plugins/docker-sandbox
  scout: Docker Scout (Docker Inc.)
    Version:  v1.27.0
    Path:     /usr/local/lib/docker/cli-plugins/docker-scout

Server:
permission denied while trying to connect to the docker API at unix:///var/run/docker.sock
```

### Docker 기본 운영 명령 수행
- 이미지
```
hjh5466@GNIA-C201-H02:~$ sudo docker images
[sudo: authenticate] Password:    
                                                                                                                                                                    i Info →   U  In Use
IMAGE   ID             DISK USAGE   CONTENT SIZE   EXTRA
```

- 컨테이너
```
hjh5466@GNIA-C201-H02:~$ sudo docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
```

- 운영
```












```









### Dockerfile 빌드/실행
- Dockerfile 빌드
```
hjh5466@GNIA-C201-H02:~/docker-practice$ sudo docker build -t my-first-image .
[+] Building 4.4s (5/5) FINISHED                                                                                                                                         docker:default
 => [internal] load build definition from Dockerfile                                                                                                                               0.0s
 => => transferring dockerfile: 96B                                                                                                                                                0.0s
 => [internal] load metadata for docker.io/library/ubuntu:22.04                                                                                                                    1.6s
 => [internal] load .dockerignore                                                                                                                                                  0.0s
 => => transferring context: 2B                                                                                                                                                    0.0s
 => [1/1] FROM docker.io/library/ubuntu:22.04@sha256:076e7bf82319619f28dd0aa9c02ab34b055ad37100395b4f49a2ffba04fb5e11                                                              2.1s
 => => resolve docker.io/library/ubuntu:22.04@sha256:076e7bf82319619f28dd0aa9c02ab34b055ad37100395b4f49a2ffba04fb5e11                                                              0.0s
 => => sha256:0626d3cc316c9fea3d4891e2ec19b8f371fe22ffb915622f6072a2ee2ca9017f 29.75MB / 29.75MB                                                                                   2.1s
 => exporting to image                                                                                                                                                             2.5s
 => => exporting layers                                                                                                                                                            0.0s
 => => exporting manifest sha256:d8432d5e552091dd1991bdf028271de65664764e92db35345c989f1a1a85dc8c                                                                                  0.0s
 => => exporting config sha256:417bad3962f226052c8761fa61fa92ba4d53e3938ae535c125bdd6f63933ea46                                                                                    0.0s
 => => exporting attestation manifest sha256:ac8d1cf340f4c223902d7400139bccc3b4c61bcbc39953df55cf6f1493313125                                                                      0.0s
 => => exporting manifest list sha256:3e4001839dc5e698d569c66258858ac5536d4ff44b84d9dd6b0c66b6640fe4a2                                                                             0.0s
 => => naming to docker.io/library/my-first-image:latest                                                                                                                           0.0s
 => => unpacking to docker.io/library/my-first-image:latest           
 ```
 