# Ubuntu install tool & plug-in 
### ubuntu tool 및 plug-in 설치 기록

설치 된 plug-in과 tools를 기록한 것들...<br>
#### 초기 gnome 설치후 카이로독 설치 그 후 나머지 설치

--------------------------------------------------------------------------------------------------

## git
```
sudo apt-get update
sudo apt-get install git
```

-----------------------------------------------------------------------------------------------


## terminator
개인적으로 사용하고 있는 터미널 tool이다 맥의 iterm과 비슷한 기능을 가지고 있어 사용하는데 유용하다.
```
sudo apt-get update
sudo apt-get install terminator
```

-----------------------------------------------------------------------------------------------


## vim
```
sudo apt-get update
sudo apt-get install vim
```                         
  
아래처럼 .vimrc 파일을 생성한후 다음과 같이 설정했다.
```
vi ~/.vimrc
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

"set rtp+=~/.vim/bundle/vim-colors-solarized
syntax on   " 문법 하이라이트 킴"
"set background=dark
"colorscheme solarized

"Bundle 'sonph/onehalf', {'rtp': 'vim/'}
"set cursorline
"colorscheme onehalfdark
"let g:airline_theme='onehalfdark'
" lightline
" " let g:lightline.colorscheme='onehalfdark'

set autoindent  " 자동 들여쓰기
set number " 행번호 표시, set nu 도 가능
set shiftwidth=2 " 자동 들여쓰기 2칸
set tabstop=2 " 탭을 2칸으로

"YouCompleteMe 설정
let g:ycm_add_preview_to_completeopt=0
let g:ycm_confirm_extra_conf=0
set completeopt-=preview

set rtp+=/usr/local/lib/python2.7/dist-packages/powerline/bindings/vim/
" Always show statusline
set laststatus=2
" Use 256 colours (Use this setting only if your terminal supports 256 colours)
set t_Co=256

" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
" alternatively, pass a path where Vundle should install plugins
"call vundle#begin('~/some/path/here')

" Plugin 설치 목록들
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
" see :h vundle for more details or widi for FAQ
" Put your non-Plugin stuff after this line

Plugin 'The-NERD-Tree'
Plugin 'jelera/vim-javascript-syntax' "Javascript Syntax Highlight
Plugin 'pangloss/vim-javascript' "Javascript Indenting
Plugin 'nathanaelkane/vim-indent-guides' "Javascript Indenting
Plugin 'Raimondi/delimitMate' "Typing을 편리하게
Plugin 'maksimr/vim-jsbeautify'

```

- vim 컬러 스키마(jellybeans) 설치:
```
curl https://raw.githubusercontent.com/nanotech/jellybeans.vim/master/colors/jellybeans.vim > ~/.vim/colors/jellybeans.vim
```

-----------------------------------------------------------------------------------------------

## zsh + oh my zsh
- zsh 설치:
```
$ sudo apt-get update && sudo apt-get install zsh
```

- ZSH 기본값 설정(zsh 위치 확인 후 그 확인된 root로 기본값 설정 및 확인): 이방법이 안된다면 https://aweekj.github.io/2017-02-20/zsh/ 참조
```
chsh -s `which zsh`

echo $SHELL
```

- oh-my-zsh 설치:
```
$ curl -L https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh | sh
```

