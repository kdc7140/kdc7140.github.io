---
title:  "모의고사"
excerpt: "프로그래머스 - 완전탐색 - 모의고사"

categories:
  - JavaScript
tags: 
  - JavaScript
  - algorithm 
  - programers
  - codeingTest
---

<br/>


수포자는 수학을 포기한 사람의 준말입니다. 수포자 삼인방은 모의고사에 수학 문제를 전부 찍으려 합니다. 수포자는 1번 문제부터 마지막 문제까지 다음과 같이 찍습니다.

1번 수포자가 찍는 방식: 1, 2, 3, 4, 5, 1, 2, 3, 4, 5, ...
2번 수포자가 찍는 방식: 2, 1, 2, 3, 2, 4, 2, 5, 2, 1, 2, 3, 2, 4, 2, 5, ...
3번 수포자가 찍는 방식: 3, 3, 1, 1, 2, 2, 4, 4, 5, 5, 3, 3, 1, 1, 2, 2, 4, 4, 5, 5, ...

1번 문제부터 마지막 문제까지의 정답이 순서대로 들은 배열 answers가 주어졌을 때, 가장 많은 문제를 맞힌 사람이 누구인지 배열에 담아 return 하도록 solution 함수를 작성해주세요.

<br/>

**** 제한조건 ****

 - 시험은 최대 10,000 문제로 구성되어있습니다.
 - 문제의 정답은 1, 2, 3, 4, 5중 하나입니다.
 - 가장 높은 점수를 받은 사람이 여럿일 경우, return하는 값을 오름차순 정렬해주세요.

 
 ** 입출력 예

|answer|return|
|[1,2,3,4,5]|[1]|
|[1,3,2,4,2]|[1,2,3]|


** 입출력 예 #1

수포자 1은 모든 문제를 맞혔습니다.
수포자 2는 모든 문제를 틀렸습니다.
수포자 3은 모든 문제를 틀렸습니다.
따라서 가장 문제를 많이 맞힌 사람은 수포자 1입니다.

<br/>

입출력 예 #2

모든 사람이 2문제씩을 맞췄습니다.

<br/>

**** 작성 코드 ****

```javascript
function solution(answers) {
    var answer = [];
    var ansArr1 = [1,2,3,4,5];
    var ansArr2 = [2,1,2,3,2,4,2,5];
    var ansArr3 = [3,3,1,1,2,2,4,4,5,5];
    var supo = [0,0,0];
    
    for(var i=0; i<answers.length; i++){
        answers[i] == ansArr1[i % ansArr1.length] ? supo[0] += 1 : "";
        answers[i] == ansArr2[i % ansArr2.length] ? supo[1] += 1 : "";
        answers[i] == ansArr3[i % ansArr3.length] ? supo[2] += 1 : "";
    }
    
    var maxCnt = Math.max(supo[0],supo[1],supo[2]);
    
    for(var i=0; i<supo.length; i++){
        supo[i] == maxCnt ? answer.push(i+1) : "";
    }
    
    return answer;
}
```


수포자들의 찍는 방식을 각 배열로 만든다. 정답인 answers와 수포자들의 찍는 방식 배열을 비교해서 맞춘 개수를 누적해서 더하고
가장 많이 맞춘 개수를 maxCnt에 저장한다.
그리고 수포자들이 맞춘 갯수와 maxCnt가 같으면 answer에 카운트를 누적해서 더하고 리턴한다.