# Ubuntu Install & 환경설정 구축
## ubuntu를 설치함과 동시에 ubuntu에서 설정한 환경설정 등을 정리해 올려본다.

#### 설치 과정 이슈

윈도우를 설치 한 후 우분투를 설치를 해야 안정적인 우분투 설치가 가능하다.<br/>
혹은 설치 과정에서 ubuntu GRUB(리눅스 부트로더)의 설치 드라이브 설정을 잘못해서<br/>
GRUB가 ubuntu 설치를 해도 나타나지 않는 경우가 있다. 그때 경험한 이슈와 해결 경험을 적어본다.

또 ubuntu는 어떤 APP을 설치하기 전에도 ppa를 추가 한 다음에도 중간마다 update를 적용하면 좋다 

명령어는
```` 
sudo apt-get update
```
=================================================================================================-
### 부팅 중 부트로더가 나오지 않을때
우선 부팅 후 ubuntu install 화면에서 *'Ubuntu without install'* 로 들어간다<br/>
다음과 같은 명령어를 터미널 실행 후 'boot-repair'를 설치한다.<br/>
```
$ sudo add-apt-repository ppa:yannubuntu/boot-repair
$ sudo apt-get update
$ sudo apt-get install -y boot-repair
```

boot-repair를 실행
```
$ boot-repair
```

실행하면 아래와 같은 그림이 나온다.

![bootrepair1](http://img1.daumcdn.net/thumb/R1920x0/?fname=http%3A%2F%2Fcfile29.uf.tistory.com%2Fimage%2F1638D94150C2D69D2FE359)<br/>
![bootrepair2](http://img1.daumcdn.net/thumb/R1920x0/?fname=http%3A%2F%2Fcfile10.uf.tistory.com%2Fimage%2F0138D94150C2D69D306990)<br/>
위 사진에 'Recommended repair (repairs most frequent problems)'를 클릭후 yes 클릭.

![bootrepair3](http://img1.daumcdn.net/thumb/R1920x0/?fname=http%3A%2F%2Fcfile9.uf.tistory.com%2Fimage%2F0238D94150C2D69D31E258)<br/>

다음과 같이 ok를 클릭하면 재부팅때 GRUB가 나온다.

○ 참고 자료: http://deviantcj.tistory.com/493

----------------------------------------------------------------------------------------------

### low graphic 이슈가 발생했을 때
다음과 같이 GRUB에 ubuntu를 실행 했을때 다음과 같은 이슈가 발생했다.<br/>
![lowgraphic](http://simpledeveloper.com/wp-content/uploads/2014/02/system_running_in_low_graphics_mode.png)<br/>


처음 파악한 바로는 ubuntu와 내장된 그래픽 카드 드라이버와의 연결이 제대로 읽어지지 않은 발생 한 문제로 파악되었다.<br/> 
그래서 직접적으로 아래와 같이 그래픽카드 드라이버의 설치를 했다..... 하지만...<br/>

1. GRUB menu에 recovery mode<br/> 
![recovery mode1](http://i.stack.imgur.com/5kllk.png)

2. failsafeX를 클릭<br/>
![recovery mode2](http://i.stack.imgur.com/R5oV8.png)

3. 다음과 같은 창이 뜨면 *CTRL*+*ALT*+*F1*으로 server 계정에 접속(아이디와 비번 입력후 들어가기)<br/>
![recovery mode3](http://i.stack.imgur.com/eLE3j.png)

4. 본인의 경우 그래픽 카드를 *'nvidia'*를 사용하기 때문에 *'nvidia'*로 install 했다.<br/>
- nvidia 경우
```
sudo apt-get install nvidia-current
sudo apt-get install nvidia-current-updates
```

- AMD/ATI 경우
```
sudo apt-get install fglrx
```

*이슈는 해결되지 않았다..*<br/>
------------------------------------------------------------------------

그래서 다른 방법을 구글링으로 찾아보니 다음과 같은 해결 방책이 나왔다.
- gdm이 설치 되어 있다면        
```
$ sudo apt-get update
$ sudo apt-get -d install –-reinstall gdm
$ sudo apt-get install gdm
```
    
- gdm이 설치 되어 있지 않다면
```
$ sudo apt-get update
$ sudo apt-get remove –purge gdm
$ sudo apt-get install gdm
```
  
다음 reboot 실행.
```
$ sudo reboot
```

이후 정상작동 된것으로 보아 ubuntu내의 gdm에서 이슈가 발생하는 것으로 파악 된다.
                
○ 참고자료:<br/>
https://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error
http://simpledeveloper.com/system-running-in-low-graphics-mode/

====================================================================================================

## git
```
$ sudo apt-get update
$ sudo apt-get install git
```
-----------------------------------------------------------------------------------------------------


## terminator
개인적으로 사용하고 있는 터미널 tool이다 맥의 iterm과 비슷한 기능을 가지고 있어 사용하는데 유용하다.
```
$ sudo apt-get update
$ sudo apt-get install terminator
```
-----------------------------------------------------------------------------------------------------


## vim
```
$ sudo apt-get update
$ sudo apt-get install vim
```                         
  
아래처럼 .vimrc 파일을 생성한후 다음과 같이 설정했다.
```
$ vi ~/.vimrc
```                                 

```
set number  " line 표시를 해줍니다.
set shiftwidth=4    " shift를 4칸으로 ( >, >>, <, << 등의 명령어)
set tabstop=4   " tab을 4칸으로
set ignorecase  " 검색시 대소문자 구별하지않음
set hlsearch    " 검색시 하이라이트(색상 강조)
set expandtab   " tab 대신 띄어쓰기로
set nocompatible    " 방향키로 이동가능
set bs=indent,eol,start " backspace 키 사용 가능
set history=1000    " 명령어에 대한 히스토리를 1000개까지
set ruler   " 상태표시줄에 커서의 위치 표시
set nobackup    " 백업파일을 만들지 않음
set title       " 제목을 표시
set showmatch   " 매칭되는 괄호를 보여줌
set wmnu    " tab 자동완성시 가능한 목록을 보여줌