THEME는 agnoster로 설정했다.
~/.zshrc 로 들어가 아래와 같이 설정한다.
```
ZSH_THEME="agnoster"
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
https://nolboo.kim/blog/2015/08/21/oh-my-zsh/</br>
https://gist.github.com/tsabat/1498393</br>
http://crasy.tistory.com/146</br>
https://monangik.wordpress.com/2011/04/21/install-zsh-shell-on-ubuntu/</br>
http://seungdols.tistory.com/499</br>
http://nolboo.kim/blog/2015/08/21/oh-my-zsh/</br>

-----------------------------------------------------------------------------------------------

## powerline
python 2.7 혹은 3.3 이상이 필요하다고 한다. 그래서 혹시나 설치해본다
```
sudo apt-get install python-pip git
```

- powerline 설치:
```
sudo pip install git+git://github.com/Lokaltog/powerline
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
sudo pip uninstall powerline
```

○ 참고자료:</br>
http://askubuntu.com/questions/283908/how-can-i-install-and-use-powerline-plugin</br>
https://humb1ec0ding.github.io/2013/11/26/2013-11-26-ubuntu-powerline-beautify-the-stateline/</br>

-----------------------------------------------------------------------------------------------

## vundle + nurdtree
- 우선 설치전 git을 install 해야 한다.

#### Vundle 설치
- Set up Vundle
~/.vim/bundle/ 폴더 안에 소스를 복사하여 넣어주면 작업이 완료된다.
```
user$ git clone https://github.com/gmarik/Vundle.vim.git ~/.vim/bundle/Vundle.vim  
```

- Configure Plugins -> .vimrc 넣기 -> vim 들어간 후 :PluginInstall 엔터
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

--------------------------------------------------------------------------------------------------

#### NERDTree 설치

1. Search Plugins
'Vundle' 설치후 vi플러그인에 들어가 명령행 모드에 다음과 같이 실행한다.
```
:PluginSearch NERD
```

2. Add Plugin to ~/.vimrc
'.vimrc'에 다음과 같은 명령어로 추가한다.
```
echo "Plugin 'The-NERD-Tree'" >> ~/.vimrc  
```

3. Install Plugin
'vim'을 실행후 명령행 모드에서 ':PluginInstall'이라고 실행하면 된다.

○ 참고자료:</br>
https://dobest.io/install-vundle-and-nerdtree/</br> 
(개인적으로 이런 멋진 plug-in을 알려주신 갓수찬님께 감사를...)

-----------------------------------------------------------------------------------------------

## pyenv + virtualenv + autoenv
- 각각의 plugin은 Python 개발 효율성을 증대해주는 유용한 도구들이다 발췌한 요약 기능을 쓰자면

'pyenv' : "Simple Python Version Management", 로컬에 다양한 파이썬 버전을 설치하고 사용할 수 있도록 한다.</br> pyenv를 사용함으로써 파이썬 버전에 대한 의존성을 해결할 수 있다.</br>
'virtualenv' : “Virtual Python Environment builder”, 로컬에 다양한 파이썬 환경을 구축하고 사용할 수 있도록 한다.</br> 일반적으로 Python Packages라고 부르는 ( pip install을 통해서 설치하는 ) 패키지들에 대한 의존성을 해결할 수 있다.</br>
'autoenv' : 만약 pyenv와 virtualenv를 통해서 의존성을 해결한다고 하더라도 작업할때마다 설정해주는 것은 귀찮은 작업이다.</br> 특정 프로젝트 폴더로 들어가면 자동으로 개발 환경을 설정해주는 autoenv라는 스크립트를 활용하자.</br>

#### pyenv 설치 전 의존성 패키지를 미리 빌드해 놓는 것이 좋다.
- 설치전 의존성 패키지 설치</br>
[개발자 yyuu의 공통 빌드 prolblems: https://github.com/yyuu/pyenv/wiki/Common-build-problems]
```
sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev \
         libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils
```

#### 추가 문제..[pip install 이 안먹히는 문제 발생 2016.08.09]
python-pip를 설치를 하는 것으로 문제해결(둘 중 하나만 하면 됨)
- A 설치방법
```
sudo apt-get update
sudo apt-get -y install python-pip
```

- B 설치방법
```
curl "https://bootstrap.pypa.io/get-pip.py" -o "get-pip.py"
python get-pip.py
```

○ 참고자료:</br>
http://www.liquidweb.com/kb/how-to-install-pip-on-ubuntu-14-04-lts/</br>


--------------------------------------------------------------------------------------------------

#### pyenv 설치
[2016.08.10]zsh로 설치 했다면 끝에 install curl 끝에 **'bash'**가 아닌 **'zsh'**로 설치해야 한다.
- Install:
```
curl -L https://raw.githubusercontent.com/yyuu/pyenv-installer/master/bin/pyenv-installer | bash
```
설치가 성공적으로 되면 아래 문구에서 '.zshrc'(설치된게 아니면 '.bashrc')에 아래 내용을 넣는다.
```
export PATH="/home/feanar/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```


- Update:
```
pyenv update
```

- Uninstall: 
```
rm -fr ~/.pyenv
```

그리고 '.zshrc'(zsh이 설치되었다면) 그게 아니면 '.bashrc'에 아래 내용을 삭제한다.
```
export PATH="~/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```

----------------------------------------------------------------------------------------------------

#### virtualenv 설치
- Install:
```
git clone https://github.com/yyuu/pyenv-virtualenv.git ~/.pyenv/plugins/pyenv-virtualenv
```

- Add my shell(~/.zshenv 파일 대신에 ~/.bash_profile에 추가하는 것을 추천한다고 적혀있다. 개인적으로 난 .zshrc에 적용했다.):
```
echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bash_profile
```

- Restart your shell to enable pyenv-virtualenv:
```
exec "$SHELL"
```

----------------------------------------------------------------------------------------------------

#### autoenv 설치
- pip install:
```
pip install autoenv
echo "source `which activate.sh`" >> ~/.bash_profile
```

- git install:
```
git clone git://github.com/kennethreitz/autoenv.git ~/.autoenv
echo 'source ~/.autoenv/activate.sh' >> ~/.bash_profile
```

○ 참고자료:</br>
https://github.com/yyuu/pyenv</br>
https://github.com/yyuu/pyenv-virtualenv</br>
https://github.com/kennethreitz/autoenv</br>
https://dobest.io/how-to-set-python-dev-env/</br>
http://yujuwon.tistory.com/entry/pyenv-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0<br/>
http://blog.radup.net/38</br>
http://gyus.me/?p=475</br>

--------------------------------------------------------------------------------------------------

## google chrome
```  
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add - 

sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list'

sudo apt-get update
sudo apt-get install google-chrome-stable
```
○ 참고자료:</br>
http://askubuntu.com/questions/510056/how-to-install-google-chrome</br>

