# ffmpeg_guide

## FFMPEG란?
동영상 재생, 녹화, 스트리밍과 변환을 위해 필요한 기능을 제공하는 멀티미디어 프레임워크.

컴파일해서 CLI로 사용할 수도 있고, C코드 라이브러리형태로 사용도 가능한듯?

## 설치
라이브러리 규모가 크고 의존성이 많아서 설치는 좀 골때린다. ㅡㅡ;

### OS
centos6에다가 설치하는데 nasm 2.13이 필요한데, centos6의 GLIBC가 낮아서 지원이 불가능하다.

GLIBC도 2.14이상이 필요한데 cecntos6의 GLIBC버전은 2.12다.

GLIBC 올리기가 조금 어려워보여(GLIBC에 의존하는 것들이 매우 많음) OS를 centos7로 다시 설치하였다.


### 기본 의존성 설치
필요한 의존성.

바로 설치때리지말고 밑에 읽고 하자.

아마 대부분 설치되어 있을 것이므로.
```bash
yum install git autoconf automake cmake gcc gcc-c++ libtool make nasm pkgconfig zlib-devel
```

대부분 기본적으로 설치되어 있으나 확인은 필요하다.

아래 명령으로 설치되어있는지 확인할 수 있다.
```bash
yum install 패키지명
```
나같은 경우에는 nasm만 없었다.

nasm을 install하려고보니 yum에 등록된 nasm버전이 낮아서 nasm yum 레포지토리를 별도로 등록해주었다.

/etc/yum.repos.d 디렉토리에 vi로 nasm.repo 파일을 만들고
http://www.nasm.us/nasm.repo 사이트에 있는 내용을 그대로 입력해주고 저장하면 된다.

### yasm 설치
x264는 yasm에 의존성이 있어서 설치해주어야 한다.
```bash
git clone --depth 1 git://github.com/yasm/yasm.git
cd yasm
./autogen.sh
./configure --prefix="/home/myuser/apps/ffmpeg" --bindir="/home/myuser/apps/ffmpeg/bin"
make
make install
```


