<!-- ---
title: ' [CodingTest] 카카오 블라인드 - 프로그래밍 2 '
date: 2019-09-07 14:30:00
category: 'codingtest'
---

![](./images/logo.png)

<center><strong>2020 KAKAO BLIND RECRUITMENT</strong></center>

<br />

## **💎 목차**
  * [문제 설명 (Problem)](#-문제-설명)
  * [용어 정의 (Definition)](#-용어-정의)
  * [입출력 예 (Example)](#-입출력-예)
  * [문제 풀이 (Solution)](#-문제-풀이)

## **📕 문제 설명**

- 카카오에 신입 개발자로 입사한 콘은 선배 개발자로부터 개발역량 강화를 위해 다른 개발자가 작성한 소스 코드를 분석하여 문제점을 발견하고 수정하라는 업무 과제를 받았습니다. 

- 소스를 컴파일하여 로그를 보니 대부분 소스 코드 내 작성된 괄호가 개수는 맞지만 짝이 맞지 않은 형태로 작성되어 오류가 나는 것을 알게 되었습니다.

- 수정해야 할 소스 파일이 너무 많아서 고민하던 콘은 소스 코드에 작성된 모든 괄호를 뽑아서 올바른 순서대로 배치된 괄호 문자열을 알려주는 프로그램을 다음과 같이 개발하려고 합니다.

<br />

**[⬆ 목차](#-목차)**

---

## **🔖 용어 정의**

- '(' 와 ')' 로만 이루어진 문자열이 있을 경우, '(' 의 개수와 ')' 의 개수가 같다면 이를 `균형잡힌 괄호 문자열`이라고 부릅니다.

- 그리고 여기에 '('와 ')'의 괄호의 짝도 모두 맞을 경우에는 이를 `올바른 괄호 문자열`이라고 부릅니다.

- 예를 들어, `"(()))("`와 같은 문자열은 균형잡힌 괄호 문자열 이지만 올바른 괄호 문자열은 아닙니다.

- 반면에 `"(())()"`와 같은 문자열은 균형잡힌 괄호 문자열 이면서 동시에 올바른 괄호 문자열 입니다.

- '(' 와 ')' 로만 이루어진 문자열 w가 균형잡힌 괄호 문자열 이라면 다음과 같은 과정을 통해 올바른 괄호 문자열로 변환할 수 있습니다.

```
1. 입력이 빈 문자열인 경우, 빈 문자열을 반환합니다.

2. 문자열 w를 두 "균형잡힌 괄호 문자열" u, v로 분리합니다. 
  2-1. 단, u는 "균형잡힌 괄호 문자열"로 더 이상 분리할 수 없어야 하며, 
  2-2. v는 빈 문자열이 될 수 있습니다.

3. 문자열 u가 "올바른 괄호 문자열" 이라면 문자열 v에 대해 1단계부터 다시 수행합니다. 
  3-1. 수행한 결과 문자열을 u에 이어 붙인 후 반환합니다. 

4. 문자열 u가 "올바른 괄호 문자열"이 아니라면 아래 과정을 수행합니다. 
  4-1. 빈 문자열에 첫 번째 문자로 '('를 붙입니다. 
  4-2. 문자열 v에 대해 1단계부터 재귀적으로 수행한 결과 문자열을 이어 붙입니다. 
  4-3. ')'를 다시 붙입니다. 
  4-4. u의 첫 번째와 마지막 문자를 제거하고, 
  4-5. 나머지 문자열의 괄호 방향을 뒤집어서 뒤에 붙입니다. 
  4-6. 생성된 문자열을 반환합니다.

```

균형잡힌 괄호 문자열 p가 매개변수로 주어질 때, 주어진 알고리즘을 수행해 올바른 괄호 문자열로 변환한 결과를 return 하도록 solution 함수를 완성해 주세요.

<br />

__매개변수 설명__

- p는 '(' 와 ')' 로만 이루어진 문자열이며 길이는 2 이상 1,000 이하인 짝수입니다.

- 문자열 p를 이루는 '(' 와 ')' 의 개수는 항상 같습니다.

- 만약 p가 이미 올바른 괄호 문자열이라면 그대로 return 하면 됩니다.

<br />

**[⬆ 목차](#-목차)**

---

## **📙 입출력 예**

![](./images/2.example.png)
<br />

- 입출력 예 #1
    - 문자열을 1개 단위로 잘라 압축했을 때 가장 짧습니다.

-  입출력 예 #2
    - 문자열을 8개 단위로 잘라 압축했을 때 가장 짧습니다.

- 입출력 예 #3
    - 문자열을 3개 단위로 잘라 압축했을 때 가장 짧습니다.

- 입출력 예 #4
    - 문자열을 2개 단위로 자르면 abcabcabcabc6de 가 됩니다.
    - 문자열을 3개 단위로 자르면 4abcdededededede 가 됩니다.
    - 문자열을 4개 단위로 자르면 abcabcabcabc3dede 가 됩니다.
    - 문자열을 6개 단위로 자를 경우 2abcabc2dedede가 되며, 이때의 길이가 14로 가장 짧습니다.

- 입출력 예 #5
    - 문자열은 제일 앞부터 정해진 길이만큼 잘라야 합니다.
    - 따라서 주어진 문자열을 x / ababcdcd / ababcdcd 로 자르는 것은 불가능 합니다.
    - 이 경우 어떻게 문자열을 잘라도 압축되지 않으므로 가장 짧은 길이는 17이 됩니다.

<br />

**[⬆ 목차](#-목차)**

---

## **📘 문제 풀이**

풀이는 추후
<br />

**[⬆ 목차](#-목차)**

---

<br />

> 출처
>
> <a href="https://programmers.co.kr/tryouts/9846/challenges/33724" target="_blank">온라인 코딩테스트 > 프로그래밍 2</a>

# 여러분의 댓글이 큰힘이 됩니다. (๑•̀ㅂ•́)و✧ -->