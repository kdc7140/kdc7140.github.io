---
title:  "2016년 요일구하기"
excerpt: "프로그래머스 - 코딩테스트 연습"

categories:
  - codingTest
tags: 
  - algorithm 
  - programers
  - codeingTest
---


<br/>
2016년 1월 1일은 금요일입니다. 2016년 a월 b일은 무슨 요일일까요? 

두 수 a ,b를 입력받아 2016년 a월 b일이 무슨 요일인지 리턴하는 함수, solution을 완성하세요. 요일의 이름은 일요일부터 토요일까지 각각 SUN,MON,TUE,WED,THU,FRI,SAT입니다. 예를 들어 a=5, b=24라면 5월 24일은 화요일이므로 문자열 "TUE"를 반환하세요.


**제한 조건**

* 2016년은 윤년입니다.
* 2016년 a월 b일은 실제로 있는 날입니다. (13월 26일이나 2월 45일같은 날짜는 주어지지 않습니다)


<br/>
**입출력 예**

|a|b|result|
|---|---|---|
|5|24|"TUE"|


<br/>
**** 작성코드****

    function solution(a, b) {
        var week = ['FRI','SAT','SUN','MON','TUE','WED','THU'];     //요일배열
        var lastDate = [31,29,31,30,31,30,31,31,30,31,30,31];       //각 월의 마지막날 배열

        var answer = week[(lastDate.slice(0,a-1).reduce((x,y) => x + y, 0) +b-1) %7];

        return answer;
    }


<br/>
**** 코드 풀이 ****

2016년 1월 1일은 금요일부터 시작하기 때문에 'FRI'로 시작하는 요일 배열 week를 만들고, 매달 마지막 날은 lastDate 배열을 만든다. 2016년 2월은 윤년이라 2월의 마지막 날은 29일이 된다.

예를 들어, 2월 1일의 경우 1월의 전체 일수 + 1일이 되고 3월 3일의 경우 1월+2월의 전체 일수 + 3일이 된다.
따라서 reduce() 함수를 사용해서 구해야 할 날짜의 전월의 전체 일수를 더해주고 구해야 할 날짜의 일수인 b를 더해준다.<br/>
lastDate.slice(0, a-1)이 되는 이유는 주어진 월인 a보다 한 달 전인 월까지의 날짜를 더해야 하기 때문이고,
b-1을 하는 이유는 week 배열의 원소를 찾아야 하므로 배열의 인덱스 시작이 1이 아닌 0이기 때문이다.

이렇게 해서 a 월 b 일까지의 전체 일수를 더하고 7로 나눈 나머지를 사용해서 요일을 구하면 되겠다.


직접 월의 마지막 날을 선언하지 않고 Script에서 제공하는 Date()를 사용해서 풀어볼 수 있는데

    function solution(a, b) {
        var week = ['SUN','MON','TUE','WED','THU','FRI','SAT'];

        var answer = week[new Date(`2016-${a}-${b}`).getDay()];

        return answer;
    }

getDay() 함수는 요일을 구할 때 많이 사용하고 일요일~토요일 순서로 0~6의 숫자를 반환한다.
이 함수를 사용할 때는 0이 일요일이므로 week 배열의 시작이 'FRI'가 아닌 'SUN'이라는 점에 주의하자.

<br/>