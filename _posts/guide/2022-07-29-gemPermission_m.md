---
title:  "Mac에서 Gem::FilePermissionError 해결 방법"
excerpt: "오류 해결 방법"

toc : true
toc_sticky : true

categories:
  - Error
tags: 
  - ruby 
  - gem
  - bundler
  - 오류해결
  
---

<br/>

Mac에서 오류 ruby를 설치하다보면 아래와 같이 Gem::FilePermissionError가 발생할 때가 있습니다.

    ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions for the /Library/Ruby/Gems/2.6.0 directory.

권한이 없어 gem 설치가 되지 않는다는 것인데 system이 ruby를 사용하고 있기 때문인데,

오늘은 rbenv를 사용해서 에러를 해결해보겠습니다.


### 1. 원인확인

아래 install 명령어를 통해 rbenv를 우선적으로 설치해줍니다.

    $ brew install rbenv



brew 명령어를 사용할 수 없다면 HomeBrew를 우선 적으로 설치해주세요.

[HomeBrew 설치하기](https://brew.sh/index_ko){:target="_blank"}


<img src="/assets/images/homebrew.jpg"><br/><br/>

설치를 완료한 이후 명령어를 통해 정상적으로 설치했는지 버전을 확인해줍니다.

    $ rbenv versions

<br/>
확인하면 아래와 같이 system에서 ruby를 사용하고 있다는 것을 알 수 있습니다.

    * system (set by /Users/dongChangKim/.rbenv/version)

<br/>
따라서 system이 아닌 rbenv에서 관리되는 ruby 버전을 벌도로 설치하면 되는데 아래 명령어를 통해 현재 설치 가능한 버전을 확인해줍니다.

    $ rbenv install -l

<br/>
나오는 버전 중 사용하실 버전을 선택하시면 되고, 저는 현재(2022.07.29)기준 최신 버전인 3.1.2 버전을 설치하도록 하겠습니다.

<br/>

### 2. ruby 설치하기

아래 명령어를 통해 최신버전의 ruby를 설치합니다.

    $ rbenv install 3.1.2

설치가 완료된 후 다시 한 번 위에서 사용했던 버전 확인 명령어를 통해 버전을 확인해 줍니다.

    * system (set by /Users/dongchangkim/.rbenv/version)
      3.1.2

<br/>
3.1.2 버전의 설치가 완료 되었지만 여전히 system이 선택되어 있습니다.
아래 명령어를 통해 대표 버전을 설치한 최신버전으로 변경해줍니다.

    $ rbenv global 3.1.2

<br/>
변경 하고 나면 3.1.2가 선택되어 있는 모습을 볼 수 있습니다.

<br/>

### 3. PATH 설정하기

쉘 설정 파일을 열어 다음의 코드를 추가합니다. bigsur 이상 버전을 사용하고 있으므로 저는 zsh를 사용하여 .zshrc에 추가하도록 하겠습니다.

    $ vim ~/.zshrc

<br/>
vim 에디터에서 i를 눌러 insert Mode에 진입하고 아래 두줄을 추가 해줍니다.

    export PATH="$HOME/.rbenv/bin:$PATH"
    eval "$(rbenv init -)"

<br/>
코드 추가 이후 esc를 눌러 normal 모드로 변경해 준 뒤 :wq 를 입력해서 저장 후 종료해줍니다.

|명령어|내용|
|-----|-----|
| :q|종료|
| :w|저장|
| :wq|저장 후 종료|
| :q!|저장하지 않고 종료|
| :wq!|강제로 저장하고 종료|

<br/>

PATH를 설정하고 업데이트 한 내용을 적용하기 위해 source 명령어를 사용하고 flutter 명령어로 버전을 확인합니다.

    $ source ~/.zshrc       //내용 적용
    $ flutter --version     //버전확인

<br/>
정상적으로 버전이 나타나고 설정이 됐다면 아래 코드로 bundler를 설치합니다.

    $ gem install bundler

<br/>
이 후 설치를 진행하다보면 뭐가 없다 뭘 해야한다 라고 나오는 경우가 있는데 시스템이 친절하게 
어떤 명령어를 입력하라고 알려주니 그대로 따라하시면 정상적으로 설치가 가능합니다.