--------------------------------------------------------------------------------------------------

## google drive          
> 먼저 grive를 설치해 의존성에 맞게 해주어야 한다.
```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install grive
```

> 그 다음 grive-tools을 설치하면 된다.
```
sudo add-apt-repository ppa:thefanclub/grive-tools
sudo apt-get update
sudo apt-get install grive-tools
```

> 사용법
```
검색창에 'grive' 라고 검색하면 'grive setup'을 실행한다
( 참고로 google-drive indicator는 자동 동기화 기능을 가진 App이다. )
그다음 google drive와 grive의 동기화를 허용후 나타난 코드를 복사해 붙이고 동기화 시키면 
자동적으로 google drive 폴더가 생성되어 동기화가 진행되어 google-drive의 파일들이 나온다.
( 파일들이 많이 있다면 동기화 하는데 시간이 많이 걸린다..  )
```

○ 참고자료:</br>
https://www.thefanclub.co.za/how-to/ubuntu-google-drive-client-grive-and-grive-tools</br>
http://moordev.tistory.com/80</br>

--------------------------------------------------------------------------------------------------

## sublimetext3
```
sudo add-apt-repository ppa:webupd8team/sublime-text-3
sudo apt-get update
sudo apt-get install sublime-text-installer
```

○ 참고자료:</br>
http://askubuntu.com/questions/172698/how-do-i-install-sublime-text-2-3</br>
https://packagecontrol.io/installation</br>

--------------------------------------------------------------------------------------------------

## Pycharm 
- Install
```
sudo add-apt-repository ppa:mystic-mirage/pycharm
sudo apt-get update
sudo apt-get install pycharm
```

- Remove
```
# for community edtion
sudo apt-get remove pycharm-community

# for professional version
sudo apt-get remove pycharm
```

○ 참고자료:</br>
http://goodtogreate.tistory.com/entry/PyCharm%EC%9D%84-%EC%9A%B0%EB%B6%84%ED%88%AC-1404%EC%84%A4%EC%B9%98-%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95i</br>

--------------------------------------------------------------------------------------------------

## ATOM 
```
sudo add-apt-repository ppa:webupd8team/atom 
sudo apt-get update
sudo apt-get install atom
```

○ 참고자료:</br>
http://logon.tistory.com/392</br>

--------------------------------------------------------------------------------------------------

## slack
slack homepage에서 다운후 설치</br>
○ 다운로드: https://slack.com/downloads

--------------------------------------------------------------------------------------------------

## GNOME
- GNOME은 ubuntu의 UI를 설정해주는 프로그램이다.</br>
보다 자신에게 편한 ubuntu의 UI사용이나 변경을 원한다면 이용하는 것이 좋다.</br>
#### GNOME 
```
sudo add-apt-repository ppa:gnome3-team/gnome3-staging

sudo add-apt-repository ppa:gnome3-team/gnome3
```

```
sudo apt dist-upgrade
```

```
sudo apt install gnome gnome-shell
```


#### GNOME Classic
```
sudo apt-get install gnome-session-flashback
sudo apt-get install docky
```

#### Numix Theme
```
sudo add-apt-repository ppa:numix/ppa
sudo apt-get update
sudo apt-get install numix-gtk-theme numix-icon-theme numix-icon-theme-circle
```

#### Cairo-Dock
- Cairo-Dock은 좌측에 있는 상태표시줄을 하단으로 옮겨 맥같이 사용하게 해주는 UI 프로그램이다.
```
sudo apt-get update
sudo apt-get install cairo-dock
```

#### unity-tweak-tool
- ubuntu 런처 및 테마 기본 폰트 설정등을 GUI 환경에서 쉽게 변경하게 해주는 프로그램이다.</br>
현재는 개발 중단으로 인해 우분투 16.04 버전에서는 사용할 수 없고 별도의 프로그램을 설치해야 하는데 이 블로그에 설명이 나온다. *http://logon.tistory.com/349*
```
sudo apt-get install unity-tweak-tool
```

○ 참고자료:</br>
http://logon.tistory.com/392</br>
http://logon.tistory.com/349</br>

--------------------------------------------------------------------------------------------------
 
## bomi player
동영상 tool을 대부분 SMplayer로 추천하는데 개인적으로 bomi가 좀더 깔끔하고 이용하기 편했다.</br>
아래 처럼 설치를 진행하면 되나 bomi의 update 오류가 발생했다는 점이 있다는 점을 알게 되었다.</br>
```
sudo add-apt-repository ppa:darklin20/bomi
sudo apt-get update
sudo apt-get install bomi
```

그래서 해결 점으로 다음 아래와 같은 방식으로 설치하면 문제가 임시적으로 해결된다고 한다..<br/>
(소식에 의하면 bomi의 개발자가 개발을 잠정중단했다고 한다...)
```
sudo add-apt-repository ppa:ubuntu-toolchain-r/test
sudo apt-get update
sudo apt-get install bomi
```

○ 참고자료:</br>
http://logon.tistory.com/283</br>

