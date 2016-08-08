# Ubuntu install tool & plug-in 
### ubuntu tool 및 plug-in 설치 기록

설치 된 plug-in과 tools를 기록한 것들...

--------------------------------------------------------------------------------------------------


## git
```
$ sudo apt-get update
$ sudo apt-get install git
```

--------------------------------------------------------------------------------------------------


## terminator
개인적으로 사용하고 있는 터미널 tool이다 맥의 iterm과 비슷한 기능을 가지고 있어 사용하는데 유용하다.
```
$ sudo apt-get update
$ sudo apt-get install terminator
```

--------------------------------------------------------------------------------------------------


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
set cindent " C 프로그래밍용 자동 들여쓰기
set autoindent " 자동 들여쓰기
set smartindent " 스마트한 들여쓰기
set ignorecase  " 검색시 대소문자 구별하지않음
set hlsearch    " 검색시 하이라이트(색상 강조)
set expandtab   " tab 대신 띄어쓰기로

set bs=indent,eol,start " backspace 키 사용 가능
set history=1000    " 명령어에 대한 히스토리를 1000개까지
set ruler   " 상태표시줄에 커서의 위치 표시
set nobackup    " 백업파일을 만들지 않음
set title       " 제목을 표시

set showmatch   " 매칭되는 괄호를 보여줌
set wmnu    " tab 자동완성시 가능한 목록을 보여줌
set nocompatible " 오리지날 VI와 호환하지 않음
set wrap 
set nowrapscan " 검색할 때 문서의 끝에서 처음으로 안돌아감

set visualbell " 키를 잘못눌렀을 때 화면 프레시
set ruler " 화면 우측 하단에 현재 커서의 위치(줄,칸) 표시
set fencs=ucs-bom,utf-8,euc-kr.latin1 " 한글 파일은 euc-kr로, 유니코드는 유니코드로
set fileencoding=utf-8 " 파일저장인코딩 
set tenc=utf-8      " 터미널 인코딩

set hlsearch " 검색어 강조, set hls 도 가능
set lbr
set incsearch " 키워드 입력시 점진적 검색
set background=dark " 하이라이팅 lihgt / dark
set backspace=eol,start,indent " 줄의 끝, 시작, 들여쓰기에서 백스페이스시 이전줄로
set history=1000 " vi 편집기록 기억갯수 .viminfo에 기록
filetype indent on " 파일 종류에 따른 구문강조

"colorscheme default  "  vi 색상 테마 설정
colorscheme jellybeans " vi 색상 테마
"colorscheme blue "vi 색상 blue
"colorscheme desert "vi 색상
"colorscheme elflord "vi 색상
"colorscheme koehler "vi 색상
"colorscheme morning "vi 색상
"colorscheme peachpuff "vi 색상
"colorscheme shine "vi 색상
"colorscheme slate "vi 색상
"colorscheme torte "vi 색상

set autoindent  " 자동 들여쓰기
set number " 행번호 표시, set nu 도 가능
set shiftwidth=4 " 자동 들여쓰기 4칸
set tabstop=4 " 탭을 4칸으로

syntax on   " 문법 하이라이트 킴"
```

- vim 컬러 스키마(jellybeans) 설치:
```
$ curl https://raw.githubusercontent.com/nanotech/jellybeans.vim/master/colors/jellybeans.vim > ~/.vim/colors/jellybeans.vim
```

--------------------------------------------------------------------------------------------------


## zsh + oh my zsh
- zsh 설치:
```
$ sudo apt-get update && sudo apt-get install zsh
```

- ZSH 기본값 설정(zsh 위치 확인 후 그 확인된 root로 기본값 설정):
```
which zsh 
chsh -s /usr/bin/zsh
```

- oh-my-zsh 설치:
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

○ 참고자료:</br>
https://gist.github.com/tsabat/1498393</br>
http://crasy.tistory.com/146</br>
https://monangik.wordpress.com/2011/04/21/install-zsh-shell-on-ubuntu/</br>
http://seungdols.tistory.com/499</br>
http://nolboo.kim/blog/2015/08/21/oh-my-zsh/</br>

--------------------------------------------------------------------------------------------------


## powerline
python 2.7 혹은 3.3 이상이 필요하다고 한다. 그래서 혹시나 설치해본다
```
$ sudo apt-get install python-pip git
```

- powerline 설치:
```
$ sudo pip install git+git://github.com/Lokaltog/powerline
```

- font 설치:
```
wget https://github.com/Lokaltog/powerline/raw/develop/font/PowerlineSymbols.otf https://github.com/Lokaltog/powerline/raw/develop/font/10-powerline-symbols.conf
sudo mv PowerlineSymbols.otf /usr/share/fonts/
sudo fc-cache -vf
sudo mv 10-powerline-symbols.conf /etc/fonts/conf.d/
```

- Bash confing 설정:
```
if [ -f /usr/local/lib/python2.7/dist-packages/powerline/bindings/bash/powerline.sh ]; then
    source /usr/local/lib/python2.7/dist-packages/powerline/bindings/bash/powerline.sh