set nocompatible " 오리지날 VI와 호환하지 않음
set autoindent  " 자동 들여쓰기
set cindent " C 프로그래밍용 자동 들여쓰기
set smartindent " 스마트한 들여쓰기
set wrap 
set nowrapscan " 검색할 때 문서의 끝에서 처음으로 안돌아감
set nobackup " 백업 파일을 안만듬
set visualbell " 키를 잘못눌렀을 때 화면 프레시
set ruler " 화면 우측 하단에 현재 커서의 위치(줄,칸) 표시
set shiftwidth=4 " 자동 들여쓰기 4칸
set number " 행번호 표시, set nu 도 가능
set fencs=ucs-bom,utf-8,euc-kr.latin1 " 한글 파일은 euc-kr로, 유니코드는 유니코드로
set fileencoding=utf-8 " 파일저장인코딩 
set tenc=utf-8      " 터미널 인코딩
set hlsearch " 검색어 강조, set hls 도 가능
set lbr
set incsearch "  키워드 입력시 점진적 검색
filetype indent on "  파일 종류에 따른 구문강조
set background=dark " 하이라이팅 lihgt / dark
set backspace=eol,start,indent "  줄의 끝, 시작, 들여쓰기에서 백스페이스시 이전줄로
set history=1000 "  vi 편집기록 기억갯수 .viminfo에 기록

colorscheme default  "  vi 색상 테마 설정

"colo blue "글자색 blue
"colo default "글자색 기본값 
"colo desert "글자색 
"colo elflord "글자색 
"colo koehler "글자색 
"colo morning "글자색 
"colo peachpuff "글자색 
"colo shine "글자색 
"colo slate "글자색 
"colo torte "글자색 

syntax on   " 문법 하이라이트 킴"
```
-----------------------------------------------------------------------------------------------------

## zsh + oh my zsh
zsh 설치
```
$ sudo apt-get update && sudo apt-get install zsh
```

ZSH 기본값 설정(zsh 위치 확인 후 그 확인된 root로 기본값 설정)
```
which zsh 
chsh -s /usr/bin/zsh
```

oh-my-zsh 설치
```
wget –no-check-certificate https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O – | sh
```

THEME는 agnoster로 설정했다.
~/.zshrc 로 들어가 아래와 같이 설정한다.
```
ZSH_THEME = "agnoster"
```

Font가 깨진 zsh agnoster 테마가 나온다면 fonts를 받아 설치후 font를 ubuntu mono로 설정해준다.
```
git clone https://github.com/powerline/fonts.git

cd fonts
./install.sh
```

oh-my-zsh 설치후 
```
This is the Z Shell configuration function for new users,
zsh-newuser-install.
You are seeing this message because you have no zsh startup files
(the files .zshenv, .zprofile, .zshrc, .zlogin in the directory
~).  This function can help you with a few settings that should
make your use of the shell easier.

