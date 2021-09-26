# linux_study
인프런 강의를 보며 매일 리눅스를 공부해보자
![짱구222](https://user-images.githubusercontent.com/86240112/133720977-8f3c507c-634e-4d3b-ac39-8c1e2de829c8.png)

----

# 아아아아아아아아

리눅스 배포판 : 우분투
shell 로 접근해서 리눅스 시스템을 이용할 수 있다.
터미널을 통한 쉘의 사용.
![image](https://user-images.githubusercontent.com/86240112/134801585-63b41155-3c4a-4525-94e8-8baee2f3131a.png)

터미널을 띄우면 리눅스 쉘 (Bash)를 사용하고 있다. 라고 생각하면 된다. 쉘에 종류는 많고 리눅스에서 기본적인 쉘은 Bash 이다.
텔넷이 아닌 ssh를 이용하여 클라우드에 있는 리눅스의 쉘을 내 로컬쪽에 띄운다. (원격지에있는 쉘) 그리고 컨트롤하면된다.

root@server-a:~$  : root : 로그인한 사용자 계정명, @ : 계정명과 호스트네임을 구별하기 위한 구분자, Server-A : 호스트네임
~ : 현재 작업 위치 ,  # <-- root 계정 , $ : 일반사용자 계정 ( 프롬프트 를 표시하는거임 ) 프롬프트란, 텍스트 기반의 환경에서, 각종 명령어를 입력하는 곳

~ : '킬데' 인 이것은 현재 사용자의 홈디렉토리라는 표시. 리눅스는 기본적으로 여러 사용자가 리눅스 시스템에 사용자로서 등록이 되고
사용할수 있기 때문에. 조금 더 직관적으로 하면   /home 이 기본 경로고 abc라는 계정을 만드면 기본 홈 디렉토리는 /home/abc 이다. 배포판 마다 다르지만 우분투는 그렇다 !

- https://explainshell.com/ <--- 명령어 찾기 좋은 홈페이지
ls | grep abc : like %abc% 디렉토리에 있는 모든 파일 찾는 명령어 
history | grep redis : 실행했던 명령어 리스트 
ps -ef | grep java : 현재 실행중인 프로세스


파일 목록/ 내용 조회 관련 명령어 : ls, cat, head, tail
검색/탐색 관련 명령어 : grep, find
압축/해제 관련 명령어 : tar, gzip/gunzip, zip/unzip
시간 관련 명령어 : date, cal
기타 명령어 : echo, exit, history
관리자 권한 실행 : sudo
패키지 매니저 : apt
텍스트 에디터 : nano

명령어를 배워보자! 

man : 메뉴얼의 약자 man!
/ <- 슬러시를 치고 찾고자하는 단어를 누르면 찾을수있다. /abc  -> abc쪽 C + F 와 같은 개념임!
cp : 파일 카피하는 !

리눅스도 파일들이 트리처럼 되어있다. 
디렉토리 -> 파일여러개 또 그 안에 디렉토리! 그안에 또 파일 등등...

윈도우와 같지만 다른 점은 윈도우는 C Drive , D Drive가 있고 거기서 트리가 있지만
리눅스는 디스크 드라이브가 여러개라 하더라고 Root 라는 디렉토리 하나!!! 에서 모든 디렉토리와 파일들이 시작된다.

디렉토리 == 폴더 

ls : 디렉토리를 보여주는 명령어
cd ( change Directory ) : 현재의 디렉토리에서 다른 디렉토리에 갈 때!
cd .. : 뒤의 경로로 가는 !
pwd : 현재 내가 어디에있는 지 ! 

pwd 치면  /home/test 가 나온다. 해석해보자  / ( root )   /home ( root 에 home 디렉토리)   /home/test ( root에 home 디렉토리에 test 디렉토리)

즉슨, test 라는 계정이 쉘을 실행할때는 home 디렉토리가 ~로 표시하겠다 이 ~표시는 !! /home/test 경로랑 같다. 누군가의 홈 디렉토리다!
( 오렵다.... )

cd - : 직전에 있었던 곳에 가는 것! 
그럼 여기서 또 cd - : 하면 또 다시 돌아가는거임.  cd .. 와 다른점임!

ls -al : 모든 파일을 전부 보여준다. 파일의 이름뿐아니라 여러가쥐!!!


# 파일 내용 조회

cat : 이 명령어를 이용해서 파일의 처음부터 끝까지 화면에다가 뿌려준다. 
( ex : cat abc.txt )

head : 처음부터 어느정도만 ! 일부
tail : 문서상에 가장 끝에 보여주는 ! 일부

head dpkg.log
tail dpkg.log

cd /var/log : 로그파일이 들어있쥐.. 저장하는 메세쥐죠. 물론 다른곳에 있지만 일반적으로 여기에 저장된다.
dpkq 파일을 찾고 싶은데 dp 만 치고 tap 눌러도된다 즉슨, cat dp 하고 Tap !!!!


만약 head 에 대한 더 필요로 한다면 
man head 하면 됨.

# 파일 내용 검색

grep은 입력으로 전달된 파일(또는 그냥 파일)의 내용에서 특정 문자열을 찾고자할 때 사용하는 명령어
grep : 파일 내용중에 원하는 부분을 검색해서 찾겠다!
dpkg.log 의 내용을 알고싶다.
tail dpkg.log 로 해서 밑에 부분만 보여줄 수 있고 !

grep --help , man grep 으로 볼수도 있다.
grep "찾을 내용" <- 이렇게 따옴표를 넣는게 좋다.
grep "hello" dpkg.log  
만약 아무것도 안나오면 내용에 hello 가 없는것 


ls -al 에서 kern.log 를 검색하고싶어! ( 화면에 출력되는 명령어 를 쓰면서! )
ls -al | grep kern.log : 현재 디렉토리에서 ls -al 한 결과! 화면에 나올텐데 파이프를 통해서 
다음 명렬중에 보내줘! 즉, 앞에 있는 실행 결과를 뒤에 있는 명령어에 보내준다 이런 뜻이야. )

여기서 우리가 했던게 grep "abc" abefwf.log ( abefwf.log 라고 파일을 지정해줬는데 이렇게 파이프라인을 쓰면 지정안해줘도돼!
왜!? 앞에서 그 출력된게 임시 파일이라고 생각하면 되니까! )

여기서 | 가 파이프라인 이라고한다

그러면 dpkg.log | head 라고 해도되고  dpkg.log | tail 로 해도 된다 이고지. O.K!?

cat dpkg.log | grep "2021" ( dpkg.log를 전부 출력해 근데 2021이 있 는것만 출력해 ! )

# 파일 검색

find --help
이렇게 사용법을 찾을때 대괄호 ( [] ) 가 있을 텐데 이건 ! 생략이 가능하다는 뜻이다!

find 명령어는 현재 디렉토리의 하위 디렉토리까지 전부! 찾는 명령어다 ( 자기자신도 포함 )
즉슨, root 디렉토리에서 find하면!! 전체 모두! 에서 찾는거겠죵

여러가지 설정파일들이 /etc 밑에 있는 경우가 많다.

find /etc -print 
find /etc -name "conf" -print  - 이렇게 하면 허가 거부가 뜰 가능성이 있다. !
이유는 ... : test라는 계정이 권한이 없다는 것임.

find /etc -name "*.conf" -print

. : 현재 디렉토리
.. : 상위 디렉토리

같은 단계에서 다른 디렉토리로 가려면  $ ../abc : 나의 상위 디렉토리에서의 abc 디렉토리 

find | grep "conf" 
: find하고 모든 파일들이 나오는데 그러고 나서 grep "conf" 쳐서 conf가 들어간 파일을 찾아라 ! 이뜻임

find | grep "conf" 와 find -name "*.conf" -print 와 는 다르다 
1번 실행 2번실행


# 압축 관련 커맨드

이 압축 관련 커맨드는 압축을 리눅스에서 어떻게 풀지 - .zip 파일 , .gz 파일, .tar.bz  파일, tar.gz 파일 등
find > filelist

' > ' : 왼쪽에 나온 명령어를 오른쪽 파일에 넣어라!

하나의 파일을 압축해보자 ! 보통 gzip을 쓴다
gzip filelist 
하고 나서 ls 해보면 filelist.gz 이라는 것이 생겼을 것 !
file filelist.gz 이렇게 해서 정보를 얻을수 있따.

gunzip filelist.gz 
을 주면 원래의 파일로 돌아온다 ! 즉 압축이 풀어진다. 

리눅스는 원래 확장자라는 의미가 없다 !


mv : 파일명을 바꾼다 
mv filelist.gz test
파일이름을 바꿧다. test로 ! 

여기서 file test 하면 똑같이 파일정보가 나온다. 즉슨, 확장자가 따로 없다 얘기다 !

tar.gz 같은 경우는 tar로 여러파일들을 묶고 그리고 gz으로 한번 묶는다! 라는 느낌

tar --help

tar -czf test.tar.gz filelist.gz snap/ 사진 


mkdir testdir
cd testdir
tar -zxf ../test.tar.gz 


# 시간 및 기타 커맨드

date 라고 명령어 쳐보면 시간이 나온다
ssh 해서 서버 그쪽의 쉘을 띄운다. 그럴때 그 시간의 리눅스 쉘 시간이 나온다.
시간을 확인해야할일이 종종 생기기에 이 시간 명령어를 공부할 필요가 있다.

date --help
date +%Y   : 2021  이렇게 년도만나오게 된다
date +%y   : 21    이렇게 두자리만 나오게 된다
cal 2021   : 달력 이 나옴


history 를 치면 그동안의 했던 명령어들이 쭉 나온다.
!! 하면 최근에 했던 명령어가 실행 된다. 

exit 를 쓰면 쉘이 끝나는 것이다. 즉 터미널이 꺼짐. exit 는 쉘!이 끝나는거다. 이 터미널이 쉘을 실행하다보니 터미널이꺼지는것 !

hash 를 하면 또 쉘하나가 켜진다.


echo : 메아리처럼 화면상에 보여주는거다. 이게 무슨 쓸모냐 ? Bash에 변수가 있다. 변수를 만들어서 이게 1 또는 0을 가질수도 있고 여러 자료를 담고 있을 수 있다.  

echo hhhhhhh 하면 hhhhhh 가 뜬다.
echo $PWD : PWD 라는 변수의 값을 출력해 !  -> /home/test 가 뜰거임
env : 를 하면 어떠한 변수가 있는지 전부 출력된다.

자자 실습

which ls : ls가 어디에있느냐 하면 /usr/bin/ls 가 나옴
file /user/bin/ls : 이게 무엇인지 나옴


# 관리자 권한 실행

리눅스에는 root 라는 관리자 계정이 숨어있다.
반드시 존재하는 계정이다.

윈도우즈에서도 admin이라고 있다. 리눅스는 똑같이 root 라는 계정이 있다.

/home/{id} : 사용자 계정
이 사용자계정은 root 계정하고 좀 다르다. ! 권한이 다르다! 

뭔가 할 수 있는 계정과 할수 없는 계정이 이있다.

관리자 계정은 시스템의 모든 설정을 바꿀 수 있다.
사용자 계정은 이 딱 자기쪽만 바꿀수 있다.

무언가 설치를 한다고 했을 때, 기본적으로는 관리자 계정에서만 할 수 있다.

이제 여기서 sudo 커맨드가 나온다.
switch user do 라는 의미이다. 내가 실행을 하지만! 다른 계정으로 하는 것처럼 실행한다는 뜻이다.
이게 보통 사용자 계정이 아닌 관리자 계정으로 무언가를 할때 쓰는 것!!

sudo apt-get install 이런식으로 !

# 패키지 매니저 사용법 (apt, yum)

예를들면 hello를 삭제, 조회, 삭제 등등 

사람 -> Pkg Mg -> Repository 

sudo apt install hello

만약에 지난번에 hello가 과거버전이고 repository에 새로운 버전이있따고 하면!
sudo apt install hello 하면 다시 삭제하고 다시 install 이된다.
sudo api rmove hello : 삭제!

apt list : 어마어마하게 많은 패키지들이 나열된다.

apt list | grep hello : hello 가 포함된 패키지를 찾을 수 있음.
apt list --help 
man apt 하고 나서 찾아보면돼
apt list --installed : 설치된 것 확인


# 나노(nano) 편집기 사용법

쉘에서의 편집기 기능! 우분투에 nano 라고 있다.
nano : vim보다는 굉장히 간단

nano
nano test


# 사용자와 그룹

A사용자, B사용자

A사용자의 데이터를 B사용자에게 보호를 해야한다.

사용자 : User
그룹 : group

여기서 이제 권한이 나오는거쥐..

생각해보자 하나의 공간이 있고 여기에 왕은 root 야! system administrator !

그리고 그 안에 이제 그룹 A가 있고 B가 있고 user a/b/c 등등이 있어  a,b 는 group a 일수있고 group b에는 c가 들어일수있어
그리고 한명이 여러개의 계정을 갖고 있을 수 있어!! 나도 뭐 구글 여러개 갖고 있으니까 !

그래서 사용자 1명! 이라기보다는 user를 계정 1개라고 생각하는게 좋아. 즉 userA , userB가 한명의 사람이 할수도있어
root 같은 경우도 사람 1명이 아니야!

# 파일의 소유권과 권한

File 은 권한, 소유권이 있다.

파일이 있고 ls -l 하면 파일에 대한 상세정보가 나온다. Owner, Group ! 순!
Permissions : drwxr-xr-x 와같은거! 이걸 mod , mode 라고도해


File은 소유권으로 부터 시작한다! 누구의 소유권이냐! 그룹과 User !
어떤 그룹의 것 - 이게 되게 이해하기 어려울 수 있다 !!
A조에 해당하는 사람이 있을 수 있고 B조에 있을수도있고!

이 조원들끼리는 공유해야하는 파일이 있다
하나의 결과물을 만들어야하는 경우!?

즉슨, A조의 모든 조원들이 모두 이 파일을 쉐어할수 있어야한다! 
그래서 어떤 파일이냐 디렉토리 ( 파일이나 디렉토리나 뭐.. 같다 )

mode 부분에  rwx rwx rwx  : 순서대로 Owner, Group, Other Users  임!!
r : Read , W : Write , X : Execute 
x같은 경우 텍스트파일보다 쉘스크립트 파일등과 같은 실행가능한 유형의 파일타입


맨앞에 파일 타입   -  , d 가 있음 !!

여기서 꿀팁은 보통 텍스트파일같은 경우 실행할수 있는 파일이 아니기에 보통 owner 같은 권한에서도 rw- 처럼 된다.


# 파일 권한 설정

chmod ( change mode )
permission == mode 라고도 한다

chomod 라는 툴이다

표현 방법 : 의미표현 , 8진표기법
의미표현 chmod go+rx ( + 권한을 넣는다, - 권한을 뺀다)
8진표현  chmod 755


















































































































