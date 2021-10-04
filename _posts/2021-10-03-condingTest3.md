---
title:  "나누어 떨어지는 숫자 배열"
excerpt: "프로그래머스 - 코딩테스트 연습"

categories:
  - codingTest
tags: 
  - algorithm 
  - programers
  - codeingTest
---

<br/>
array의 각 element 중 divisor로 나누어 떨어지는 값을 오름차순으로 정렬한 배열을 반환하는 함수, solution을 작성해주세요.
divisor로 나누어 떨어지는 element가 하나도 없다면 배열에 -1을 담아 반환하세요.

**제한사항**

* arr은 자연수를 담은 배열입니다.
* 정수 i, j에 대해 i ≠ j 이면 arr[i] ≠ arr[j] 입니다.
* divisor는 자연수입니다.
* array는 길이 1 이상인 배열입니다.

<br/>
**입출력 예**

|arr|divisor|return|
|---|-------|------|
|[5, 9, 7, 10]|5|[5, 10]|
|[2, 36, 1, 3]|1|[1, 2, 3, 36]|
|[3,2,6]|10|[-1]|


<br/>
**입출력 예 설명**

입출력 예#1<br/>
arr의 원소 중 5로 나누어 떨어지는 원소는 5와 10입니다. 따라서 [5, 10]을 리턴합니다.

입출력 예#2<br/>
arr의 모든 원소는 1으로 나누어 떨어집니다. 원소를 오름차순으로 정렬해 [1, 2, 3, 36]을 리턴합니다.

입출력 예#3<br/>
3, 2, 6은 10으로 나누어 떨어지지 않습니다. 나누어 떨어지는 원소가 없으므로 [-1]을 리턴합니다.


<br/>
**** 작성 코드 ****

    function solution(arr, divisor) {
      var answer = [];
      
      arr.forEach((el) => {
        el%divisor == 0 ? answer.push(el) : "";
      });
      
      answer.length == 0 ? answer.push(-1) : answer.sort((a,b) => a-b);
      
      return answer;
  }


<br/>
**코드 풀이**

배열 arr의 길이만큼 반복문을 돌려주고 arr의 원소가 divisor으로 나누어지는지 확인해서 나눠 떨어지면 answer에 담는다.
정답 배열인 answer이 비어있다면 -1을 담고, 값이 들어있다면 원소를 오름차순으로 정렬한다.