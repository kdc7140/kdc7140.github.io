---
title:  "Vue.js에서 Naver Open API 영화검색 사용하기"
excerpt: "open api 사용"

toc : true
toc_sticky : true

categories:
  - Guide2
tags: 
  - NAVER
  - OPEN API
  - axios 통신
  
---

<br/>


## 1. 오픈 API 이용 신청하기

### 1.1 이용 신청하기

네이버에서 제공하는 open API를 사용하기 위해서는 우선 이용신청을 해야한다. 아래 링크를 통해 사이트에 접속 후 '오픈 API 이용 신청' 버튼을 클릭한다.

[네이버 개발자센터 오픈 API 이용 신청하기](https://developers.naver.com/products/service-api/search/search.md){:target="_blank"}


좌측 메뉴에서 애플리케이션 등록을 클릭하고 아래 이미지와 같이 정보를 입력한다.

애플리케이션 이름은 신청이 완료되고 좌측 메뉴 중 '내 애플리케이션'에 등록될 이름으로 본인이 알아볼 수 있는 이름으로 입력하고
사용 API는 '검색', 비로그인 오픈 API 서비스 환경은 'WEB 설정'을 선택한 뒤 본인이 사용하는 도메인을 입력한다.
딱히 사용하는 도메인 없이 로컬에서 확인을 한다면 이미지와 같이 입력해도 무관하다.

<img src="/assets/images/naver_api1.png">

<br/>

### 1.2 Client ID, Client Secret 확인하기

등록이 완료 됐다면 좌측 메뉴에서 '내 애플리케이션'에서 내가 등록한 애플리케이션 목록을 확인할 수 있다.
목록에서 등록한 앱을 클릭하면 아래 이미지와 같은 화면을 볼 수 있고 '개요'탭에서 Client ID와 Client Secret을 확인한다.

API를 호출하기 위해 필요한 값이니 기억해두자.

<img src="/assets/images/naver_api2.png">


<br/>


## 2. API 적용하기

적용하기 앞서 naver open api를 사용하기 위해선 Proxy 설정을 해야하는데 아래 링크를 참고하여 설정하면 된다.

[Vuedptj Proxy 오류 해결하기](https://kdc7140.github.io/vue/vue013/){:target="_blank"}

설정을 했다면 아래 코드를 보자.

axios 인스턴스를 만들고 header 값에 발급받은 Client ID와 Client Secret을 입력해주고 proxy에 target으로 설정할 url을 입력한다.<br/>
그리고 호출부에서는 axios 통신하는 것과 동일 한 형식으로 target에 입력한 url을 제외한 나머지 url과 검색어를 입력해서 결과를 리턴 받는다.


```javascript
//axios 인스턴스 생성
function searchMovieList() {
    return axios.create({
        withCredentials: true, // send cookies when cross-domain requests
        timeout: 5000,
        headers: {
            "X-Naver-Client-Id": "",			//발급한 Client ID
            "X-Naver-Client-Secret": "",		//발급한 Client Secret
        },
        proxy: {
            "/v1": {
                target: "https://openapi.naver.com",
            },
        },
    });
}

//axios 통신
searchMovieList.get("/v1/search/movie.json?query='검색어'")
	.then((result) => {
		console.log(result);
	})
	.catch((error) => {
		console.log(error);
	});
``` 
















