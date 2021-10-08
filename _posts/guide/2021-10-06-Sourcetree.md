---
title:  "[Git]소스트리(Sourcetree) 설치&설명"
excerpt: "[Git]소스트리(Sourcetree) 설치&설명"

categories:
  - Tool
tags: 
  - Sourcetree
  - Git GUI
---


<br/>
안녕하세요 **모야**입니다.

오늘은 Git GUI 중의 하나인 SourceTree를 설치해보고 구성에대해 간단히 설명해보도록 하겠습니다.

GUI(Graphical User Interface)란 누구나 이해하기 쉽도록 프로젝트 히스토리를 시각적으로 나타내주는 도구입니다.
말 그대로 Git GUI는 Git을 더 편하게 사용할 수 있도록 시각화해서 보여주는 도구라고 생각하면 될 것 같습니다.

SourceTree는 Window와 Max OS에서 사용이 가능하기 때문에 대중적으로 많이 쓰이는 Git GUI입니다.<br/>
덕분에 설치방법이나 사용법에 대해 다룬 글이 많아서 초보자도 사용 진입장벽이 낮아 쉽게 사용할 수 있고, 저도 자주 사용하고 있기 때문에 간략하게나마 포스팅해 보려고 합니다.

Git GUI에는 SourceTree 말고도 github desktop, GitKraken, SmartGit 등 다양한 종류가 있으니 본인이 사용하기 편한 Tool을 찾아 설치하여 사용하시면 됩니다.



<br/><br/>

### 1. SourceTree 설치하기

먼저 SourceTree 홈페이지에 접속해서 본인의 운영체제에 맞는 설치파일을 다운로드 합니다.

[SourceTree 설치페이지](https://www.sourcetreeapp.com){:target="_blank"}


<img src="/assets/images/sourceTree_homepage.PNG"><br/><br/>


설치파일을 실행하면 아래와 같은 화면이 나타나는데 Bitbucket Server 또는 bitbucket을 사용하실 분들은 체크해서 로그인을 진행하시면 되고 계정이 없으신 분은 Create one for free를 눌러 회원가입을 진행하셔야 합니다.
이미 로그인이 되있다면 건너뛰기 버튼이 나오는데 그냥 건너뛰기를 눌러 다음으로 넘어가도록 합니다.

* Bitbucket Server : 개별 서버를 설치한 경우 로그인할 때 선택
* Bitbucket : Bitbucket에 가입된 사용자가 로그인할 때 선택

<img src="/assets/images/st_1.PNG"><br/><br/>


아래는 Bitbucket 회원가입 화면입니다. 아래 화면에서 로그인을 진행하면 다음단계로 진행됩니다.

<img src="/assets/images/bucket_login.PNG"><br/><br/>


Git을 사용할거니까 Git에 체크해주시고 Mercurial은 Git과 비슷한 툴로 설치하셔도 되고 안하셔도 됩니다.

<img src="/assets/images/st_2.PNG"><br/><br/>


ID와 Email을 입력하고 다음버튼을 누릅니다.

<img src="/assets/images/st_3.PNG"><br/><br/>


마지막으로 보유하고 있는 SSH키가 있다면 등록하면 되는데 갖고 있는 키가 없다면 '아니오'를 눌러 넘어갑니다. 추후 등록할 수 있기 때문에 등록하지 않아도 무관합니다.

<img src="/assets/images/st_4.PNG"><br/><br/>


모든 설치절차를 마치고 아래와 같이 SourceTree가 실행되면 설치 완료입니다.

<img src="/assets/images/sourceTree.PNG"><br/><br/>


### 2. SourceTree 사용법


설치를 완료 했으니 사용법에 대해 간략히 알아보도록 하겠습니다.
SourceTree를 실행하면 상단에 Local, Remote / Clone, Add, Create 5개의 메뉴가 있습니다.

* Local : 로컬 저장소로 .git폴더가 있는 리스트를 보여줍니다.
* Remote : 원격저장소의 리스트를 보여줍니다.
* Clone : Repository를 로컬로 복사합니다.
* Add : 기존 저장소를 추가합니다.
* Create : 새로운 저장소를 만듭니다.
  

<img src="/assets/images/st_main.PNG"><br/><br/>


5개의 메뉴중 Clone을 사용해서 Repository를 로컬에 복사해오도록 하겠습니다.
Clone 버튼을 눌러보면 입력화면이 나타나는데 맨 위칸 소스경로 / URL 입력창에 복사해올 Git Repository 주소를 
입력해주시면 됩니다.<br/>
경로를 입력하면 나머지 칸은 자동으로 채워지지만 저장경로를 따로 설정하실 분은 
목적지 경로를 따로 설정해서 진행하시길 바랍니다.


<img src="/assets/images/st_clone.PNG"><br/><br/>


정상적으로 Clone이 진행되었다면 아래와 같은 화면이 나타나고 많은 메뉴가 있는 것을 볼 수 있습니다.
화면을 구성하고 있는 메뉴들에 대해 간단히 설명을 하도록 하겠습니다.


<img src="/assets/images/st_repo.PNG"><br/><br/>


1. 상단 좌측 메뉴바
 * **커밋(Commit)**   : 로컬의 변경사항을 Github Repository에 기록
 * **풀(Pull)**       : Github Repository의 변경사항을 로컬에 반영
 * **푸시(Push)**     : Commit한 내용을 Github Repository에 저장
 * **패치(Fetch)**    : Github Repository의 변경사항을 로컬로 가지고 옴(반영x)
 * **브랜치(Branch)** : 브랜치(작업공간) 생성 및 삭제
 * **병합(Merge)**    : 2개 이상의 브랜치를 하나로 합침
 * **스태시(Stash)**  : 로컬에서 작업한 내용을 임시로 다른곳에 저장
 * **폐기(Discard)**  : 변경사항 되돌리기
 * **태그(Tag)**      : 참조하기 쉽도록 이력을 남김<br/><br/>


2. 상단 우측 메뉴바
 *  깃플로우 : 깃플로우를 사용할 저장소 선택창을 연다
 *  원격     : 원격저장소를 연다
 *  터미널   : 명령창 또는 터미널을 연다
 *  탐색기   : 윈도우 탐색기를 연다
 *  설정     : 설정창을 연다<br/><br/>
  

3. Repository의 브랜치, 태그 등 내용을 확인할 수 있다.<br/><br/>


4. 프로젝트의 커밋 히스토리를 확인할 수 있다. <br/><br/>
  

5. 커밋에 대한 설명과 파일 정보를 확인할 수 있다.<br/><br/>



주로 사용하는 메뉴는 상단 좌측메뉴인 1번 메뉴들이지만 나머지 기능들도 알아둬서 나쁠건 없으니 
사용하시기 전에 한번 읽어보시는걸 추천드립니다.<br/>
어떤 기능을 하는지 알고 있으면 사용하는 방법은 크게 어렵지 않으니, 직접 사용해보시면서 방법을 익히시면 좋을 것 같습니다.



감사합니다.<br/>


