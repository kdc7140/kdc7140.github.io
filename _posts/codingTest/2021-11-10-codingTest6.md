---
title:  "체육복"
excerpt: "프로그래머스 - 코딩테스트 연습 - 탐욕법(Greedy)"

categories:
  - Kotlin
tags: 
  - Kotlin
  - algorithm 
  - programers
  - codeingTest
---



<br/>
점심시간에 도둑이 들어, 일부 학생이 체육복을 도난당했습니다. 다행히 여벌 체육복이 있는 학생이 이들에게 체육복을 빌려주려 합니다. 학생들의 번호는 체격 순으로 매겨져 있어, 바로 앞번호의 학생이나 바로 뒷번호의 학생에게만 체육복을 빌려줄 수 있습니다. 예를 들어, 4번 학생은 3번 학생이나 5번 학생에게만 체육복을 빌려줄 수 있습니다. 체육복이 없으면 수업을 들을 수 없기 때문에 체육복을 적절히 빌려 최대한 많은 학생이 체육수업을 들어야 합니다.

전체 학생의 수 n, 체육복을 도난당한 학생들의 번호가 담긴 배열 lost, 여벌의 체육복을 가져온 학생들의 번호가 담긴 배열 reserve가 매개변수로 주어질 때, 체육수업을 들을 수 있는 학생의 최댓값을 return 하도록 solution 함수를 작성해주세요.
<br/><br/>

**** 제한사항 ****

- 전체 학생의 수는 2명 이상 30명 이하입니다.
- 체육복을 도난당한 학생의 수는 1명 이상 n명 이하이고 중복되는 번호는 없습니다.
- 여벌의 체육복을 가져온 학생의 수는 1명 이상 n명 이하이고 중복되는 번호는 없습니다.
- 여벌 체육복이 있는 학생만 다른 학생에게 체육복을 빌려줄 수 있습니다.
- 여벌 체육복을 가져온 학생이 체육복을 도난당했을 수 있습니다. 이때 이 학생은 체육복을 하나만 도난당했다고 가정하며, 남은 체육복이 하나이기에 다른 학생에게는 체육복을 빌려줄 수 없습니다.


<br/>

**** 입출력 예 ****

|n|lost|reverve|return|
|---|---|---|---|
|5|[2, 4]|[1, 3, 5]|5|
|5|[2, 4]|[3]|4|
|3|[3]|[1]|2|


<br/>

**** 입출력 예 설명 ****

예제 #1
 - 1번 학생이 2번 학생에게 체육복을 빌려주고, 3번 학생이나 5번 학생이 4번 학생에게 체육복을 빌려주면 학생 5명이 체육수업을 들을 수 있습니다.

예제 #2
 - 3번 학생이 2번 학생이나 4번 학생에게 체육복을 빌려주면 학생 4명이 체육수업을 들을 수 있습니다.

<br/>

### ** 작성코드 **

```kotlin
class Solution {
    fun solution(n: Int, lost: IntArray, reserve: IntArray): Int {
        var answer = n

        //여분의 체육복이 있는 사람이 체육복을 잃어버렸을 경우 제거
        var lostSet = lost.toSet() - reserve.toSet()
        var reserveSet = (reserve.toSet() - lost.toSet()) as MutableSet

        //체육복을 잃어버린 사람의 앞뒷사람이 여분의 체육복을 가지고 있는경우
        for (item in lostSet) {
            when {
                item - 1 in reserveSet -> reserveSet.remove(item - 1)
                item + 1 in reserveSet -> reserveSet.remove(item + 1)
                else -> answer--
            }
        }
        
        return answer
    }
}
```


<br/>

### ** 코드풀이 **

배열의 값을 넣고 빼기 위해 array -> set 으로 변경 하고, 
체육복을 도난당한 당사자가 여분이 있을 수 있는 경우를 제외하여
lost, reserve를 생성한다.<br/>

본인이 잃어버린 경우를 제외 했으므로 잃어버린 사람의 앞, 뒤 사람이 여분의 체육복이 있는지 확인해야하는데
비교 순서는 앞사람 -> 뒷사람 순서로 진행해야 한다.<br/>
뒷사람에게 먼저 빌릴 경우 lost = [2,4], reserve = [1,3] 케이스를 보면 2번이 3번에게 체육복을 빌려
4번이 체육복을 입을 수 없게 된다.<br/>

따라서 앞사람에게 먼저 빌리도록 하고 마지막까지 빌리지 못한 lostSet의 사람수 만큼 전체 사람수인 n에서 빼준다.


<br/>

조건만 잘 파악하여 푼 다면 수월하게 풀 수 있는 것 같다. 위 풀이처럼 앞사람과 우선 비교를 해야한다는 점을
주목해서 풀면 모든 테스트 케이스를 통과할 수 있다.