You can:

(q)  Quit and do nothing.  The function will be run again next time.

(0)  Exit, creating the file ~/.zshrc containing just a comment.
     That will prevent this function being run again.

(1)  Continue to the main menu.

(2)  Populate your ~/.zshrc with the configuration recommended
     by the system administrator and exit (you will need to edit
     the file by hand, if so desired).

--- Type one of the keys in parentheses --- 

```
다음과 같은 선택이 나온다 개인적으로 (2)을 누르고 다시 설정했다.

○ 참고자료:<br/>
https://gist.github.com/tsabat/1498393
http://crasy.tistory.com/146
https://monangik.wordpress.com/2011/04/21/install-zsh-shell-on-ubuntu/
http://seungdols.tistory.com/499
http://nolboo.kim/blog/2015/08/21/oh-my-zsh/

-----------------------------------------------------------------------------------------------------


## powerline
python 2.7 혹은 3.3 이상이 필요하다고 한다. 그래서 혹시나 설치해본다
```
$ sudo apt-get install python-pip git
```

- powerline 설치
```
$ sudo pip install git+git://github.com/Lokaltog/powerline
```

- font 설치
```
wget https://github.com/Lokaltog/powerline/raw/develop/font/PowerlineSymbols.otf https://github.com/Lokaltog/powerline/raw/develop/font/10-powerline-symbols.conf
sudo mv PowerlineSymbols.otf /usr/share/fonts/
sudo fc-cache -vf
sudo mv 10-powerline-symbols.conf /etc/fonts/conf.d/
```

- Bash confing 설정
```
if [ -f /usr/local/lib/python2.7/dist-packages/powerline/bindings/bash/powerline.sh ]; then
    source /usr/local/lib/python2.7/dist-packages/powerline/bindings/bash/powerline.sh
fi
```

- vim config 설정
```
set rtp+=/usr/local/lib/python2.7/dist-packages/powerline/bindings/vim/
" Always show statusline
set laststatus=2
" Use 256 colours (Use this setting only if your terminal supports 256 colours)
set t_Co=256
```

- 삭제시
```
$ sudo pip uninstall powerline
```
-----------------------------------------------------------------------------------------------------


## vundle + nurdtree
```

```
-----------------------------------------------------------------------------------------------------


## pyenv + virtualenv + autoenv
```

```
-----------------------------------------------------------------------------------------------------

                                        
## google chrome
```  
$ sudo add-apt repository
$ sudo apt-get update
$ sudo apt-get install google-chrome-stable
```
-----------------------------------------------------------------------------------------------------


## google drive          
```

```
-----------------------------------------------------------------------------------------------------

                                                   
                                                
## sublimetext3
```

```
-----------------------------------------------------------------------------------------------------

                                                       
##  slack
slack homepage에서 다운후 설치<br/>
- 다운로드: https://slack.com/downloads
-----------------------------------------------------------------------------------------------------


## GNOME
- GNOME은 ubuntu의 UI를 설정해주는 프로그램이다.<br/>
보다 자신에게 편한 ubuntu의 UI사용이나 변경을 원한다면 이용하는 것이 좋다.<br/>
#### GNOME Classic
```
$ sudo apt-get install gnome-session-flashback                                                        
$ sudo apt-get install docky
```
-----------------------------------------------------------------------------------------------------


##  bomi player
개인적으로 동영상 tool을 대부분 SMplayer로 추천하는데 개인적으로 난 bomi가 좀더 깔끔하고 이용하기 편했다.<br/>
아래 처럼 설치를 진행하면 되나 bomi의 update 오류가 발생했다는 점이 있다는 점을 알게 되었다.<br/>
```
$ sudo add-apt-repository ppa:darkin20/bomi
$ sudo apt-get -repository ppa:ubuntu-toolchain-r/test
$ sudo apt-get update
$ sudo apt-get install bomi
```

그래서 해결 점으로 다음 아래와 같은 방식으로 설치하면 문제가 임시적으로 해결된다고 한다..<br/>
(소식에 의하면 bomi의 개발자가 개발을 잠정중단했다고 한다...)
```
$ sudo add-apt-repository ppa:ubuntu-toolchain-r/test
$ sudo apt-get update
$ sudo apt-get install bomi
```
