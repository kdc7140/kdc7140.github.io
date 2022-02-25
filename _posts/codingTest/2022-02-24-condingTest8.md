---
title:  "가장 큰 수"
excerpt: "프로그래머스 - 정렬 - 가장 큰 수"

categories:
  - JavaScript
tags: 
  - JavaScript
  - algorithm 
  - programers
  - codeingTest
---

<br/>


0 또는 양의 정수가 주어졌을 때, 정수를 이어 붙여 만들 수 있는 가장 큰 수를 알아내 주세요.
예를 들어, 주어진 정수가 [6, 10, 2]라면 [6102, 6210, 1062, 1026, 2610, 2106]를 만들 수 있고, 
이중 가장 큰 수는 6210입니다.
0 또는 양의 정수가 담긴 배열 numbers가 매개변수로 주어질 때, 순서를 재배치하여 만들 수 있는 
가장 큰 수를 문자열로 바꾸어 return 하도록 solution 함수를 작성해주세요.


<br/>

**** 제한사항 ****
 - numbers의 길이는 1 이상 100,000 이하입니다.
 - numbers의 원소는 0 이상 1,000 이하입니다.
 - 정답이 너무 클 수 있으니 문자열로 바꾸어 return 합니다.


 <br/>

**** 입출력 예 ****

|numbers|return||
|[6, 10, 2]|"6210"|
|[3, 30, 34, 5, 9]|"9534330"|


<br/>


**** 작성 코드 ****

```javascript
function solution(numbers) {
    var answer = [];
    
    answer = numbers.sort(function(x,y){
        var e = Number(String(x)+String(y));
        var q = Number(String(y)+String(x));

        return q-e

    }).join('');
    
    return answer;
}
```


<br/>

**** 코드 풀이 ****

주어진 배열의 원소로 가장 큰 수를 만드는 문제인데 순서대로 앞, 뒤 원소를 합쳐서 크기 비교하여 
오름차순으로 정렬하면 쉽게 풀리는 문제인 것 같다.
1번+2번 순서의 원소를 더한 것과, 2번+1번 순서로 더한 수의 크기를 비교해서 오름차순으로 정렬한 배열을
join()을 사용하여 배열을 문자열로 변경해주면 된다.
