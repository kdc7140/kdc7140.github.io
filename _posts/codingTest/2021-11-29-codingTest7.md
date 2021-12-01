---
title:  "시저암호"
excerpt: "프로그래머스 - 연습문제 - 시저암호"

categories:
  - JavaScript
tags: 
  - JavaScript
  - algorithm 
  - programers
  - codeingTest
---

<br/>

어떤 문장의 각 알파벳을 일정한 거리만큼 밀어서 다른 알파벳으로 바꾸는 암호화 방식을 시저 암호라고 합니다. 예를 들어 "AB"는 1만큼 밀면 "BC"가 되고, 3만큼 밀면 "DE"가 됩니다. "z"는 1만큼 밀면 "a"가 됩니다. 문자열 s와 거리 n을 입력받아 s를 n만큼 민 암호문을 만드는 함수, solution을 완성해 보세요.

<br/>

**** 제한사항 ****

 - 공백은 아무리 밀어도 공백입니다.
 - s는 알파벳 소문자, 대문자, 공백으로만 이루어져 있습니다.
 - s의 길이는 8000이하 입니다.
 - n은 1이상, 25이하인 자연수입니다.

<br/>

**** 입출력 예 ****

|s|n|result|
|-|-|------|
|"AB"|1|"BC"|
|"z"|1|"a"|
|"a B z"|4|"e F d"|


<br/>

**** 작성 코드 ****

```kotlin
function solution(s, n) {
    var answer = '';
    //a-z : 97-122 / A-Z : 65-90
    
    answer = s.split("").map((el) => {
        var uni = 0;
        if(el.charCodeAt() == 32){
            uni = 32;
        }else if(el.charCodeAt()+n > 122){
            uni = el.charCodeAt()+n-26;
        }else if(el.charCodeAt() <= 90 && el.charCodeAt()+n > 90 ){
            uni = el.charCodeAt()+n-26;
        }else{
            uni =  el.charCodeAt()+n;
        }
        
        return String.fromCharCode(parseInt(uni));
    }).join("");
    return answer;
}
```


<br/>

**** 코드 풀이 ****

