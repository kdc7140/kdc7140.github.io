---
title:  "[Git]소스트리(Sourcetree) 설치&사용"
excerpt: "[Git]소스트리(Sourcetree) 설치&사용"

categories:
  - Tool
tags: 
  - Sourcetree
  - Git GUI
---


<br/>
안녕하세요 **모야**입니다.

오늘은 Git GUI 중의 하나인  SourceTree 설치 및 사용법을 알아보겠습니다.

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


Github에 Repository를 새로 생성해서 Clone으로 로컬에 복사해보도록 하겠습니다.
Github 사이트에 접속해서 Repositories 버튼을 클릭하고 우측의 New 버튼을 눌러줍니다.

<img src="/assets/images/git_repo.PNG"><br/><br/>


Repository명을 입력하고 Add a README file 체크 후 생성해줍니다

<img src="/assets/images/create_repo.PNG"><br/><br/>