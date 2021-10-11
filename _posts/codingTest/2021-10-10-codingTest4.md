---
title:  "다리를 지나는 트럭"
excerpt: "프로그래머스 - 코딩테스트 연습 - 연습문제"

categories:
  - codingTest
tags: 
  - javaScript
  - algorithm 
  - programers
  - codeingTest
---

트럭 여러 대가 강을 가로지르는 일차선 다리를 정해진 순으로 건너려 합니다. 모든 트럭이 다리를 건너려면 최소 몇 초가 걸리는지 알아내야 합니다. 다리에는 트럭이 최대 bridge_length대 올라갈 수 있으며, 다리는 weight 이하까지의 무게를 견딜 수 있습니다. 단, 다리에 완전히 오르지 않은 트럭의 무게는 무시합니다.

예를 들어, 트럭 2대가 올라갈 수 있고 무게를 10kg까지 견디는 다리가 있습니다. 무게가 [7, 4, 5, 6]kg인 트럭이 순서대로 최단 시간 안에 다리를 건너려면 다음과 같이 건너야 합니다.


|경과 시간|다리를 지난 트럭|다리를 건너는 트럭|대기 트럭|
|--------|---------------|----------------|---------|
|0|[]|[]|[7,4,5,6]|
|1~2|	[]	|[7]	|[4,5,6]|
|3	|[7]	|[4]	|[5,6]|
|4	|[7]	|[4,5]	|[6]|
|5	|[7,4]	|[5]	|[6]|
|6~7	|[7,4,5]	|[6]	|[]|
|8	|[7,4,5,6]	|[]	|[]|


따라서, 모든 트럭이 다리를 지나려면 최소 8초가 걸립니다.

solution 함수의 매개변수로 다리에 올라갈 수 있는 트럭 수 bridge_length, 다리가 견딜 수 있는 무게 weight, 트럭 별 무게 truck_weights가 주어집니다. 이때 모든 트럭이 다리를 건너려면 최소 몇 초가 걸리는지 return 하도록 solution 함수를 완성하세요.

**제한조건**

* bridge_length는 1 이상 10,000 이하입니다.
* weight는 1 이상 10,000 이하입니다.
* truck_weights의 길이는 1 이상 10,000 이하입니다.
* 모든 트럭의 무게는 1 이상 weight 이하입니다.<br/><br/>


**입출력 예**

|bridge_length	|weight	|truck_weights	|return|
|---------------|-------|---------------|------|
|2	|10	|[7,4,5,6]	|8|
|100	||100	|[10]	|101|
|100	|100	|[10,10,10,10,10,10,10,10,10,10]	|110|



****작성코드****

    function solution(bridge_length, weight, truck_weights) {
      var answer = 0;
      var comArr = [];
      var ingArr = [];
      const wegArr = truck_weights.length;
      
      //reduce 사용을 위해 배열길이만큼 0 추가
      for(var i=0; i<bridge_length; i++){
          ingArr.push(0);
      }
      
      while(true){
          //다리를 지난트럭 배열길이가 처음 대기트럭 배열 길이와 동일하면 반복 종료
          if(comArr.length == wegArr){
              break;
          }else{
              //다리를 건너는 트럭이 마지막에 도달하면 다리를 지난트럭 배열에 추가
              if(ingArr[0] != 0){
                  comArr.push(ingArr[0]);   
              }
              //다리를 건넜으니 다리를 건너는 트럭배열에서 첫번째 값 제거
              ingArr.shift();
              
              //다리를 건너고 있는 트럭무게와 대기중인 첫번째 트럭무게의 합이 weight 보다 작거나 같을경우
              //대기중인 첫번째 트럭이 다리를 건넘
              if(ingArr.reduce((a, b) => a + b)+truck_weights[0] <= weight){
                  ingArr.push(truck_weights[0]);
                  truck_weights.shift();
              }else{
                  ingArr.push(0);
              }
          }
          answer += 1;
      }
      return answer;
  }