fi
```

- vim config 설정:
```
set rtp+=/usr/local/lib/python2.7/dist-packages/powerline/bindings/vim/
" Always show statusline
set laststatus=2
" Use 256 colours (Use this setting only if your terminal supports 256 colours)
set t_Co=256
```

- 삭제시:
```
$ sudo pip uninstall powerline
```

○ 참고자료:</br>
http://askubuntu.com/questions/283908/how-can-i-install-and-use-powerline-plugin</br>
https://humb1ec0ding.github.io/2013/11/26/2013-11-26-ubuntu-powerline-beautify-the-stateline/</br>

--------------------------------------------------------------------------------------------------


## vundle + nurdtree
- 우선 설치전 git을 install 해야 한다.

#### Vundle 설치
1. Set up Vundle:
~/.vim/bundle/ 폴더 안에 소스를 복사하여 넣어주면 작업이 완료된다.
```
user$ git clone https://github.com/gmarik/Vundle.vim.git ~/.vim/bundle/Vundle.vim  
```

2. Configure Plugins:
```
" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
" alternatively, pass a path where Vundle should install plugins
"call vundle#begin('~/some/path/here')

" let Vundle manage Vundle, required
Plugin 'gmarik/Vundle.vim'

" The following are examples of different formats supported.
" Keep Plugin commands between vundle#begin/end.
" plugin on GitHub repo
Plugin 'tpope/vim-fugitive'
" plugin from http://vim-scripts.org/vim/scripts.html
Plugin 'L9'
" Git plugin not hosted on GitHub
Plugin 'git://git.wincent.com/command-t.git'
" git repos on your local machine (i.e. when working on your own plugin)
Plugin 'file:///home/gmarik/path/to/plugin'
" The sparkup vim script is in a subdirectory of this repo called vim.
" Pass the path to set the runtimepath properly.
Plugin 'rstacruz/sparkup', {'rtp': 'vim/'}
" Avoid a name conflict with L9
Plugin 'user/L9', {'name': 'newL9'}

