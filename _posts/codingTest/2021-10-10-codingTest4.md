---
title:  "다리를 지나는 트럭"
excerpt: "프로그래머스 - 코딩테스트 연습 - 연습문제"

categories:
  - JavaScript
tags: 
  - javaScript
  - algorithm 
  - programers
  - codeingTest
---

트럭 여러 대가 강을 가로지르는 일차선 다리를 정해진 순으로 건너려 합니다. 모든 트럭이 다리를 건너려면 최소 몇 초가 걸리는지 알아내야 합니다. 다리에는 트럭이 최대 bridge_length대 올라갈 수 있으며, 다리는 weight 이하까지의 무게를 견딜 수 있습니다. 단, 다리에 완전히 오르지 않은 트럭의 무게는 무시합니다.

예를 들어, 트럭 2대가 올라갈 수 있고 무게를 10kg까지 견디는 다리가 있습니다. <br/>
무게가 [7, 4, 5, 6]kg인 트럭이 순서대로 최단 시간 안에 다리를 건너려면 다음과 같이 건너야 합니다.


|경과 시간|다리를 지난 트럭|다리를 건너는 트럭|대기 트럭|
|--------|---------------|----------------|---------|
|0| [] | [] | [7,4,5,6] |
|1~2|	[]	|[7]	|[4,5,6]|
|3	|[7]	|[4]	|[5,6]|
|4	|[7]	|[4,5]	|[6]|
|5	|[7,4]	|[5]	|[6]|
|6~7	|[7,4,5]	|[6]	|[]|
|8	|[7,4,5,6]	|[]	|[]|

<br/>
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
|2	|10	| [7,4,5,6]	|8|
|100	|100	|[10]	|101|
|100	|100	|[10,10,10,10,10,10,10,10,10,10]	|110|

<br/>

**** 작성코드 ****

```java
function solution(bridge_length, weight, truck_weights) {
    var answer = 0;
    var comArr = [];
    var ingArr = [];
    const wegLen = truck_weights.length;
    
    //reduce 사용을 위해 배열길이만큼 0 추가
    for(var i=0; i<bridge_length; i++){
        ingArr.push(0);
    }
    
    while(true){
        //다리를 지난트럭 배열길이가 처음 대기트럭 배열 길이와 동일하면 반복 종료
        if(comArr.length == wegLen){
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
```


<br/>

**** 코드풀이 ****

<img src="/assets/images/ct_4.PNG"><br/><br/>

이해를 돕기 위해 '입출력 예'에서 첫 번째 조건을 도식화 시켜봤다. 실제 truck_weight의 원소를 제거하진 않지만
코드의 흐름을 보기 위한 것이니 개의치 말도록 하자.

ingArr은 다리를 건너고 있는 트럭의 배열이고, comArr은 다리를 다 건너간 트럭의 배열이다.
다리를 건너고 있는 트럭들의 무게를 쉽게 더하기 위해 reduce를 사용했는데, reduce를 사용하기 위해
ingArr을 bridge_length 만큼 0으로 채워준다.

매 반복마다 1초씩 시간은 증가하고 다리에는 weight를 초과하지 않는 한도 내에서 트럭이 지나간다.
다음 들어올 트럭의 무게와 다리 위의 트럭 무게의 합이 weight를 초과한다면 다음 트럭은 다리를 지나갈 수 없으므로
ingArr에 0을 추가한다.

ingArr의 첫 번째 값이 0이 아닌 경우 트럭이 다리를 다 지나온 것이며 comArr에 ingArr[0] 을 추가하고
매초 ingArr의 첫 번째 값을 제거한다.
위와 같은 반복을 진행하고 comArr의 길이가 bridge_length와 동일해지면 모든 트럭이 다리를 건넌 것이므로 
반복을 종료하고 시간을 return 한다.
