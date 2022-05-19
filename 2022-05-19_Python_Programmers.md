# 프로그래머스_Python_스킬트리

## Problem link (https://programmers.co.kr/learn/courses/30/lessons/49993)

### 접근

<aside>
💡 skill 조건들

-스킬은 중복되지 않음

-**CBD가 중간에 끊기더라도 선행 순서가 맞게 들어있으면 정답으로 인정됨  —> 보충 필요** 

-스킬 경우의 수(선행스킬CBD, 유저들의 여러 스킬트리)는 skill_trees 안에 원소로 들어있음

~~-AECB도 가능한 스킬트리임 ⇒ C→B 선행조건은 충족했으니 D가 꼭 있어야 되는건 아님~~

skill_trees 에서 하나씩 꺼내오는 for 반복문

꺼낸 원소 과 - **in**  skill 한 글자씩 비교

→ 조건 충족 스킬트리 개수를 반환하는 함수 짜보기

</aside>

### 내 풀이

```python
def solution(skill, skill_trees):
    answer=0
    for eachTree in skill_trees:        #스킬트리를 하나씩 꺼내옴
        temp=''
        for eachSkill in eachTree:      #스킬 하나 (한 문자)
            if eachSkill in skill:      #그 스킬이 skill 중에 있다면
                temp += eachSkill       #임시에 추가
            else:
                pass
        if temp == skill[0:len(temp)]:  #그 순서가 skill과 같다면
            answer += 1                 #가능한 스킬트리 카운팅
    return answer
```

### 오답

```python
def solution(skill, skill_trees):
    answer=0
    ***temp=''    --> 이걸 for 문 안에 안두고 여기에 둬놓고 헤맴***
    for eachTree in skill_trees:   #스킬트리를 for 반복문으로 하나씩 꺼내옴
        for eachSkill in eachTree:
            if eachSkill in skill: 
                temp += eachSkill --> ***#temp에 문자를 넣는 방식이 아닌, 카운팅을 해나가는 temp +=1 풀이를 만들려하다가 헤맴***
            else:
                pass
        if temp == skill[0:len(temp)]:  #그 순서가 skill과 같다면
            answer += 1
    return answer
```

### 다른 사람 풀이

```python
def solution(skill, skill_trees):
    answer = 0

    for skills in skill_trees:
        skill_list = list(skill)  ***--> 리스트 안에 담았다***

        for s in skills:
            if s in skill:
                if s != skill_list.pop(0):  --> ***pop()함수 써서 맨앞레터 제거함 --> 제거 후 첫 레터를 비교해나가는 방식***!
                    break
        else:
            answer += 1

    return answer
```