" All of your Plugins must be added before the following line
call vundle#end()            " required
filetype plugin indent on    " required
" To ignore plugin indent changes, instead use:
"filetype plugin on
"
" Brief help
" :PluginList       - lists configured plugins
" :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate
" :PluginSearch foo - searches for foo; append `!` to refresh local cache
" :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal
"
" see :h vundle for more details or wiki for FAQ
" Put your non-Plugin stuff after this line
```

#### NERDTree 설치
1. Search Plugins:
'Vundle' 설치후 vi플러그인에 들어가 명령행 모드에 다음과 같이 실행한다.
```
:PluginSearch NERD
```

2. Add Plugin to ~/.vimrc:
'.vimrc'에 다음과 같은 명령어로 추가한다.
```
user$ echo "Plugin 'The-NERD-Tree'" >> ~/.vimrc  
```

3. Install Plugin:
'vim'을 실행후 명령행 모드에서 ':PluginInstall'이라고 실행하면 된다.

○ 참고자료:</br>
https://dobest.io/install-vundle-and-nerdtree/</br> 
(개인적으로 이런 멋진 plug-in을 알려주신 갓수찬님께 감사를...)

--------------------------------------------------------------------------------------------------

## pyenv + virtualenv + autoenv
- 각각의 plugin은 Python 개발 효율성을 증대해주는 유용한 도구들이다 발췌한 요약 기능을 쓰자면

'pyenv' : "Simple Python Version Management", 로컬에 다양한 파이썬 버전을 설치하고 사용할 수 있도록 한다.</br> pyenv를 사용함으로써 파이썬 버전에 대한 의존성을 해결할 수 있다.</br>
'virtualenv' : “Virtual Python Environment builder”, 로컬에 다양한 파이썬 환경을 구축하고 사용할 수 있도록 한다.</br> 일반적으로 Python Packages라고 부르는 ( pip install을 통해서 설치하는 ) 패키지들에 대한 의존성을 해결할 수 있다.</br>
'autoenv' : 만약 pyenv와 virtualenv를 통해서 의존성을 해결한다고 하더라도 작업할때마다 설정해주는 것은 귀찮은 작업이다.</br> 특정 프로젝트 폴더로 들어가면 자동으로 개발 환경을 설정해주는 autoenv라는 스크립트를 활용하자.</br>

#### pyenv 설치 전 python files을 사용하기 위해 사전에 python을 미리 설치를 하는 것이 좋다.
- Python 2.7 dependency 설치
```
sudo apt-get build-dep python2.7
```

- Python 3.5
```
curl -O "https://www.python.org/ftp/python/3.5.1/Python-3.5.1.tgz"
sudo apt-get install zlibc zlib1g zlib1g-dev libreadline6-dev libreadline6 libssl-dev libsqlite3-dev
```

- python 3.5 다운 후 설치
```
tar -xzvf Python-3.5.1.tgz
cd Python-3.5.1
./configure
make
make install
```

========================================================================
#### pyenv 설치
- Install:
```
$ curl -L https://raw.githubusercontent.com/yyuu/pyenv-installer/master/bin/pyenv-installer | bash
```

- Update:
```
$ pyenv update
```

- Uninstall: 
```
$ rm -fr ~/.pyenv
```

그리고 '.zshrc'(zsh이 설치되었다면) 그게 아니면 '.bashrc'에 아래 내용을 삭제한다.
```
export PATH="~/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```

========================================================================
#### virtualenv 설치
1. Install:
```
$ git clone https://github.com/yyuu/pyenv-virtualenv.git ~/.pyenv/plugins/pyenv-virtualenv
```

2. Add my shell(~/.zshenv 파일 대신에 ~/.bash_profile에 추가하는 것을 추천한다고 적혀있다.):
```
$ echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bash_profile
```

3. Restart your shell to enable pyenv-virtualenv:
```
$ exec "$SHELL"
```

========================================================================
#### autoenv 설치
- pip install:
```
$ pip install autoenv
$ echo "source `which activate.sh`" >> ~/.bashrc
```

- git install:
```
$ git clone git://github.com/kennethreitz/autoenv.git ~/.autoenv
$ echo 'source ~/.autoenv/activate.sh' >> ~/.bashrc
```

○ 참고자료:</br>
https://github.com/yyuu/pyenv</br>
https://github.com/yyuu/pyenv-virtualenv</br>
https://github.com/kennethreitz/autoenv</br>
https://dobest.io/how-to-set-python-dev-env/</br>
http://yujuwon.tistory.com/entry/pyenv-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0<br/>
http://blog.radup.net/38</br>

--------------------------------------------------------------------------------------------------
                                        
## google chrome
```  
$ sudo add-apt repository
$ sudo apt-get update
$ sudo apt-get install google-chrome-stable
```
○ 참고자료:</br>

--------------------------------------------------------------------------------------------------


## google drive          
```

```
○ 참고자료:</br>


--------------------------------------------------------------------------------------------------

                                                
## sublimetext3
```

```
○ 참고자료:</br>

--------------------------------------------------------------------------------------------------
 
##  slack
slack homepage에서 다운후 설치</br>
○ 다운로드: https://slack.com/downloads

--------------------------------------------------------------------------------------------------
 

## GNOME
- GNOME은 ubuntu의 UI를 설정해주는 프로그램이다.</br>
보다 자신에게 편한 ubuntu의 UI사용이나 변경을 원한다면 이용하는 것이 좋다.</br>
#### GNOME Classic
```
$ sudo apt-get install gnome-session-flashback
$ sudo apt-get install docky
```
○ 참고자료:</br>

--------------------------------------------------------------------------------------------------
 

##  bomi player
동영상 tool을 대부분 SMplayer로 추천하는데 개인적으로 bomi가 좀더 깔끔하고 이용하기 편했다.</br>
아래 처럼 설치를 진행하면 되나 bomi의 update 오류가 발생했다는 점이 있다는 점을 알게 되었다.</br>
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

○ 참고자료:</br>
http://logon.tistory.com/283</br>

