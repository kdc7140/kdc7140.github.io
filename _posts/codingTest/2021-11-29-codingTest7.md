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

어떤 문장의 각 알파벳을 일정한 거리만큼 밀어서 다른 알파벳으로 바꾸는 
암호화 방식을 시저 암호라고 합니다.<br/> 
예를 들어 "AB"는 1만큼 밀면 "BC"가 되고, 3만큼 밀면 "DE"가 됩니다. 
"z"는 1만큼 밀면 "a"가 됩니다.<br/>
문자열 s와 거리 n을 입력받아 s를 n만큼 민 암호문을 만드는 함수, solution을 완성해 보세요.

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

아스키코드를 사용하여 간단히 접근할 수 있는 문제다.
우선 문자열 s를 하나하나 비교하기 위해 split을 사용하여 배열로 만들고 탐색을 한다.
공백은 아무리 밀어도 공백이므로 스페이스바 '공백'의 코드 32는 그대로 32로 둔다.

s는 알파벳 소문자, 대문자, 공백으로 이루어져 있고 z를 1만큼 밀면 a가 되는걸로 봐서
대문자는 아무리 밀어도 대문자, 소문자는 아무리 밀어도 소문자가 될 것이다.

그러므로, 알파벳 소문자는 아스키코드 97~122이고, 대문자는 65~90이므로 각자의 최대값인 122와 90을
넘어갈 경우에는 최소값과의 차이인 26을 빼주고, 최대값을 넘지 않는 범위라면 n만큼 더해준다.

모든 값의 계산이 끝나면 fromCharCode를 통해 아스키코드를 문자열로 반환하고 join을 사용하여
배열을 문자열형태로 변경하여 반환한다.

아스키코드를 사용하지 않고 풀어볼 수 있을 것 같은데, 다음에 도전해봐야겠다.



<br/>


**** 아스키코드 사용하지 않은 코드 ****

```kotlin
function solution(s, n) {
    var upper = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    var lower = "abcdefghijklmnopqrstuvwxyz";
    var answer= '';

    for(var i=0; i<s.length; i++){
        var text = s[i];

        if(text == ' ') {
            answer += ' '; 
            continue;
        }

        var textArr = upper.includes(text) ? upper : lower;
        var index = textArr.indexOf(text)+n;
        
        if(index >= textArr.length){
            index -= textArr.length;
        }
            
        answer += textArr[index];
    }
    return answer;
}
```