---
title:  "Mac에서 Gem::FilePermissionError 해결 방법"
excerpt: "오류 해결 방법"

categories:
  - Error
tags: 
  - ruby 
  - gem
  - bundler
  - 오류해결
  
---

<br/>

Mac에서 오류 ruby를 설치하다보면 아래와 같이 Gem::FilePermissionError가 발생할 때가 있다.

    ERROR:  While executing gem ... (Gem::FilePermissionError)
    You don't have write permissions for the /Library/Ruby/Gems/2.6.0 directory.

권한이 없어 gem 설치가 되지 않는다는 것인데 system이 ruby를 사용하고 있기 때문이다.

오늘은 rbenv를 사용해서 에러를 해결해보겠습니다.


### 1. 원인확인

아래 install 명령어를 통해 rbenv를 우선적으로 설치해줍니다.

    $ brew install rbenv



brew 명령어를 사용할 수 없다면 HomeBrew를 우선 적으로 설치해주세요.

[HomeBrew 설치하기](https://brew.sh/index_ko){:target="_blank"}


//설치 이미지

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

3.1.2 버전의 설치가 완료 되었지만 여전히 system이 선택되어 있습니다.

아래 명령어를 통해 대표 버전을 설치한 최신버전으로 변경해줍니다.

    $ rbenv global 3.1.2

변경 하고 나면 3.1.2가 선택되어 있는 모습을 볼 수 있습니다.

<br/>

### 3. PATH 설정하기

쉘 설정 파일을 열어 다음의 코드를 추가합니다. bigsur 이상 버전을 사용하고 있으므로 저는 zsh를 사용하여 .zshrc에 추가하도록 하겠습니다.

    $ vim ~/.zshrc


그리고 아래 두줄을 추가 해줍니다.

    export PATH="$HOME/.rbenv/bin:$PATH"
    eval "$(rbenv init -)"


https://d-dual.tistory.com/8




