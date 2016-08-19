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

이후 정상작동 된것으로 보아 ubuntu내의 gdm에서 이슈가 발생하는 것으로 파악 된다.</br>

참고로 업데이트는 하지 말고 *추가 드라이버를 다시 열면 드라이버가 나온다.*</br>
시스템 업데이트를 먼저 하면 X.Org X server로 설치하기 때문에 아래 사진처럼 nvidia driver로 설정해 준다</br>
![Nvidia Graphic](http://img1.daumcdn.net/thumb/R1920x0/?fname=http%3A%2F%2Fcfile1.uf.tistory.com%2Fimage%2F25596135551EA0CC114785)

○ 참고자료:<br/>
https://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error</br>
http://simpledeveloper.com/system-running-in-low-graphics-mode/</br>

====================================================================================================

### fctix 한영키 적용(16.04)
[fctix][hangul]
[hangul]: http://lofty87.tistory.com/3

### install plug-in 기록
[install_plug-in][plugin]
[plugin]: https://github.com/feanar729/ubuntu/blob/master/ubuntu_14.04/install_plug-in.md
