# Ubuntu Install & 환경설정 구축
ubuntu를 설치함과 동시에 ubuntu에서 설정한 환경설정 등을 정리해 올려본다.
=============================================================================
설치 과정 이슈
윈도우를 설치 한 후 우분투를 설치를 해야 안정적인 우분투 설치가 가능하다.
혹은 설치 과정에서 ubuntu GRUB(리눅스 부트로더)의 설치 드라이브 설정을 잘못해서 GRUB가  
ubuntu 설치를 해도 나타나지 않는 경우가 있다. 그때 경험한 이슈와 해결 경험을 적어본다.

또 ubuntu는 어떤 APP을 설치하기 전에도 ppa를 추가 한 다음에도 중간마다 update를 적용하면 좋다 

명령어는
```` 
sudo apt-get update
```
-----------------------------------------------------------------------------------------
- 부팅 중 부트로더가 나오지 않을때
    우선 부팅 후 ubuntu install 화면에서 'Ubuntu without install' 로 들어간다
    다음과 같은 명령어를 터미널 실행 후 'boot-repair'를 설치한다
```
$ sudo add-apt-repository ppa:yannubuntu/boot-repair
$ sudo apt-get update
$ sudo apt-get install -y boot-repair
```
