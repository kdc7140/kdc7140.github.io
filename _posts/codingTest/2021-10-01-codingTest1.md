---
title:  "K번째수 구하기"
excerpt: "프로그래머스 - 코딩테스트 연습 - 정렬"

categories:
  - codingTest
tags: 
  - algorithm 
  - programers
  - codeingTest
---



<br/>
배열 array의 i번째 숫자부터 j번째 숫자까지 자르고 정렬했을 때, k번째에 있는 수를 구하려 합니다.<br/>

예를 들어 array가 [1, 5, 2, 6, 3, 7, 4], i = 2, j = 5, k = 3이라면 array의 2번째부터 5번째까지 자르면 [5, 2, 6, 3]입니다.

 * 1에서 나온 배열을 정렬하면 [2, 3, 5, 6]입니다.
 * 2에서 나온 배열의 3번째 숫자는 5입니다.

배열 array, [i, j, k]를 원소로 가진 2차원 배열 commands가 매개변수로 주어질 때, commands의 모든 원소에 대해 앞서 설명한 연산을 적용했을 때 나온 결과를 배열에 담아 return 하도록 solution 함수를 작성해주세요.<br/><br/>


**제한사항**

* array의 길이는 1 이상 100 이하입니다.
* array의 각 원소는 1 이상 100 이하입니다.
* commands의 길이는 1 이상 50 이하입니다.
* commands의 각 원소는 길이가 3입니다.

<br/>
**입출력 예**

|array|commands|return|
|------------------------|---|---|
|[1, 5, 2, 6, 3, 7, 4]|[[2, 5, 3], [4, 4, 1], [1, 7, 3]]|[5, 6, 3]|

<br/>
**입출력 예 설명**

* [1, 5, 2, 6, 3, 7, 4]를 2번째부터 5번째까지 자른 후 정렬합니다. [2, 3, 5, 6]의 세 번째 숫자는 5입니다.
* [1, 5, 2, 6, 3, 7, 4]를 4번째부터 4번째까지 자른 후 정렬합니다. [6]의 첫 번째 숫자는 6입니다.
* [1, 5, 2, 6, 3, 7, 4]를 1번째부터 7번째까지 자릅니다. [1, 2, 3, 4, 5, 6, 7]의 세 번째 숫자는 3입니다.	


<br/>
****작성 코드****

    function solution(array, commands) {
      var answer = [];      //정답배열
      var sArr = [];        //i~j까지 자르고 정렬할 배열

      for(var i=0; i<commands.length; i++){
          sArr = sort(array.slice(commands[i][0]-1,commands[i][1]));
          answer.push(sArr[commands[i][2]-1]);
      }

      return answer;
    }

    //숫자 정렬
    function sort(arr){
      var temp = null;
      for(var i=0; i<arr.length; i++){
          for(var j=0; j<arr.length-1; j++){
              if(arr[j] > arr[j+1]){
                  temp = arr[j];
                  arr[j] = arr[j+1];
                  arr[j+1] = temp;
              }
          }
      }
      return arr;
    }

    

<br/><br/>
**** 코드 풀이 ****

2차원 배열의 길이만큼 반복하면서 진행한다. i는 배열의 첫번째, j는 두번째 원소이므로 commands[i][0]-1 부터 commands[i][1] 까지 slice() 함수를 이용해 배열을 잘라준다. commands[i][0]-1 부터 잘라주는 이유는 배열에서 첫번째 원소는 1이 아닌 0부터 시작하기 때문이다.<br/>

slice() 함수를 이용하여 i~j까지 자르고 정렬한 배열을 sArr에 담고, 배열의 세번째 원소인 k번째 숫자를 구하기 위해 sArr배열에서 commands[i][2]-1 번째 원소를 찾아 정답으로 사용할 배열은 answer에 담아서 리턴한다.<br/>

위 풀이와 같이 숫자를 정렬하는 함수를 직접 만들수도 있지만 Script에서 제공하는 sort() 함수를 사용하여 아래와 같이 더 간단하게 작성할 수 있다.

    function solution(array, commands) {
      var answer = [];
      var sArr = [];
      
      for(var i=0; i<cArr.length; i++){
          sArr = array.slice(commands[i][0]-1,commands[i][1]).sort(function(a,b){return a - b});
          answer.push(sArr[commands[i][2]-1]);
      }
      
      return answer;
    }

sort(function(a,b,){reuturn a-b})로 사용해야하는 이유는 sort() 함수는 유니코드 순서에 따라 값을 정렬하기 때문에 숫자를 정렬할 때 2,3 보다 10, 11이 먼저 정렬된다. 따라서, 유니코드 순이 아닌 1,2,3... 숫자의 순서대로 정렬하기 위함이다.

<br/>