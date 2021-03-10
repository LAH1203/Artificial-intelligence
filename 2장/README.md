# 2. The Predicate Calculus -Luger-
#### 목차
> 0. [Introduction](#introduction)
> 1. [The Propositional Calculus](#the-propositional-calculus)
> 2. [The Predicate Calculus](#the-predicate-calculus)
> 3. [Using Inference Rules to Produce Predicate Calculus Expressions](#using-inference-rules-to-produce-predicate-calculus-expressions)
> 4. [Application: A Logic-Based Financial Advisor](#application-a-logic-Based-financial-advisor)

---

## Introduction
- 컴퓨터에서 지식을 표현하고 다루는 수단으로서의 논리의 응용은 1960년대 초기부터 시작
- 지식 표현의 수단으로 논리가 응용된 이유
  - 자연 언어로 표기된 사실을 술어 논리로 표현 가능
  - 논리는 추론을 할 수 있는 형식적 접근 방법 제공 -> 추론 과정의 기계화, 자동화 가능
  - 자연 언어로 나타낼 수 있는 개념은 술어 논리하에서 기호적 표현으로 번역이 가능하며 기호적 표현으로 나타낸 개념들은 프로그램에 의하여 조작되어 새로운 사실의 유도 가능

---

## The Propositional Calculus
### 명제 논리(Propositional Logic)
#### 명제(Proposition)
- 기본적, 원자적 문장
- (ex) "눈은 희다", "사람이 지구에 산다", "비가 온다", ...
#### 명제 논리의 기호(Symbols)
- 명제 기호(propositional symbols)
  - 명제를 지칭
  - P, Q, R, S, T, ...
- 진리 기호(truth symbols)
  - true, false
- 논리 연산자(connectives)
  - ¬, ∧, ∨, ⇒, =
#### 복합 명제(Compound proposition)
- 여러 개의 단일 명제와 논리 연산자들로 구성
- (ex) "비가 내린다"라는 명제를 R, "바람이 분다"를 W로 표기하면 R ∧ W, R ∨ W, R ⇒ W 세 가지 방법으로 표기할 수 있다.
  - R ∧ W : 비가 내리고 바람이 분다.
  - R ∨ W : 비가 내리거나 바람이 분다.
  - R ⇒ W : 비가 내리면 바람이 분다.
#### 명제 논리에서의 문장(Sentences)
- 모든 명제 기호와 진리 기호 true, false는 문장
- P와 Q가 문장이면, ¬P, P ∧ Q, P ∨ Q, P ⇒ Q, P = Q도 문장
- (ex) (¬P ∨ (Q ∧ P) ⇒ (Q ⇒ W))
#### 명제 논리의 의미론(Semantics)
- 해석(interpretation) : 각 명제 기호에 참값과 거짓값을 할당하는 것
- 어떤 문장의 의미는 그 문장의 진위, 즉 참 또는 거짓
- 어의 규칙 : '참'일 때 'T', '거짓'일 때 'F'로 표기하면
  - ¬P : P가 T면 F, P가 F면 T
  - P ∧ Q : P와 Q가 T일 때만 T, 나머지의 경우에는 F
  - P ∨ Q : P와 Q가 F일 때만 F, 나머지의 경우에는 T
  - P ⇒ Q : P가 T이고 Q가 F일 때만 F, 나머지의 경우에는 T
  - s<sub>1</sub> = s<sub>2</sub> : 문장 s<sub>1</sub>, s<sub>2</sub>가 모든 해석에 대해 같은 진리 값을 가질 경우 T
#### 등가규칙(Equivalence law)
- ¬(¬P) = P
- (P ∨ Q) = (¬P ⇒ Q)
- 드모르간의 법칙(de Morgan's law)
  - ¬(P ∨ Q) = ¬P ∧ ¬Q
  - ¬(P ∧ Q) = ¬P ∨ ¬Q
- 교환 법칙(the commutative law)
  - P ∧ Q = Q ∧ P
  - P ∨ Q = Q ∨ P
- 결합 법칙(the associative law)
  - ((P ∧ Q)∧ R) = (P ∧(Q ∧ R))
  - ((P ∨ Q)∨ R) = (P ∨(Q ∨ R))
- 분배 법칙(the distributive law)
  - P ∧ (Q ∨ R) = (P ∧ Q) ∨ (P ∧ R)
  - P ∨ (Q ∧ R) = (P ∨ Q) ∧ (P ∨ R)
#### 진리표(truth table)
| P | Q | P ∧ Q | P ∨ Q | P ⇒ Q |
|:---:|:---:|:---:|:---:|:---:|
| T | T | T | T | T |
| T | F | F | T | F |
| F | T | F | T | T |
| F | F | F | F | T |

---

## The Predicate Calculus
### 술어 논리(Predicate Logic)
#### 1차 술어 논리(First Order Predicate Logic: FOPL)
- 논리학자들이 명제 논리의 표현력 확대를 위해 개발
- 잘 정의된 의미론과 정당하고 완전한 추론 규칙들로 인해 인공지능 분야에서 표현 언어로 활용됨
#### 술어 논리에서의 기호(Symbols)
- 더 이상 단순화할 수 없는 구문적 요소
- 문자로 시작하는 문자열 '\_' 사용 가능
- 올바른 기호
  - George, fire3, tom_and_jerry, bill, X, XXX, friends_of
- 잘못된 기호
  - 3jack, "no blanks allowed", ab%cd, \*\*\*71, duck!!!
- 기호는 술어 논리로 표현하고자 하는 세계에 존재하는 객체(objects), 객체의 속성(properties), 객체 사이의 관계(relations) 등을 나타냄
#### 기호의 분류
##### 상수 기호(constant symbol)
- 표현하고자 하는 세계에 존재하는 특정 객체나 속성을 나타내며 소문자로 시작함
- (ex) george, tree, tall, red, blue, rose, ...
- 진리 기호(truth symbol) : true, false
##### 변수 기호(variable symbol)
- 임의의 객체나 속성을 지칭하는데 사용하며 대문자로 시작
- (ex) George, Color, Flower, BILL, X, Y, Xxx
##### 함수 기호(function symbol)
- 정의역(domain)내의 하나 이상의 객체로부터 치역(range)내의 하나의 객체로 사상(mapping)하는 함수를 나타냄. 소문자로 시작
- (ex) father\_of(abel), mother\_of(X), color\_of(rose)
##### 술어 기호(predicate symbol)
- 표현하고자 하는 세계의 객체 사이에 존재하는 관계, 객체의 속성 등을 나타냄. 소문자로 시작
#### 함수식(function expression)
- function\_name(term<sub>1</sub>, term<sub>2</sub>, ..., term<sub>n</sub>)
- 항(term) : 상수, 변수, 함수식
- 정의역 내의 하나 이상의 객체로부터 치역 내의 하나의 객체로 사상
  - (ex) father(david), price(bananas), plus(2, 3), f(X, Y)
#### 원자적 문장(atomic sentence, atomic expression, atom, proposition)
- predicate(term<sub>1</sub>, term<sub>2</sub>, ..., term<sub>n</sub>)
- 정의역의 원소로부터 참 또는 거짓 값으로 사상되는 관계를 나타냄
  - (ex) likes(george, kate), likes(george, susie, tuesday), friends(bill, richard), friends(father(david), father(andrew))
- 이름이 같아도 항의 수가 다르면 다른 것으로 간주됨
- 진리값 true와 false도 원자적 문장
#### 변수에 대한 한정사(quantifiers) ∀ and ∃
- 전체 한정사(universal quantifier) ∀ : 모든(all)의 의미
- 존재 한정사(existential quantifier) ∃ : 어떤(some)의 의미
- (ex) ∃Y friends(Y, peter), ∀X likes(X, ice\_cream)
#### 술어 논리에서의 문장(Sentences)
- 모든 원자적 문장은 문장
- 논리 연산자(¬, ∧, ∨, ⇒, =)와 원자적 문장을 조합하여 새로운 문장을 만들 수 있음
  - s가 문장이면 ¬s도 문장
  - s<sub>1</sub>과 s<sub>2</sub>가 문장이면 s<sub>1</sub> ∧ s<sub>2</sub>, s<sub>1</sub> ∨ s<sub>2</sub>, s<sub>1</sub> ⇒ s<sub>2</sub>, s<sub>1</sub> = s<sub>2</sub>도 문장
  - X가 변수이고 s가 문장이면 ∀X<sub>s</sub>와 ∃X<sub>s</sub>도 문장
##### Examples of English sentences represented in predicate calculus
- If it doesn’t rain tomorrow, Tom will go to the mountains.
  - ¬weather(rain, tomorrow) ⇒ go(tom, mountains)
- Emma is a Doberman pinscher and a good dog.
  - gooddog(emma) ∧ isa(emma, doberman)
- All basketball players are tall.
  - ∀X (basketball_player(X) ⇒ tall(X))
- Some people like anchovies.
  - ∃X (person(X) ∧ likes(X, anchovies))
- Nobody likes taxes.
  - ¬∃X likes(X, taxes)
- There is no unique mapping of sentences into predicate calculus expressions.
#### 1차 술어 논리로 표현한 예
- e(X) : X가 피고용인
- p(X) : X가 사장
- i(X) : X의 수입을 반환하는 함수
- ge(U, V) : U가 V보다 크거나 같음
- s(X) : X가 오늘 병가 중임
- t(X) : X가 세금을 냄
- 100만원 이상의 수입이 있는 피고용인은 세금을 낸다.
  - ∀X((e(X) ∧ ge(i(X), 100만원)) ⇒ t(X))
- 어떤 피고용인은 오늘 병가중이다.
  - ∃Y(e(Y) ⇒ s(Y))
- 어떤 피고용인의 수입도 사장보다 많지는 않다.
  - ∀X∀Y((e(X) ∧ p(Y)) ⇒ ¬ge(i(X),i(Y)))
#### A set of family relationships in a biblical genealogy
- mother(eve, abel)
- mother(eve, cain)
- father(adam, abel)
- father(adam, cain)
- ∀X∀Y father(X, Y) ∨ mother(X, Y) ⇒ parent(X, Y)
- ∀X∀Y∀Z father(X, Y) ∧ parent(Y, Z) ⇒ grandfather(X, Z)
#### A blocks world with its predicate calculus desciption
![image](https://user-images.githubusercontent.com/57928612/110585977-ca1e1e80-81b4-11eb-8e15-6c1d679acb4e.png)

- ∀X∀Y((hand_empty ∧ clear(X) ∧ clear(Y) ∧ pick_up(X) ∧ put_down(X,Y)) ⇒ stack (X,Y))
#### 정의역 D에서의 해석(interpretation)
- 정의역 D 내의 객체를 논리식의 상수, 변수, 함수, 술어에 할당하는 것
- 상수에는 D 내의 객체
- 변수에는 D의 부분 집합
- m개의 항을 갖는 함수 f는 D<sup>m</sup>에서 D로의 사상
- n개의 항을 갖는 술어는 D<sup>n</sup>으로부터 { T, F }으로의 사상
#### 주어진 해석 I 하에서 정형식의 의미는 I 하에서의 그 정형식의 진위
#### 정형식(well-formed expression, 또는 문장)의 진리값(truth value)
- 정형식의 진리 값은 상수, 변수, 함수, 술어와 논의 세계의 정의역 D에 존재하는 객체, 관계와의 사상에 따라 결정됨
- 정의역 D에 존재하는 관계의 진위 여부가 상응되는 정형식의 진위를 결정
- friends(george, susie), friends(george, kate), friends(father(george), father(susie))
#### Blocks world
![image](https://user-images.githubusercontent.com/57928612/110586488-aa3b2a80-81b5-11eb-8cae-fbbeab293e1b.png)
#### Family relationships in a biblical genealogy
- mother(eve, cain)
- mother(eve, adam)
#### 정의역 D와 해석 I 하에서 정규식 E의 진리값 결정 규칙
- 진리 기호 : true는 T, false는 F
- 원자적 문장은 T 또는 F로 결정됨
- ¬s, s<sub>1</sub> ∧ s<sub>2</sub>, s<sub>1</sub> ∨ s<sub>2</sub>의 진리값
- s<sub>1</sub> ⇒ s<sub>2</sub>의 진리값 : s<sub>1</sub>이 T이고 s<sub>2</sub>가 F이면 F, 그 밖의 경우에는 T
- s<sub>1</sub> = s<sub>2</sub>의 진리값 : 모든 가능한 해석에 대해 s<sub>1</sub>과 s<sub>2</sub>가 같은 진리값을 가지면 T, 그렇지 않으면 F
- ∀X<sub>s</sub>의 진리값 : X에 대한 모든 가능한 경우에 대해 T이면 T, 그렇지 않으면 F
- ∃X<sub>s</sub>의 진리값 : s를 T로 하는 X가 있으면 T, 그렇지 않으면 F
- (ex) ¬on(c,a), on(c,a) ∧ on(b,a), on(c,a) ∨ on(b,a), on(c,a) ⇒ clear(a), ∀X cosc3(X) ⇒ reg(X,db), ∃X cosc3(X) ⇒ likes(X,ice\_cream)
#### 변수와 한정(quantification)의 영역
- ∀X(p(X) ∧ q(Y) ⇒ r(X))
- ∃X p(X) = ∃Y p(Y)
- ∀X q(X) = ∀Y q(Y)
- ∀X(p(X) ∧ q(X)) = ∀X p(X) ∧ ∀Y q(Y)
- ∃X(p(X) ∨ q(X)) = ∃X p(X) ∨ ∃Y q(Y)
#### 부정과 한정사와의 관계
- ¬∃X p(X) = ∀X ¬p(X)
- ¬∀X p(X) = ∃X ¬p(X)
#### First-order Predicate Calculus
- First-order predicate calculus allows quantified variables to refer to objects in the domain of discourse and not to predicates or functions
- (ex) ∀(Likes) Likes(george, kate)

---

## Using Inference Rules to Produce Predicate Calculus Expressions
### 술어 논리의 중요한 특징
- 술어 논리로 표현된 주어진 사실로부터 기계적, 계산적 조작 과정을 통해 새로운 사실을 추론해낼 수 있는 추론 규칙이 존재하는 것은 술어 논리의 중요한 특징 중 하나
  - 추론 규칙을 이용하여 주어진 사실이 참(true)이란 가정 하에 항상 참이 되는 새로운 사실의 도출이 가능
  - 인공지능 분야에서 지식 표현의 수단으로 술어논리를 이용하게 된 주된 이유 중 하나
### "만족시키다(satisfy)"와 "논리적 귀결(logically follow)"
- 어떤 해석 I 하에서 술어 논리식 S가 참이면 "해석 I는 S를 만족시킨다(satisfy)"고 함
- 술어논리식의 집합 S를 만족시키는 모든 해석이 술어논리식 X를 만족시키면 "X는 S의 논리적 귀결(logically follow)"
- (ex) P ∧ Q가 참이 되는 모든 해석에 대해 P도 참 -> P는 P ∧ Q의 논리적 귀결
### 추론 규칙(inference rules)
- 주어진 문장의 집합으로부터 기계적, 계산적 과정을 통해 새로운 문장을 도출해낼 수 있는 규칙
- 긍정논법(modus ponens) : P와 P ⇒ Q로부터 Q를 추론
- 부정논법(modus tollens) : P ⇒ Q와 ¬Q로부터 ¬P를 추론
- 'and' 제거('and' elimination) : P ∧ Q가 참이면 P와 Q도 참
- 'and' 도입('and' introduction) : P와 Q가 참이면 P ∧ Q도 참
- 전체 사례화(universal instantiation)
  - 참인 문장 내의 전체 한정된 변수를 정의역 내의 적절한 항으로 교체하여 얻어지는 문장은 참
  - 즉, a가 X의 정의역에 속하면 ∀X p(X)로부터 p(a)를 추론할 수 있다.
#### 긍정논법(modus ponens)과 전체 사례화(universal instantiation)의 적용 예시
- P : "it is raining", Q : "the ground is wet"
  - from P, P ⇒ Q, we can infer Q
- "All men are mortal" : ∀X(man(X) ⇒ mortal(X))
  - "Socrates is a man" : man(socrates)
  - universal instantiation let us infer man(socrates) ⇒ mortal(socrates)
  - modus ponens let us infer mortal(socrates)
### A set of family relationships in a biblical genealogy
- mother(eve, abel)
- mother(eve, cain)
- father(adam, abel)
- father(adam, cain)
- ∀X∀Y father(X,Y) ∨ mother(X,Y) ⇒ parent(X,Y)
- ∀X∀Y∀Z father(X,Y) ∧ parent(Y,Z) ⇒ grandfather(X,Z)
- ∀X∀Y∀Z mother(X,Y) ∧ parent(Y,Z) ⇒ grandmother(X,Z)
- ∀X∀Y father(X,Y) ⇒ parent(X,Y)
  - {adam/X, abel/Y}
  - father(adam, abel) ⇒ parent(adam, abel)
- ∀X∀Y mother(X,Y) ⇒ parent(X,Y)
### 추론규칙을 적용하여 새로운 문장을 도출해내는 예시
- mother(eve, abel)
- mother(eve, cain)
- father(adam, abel)
- father(adam, cain)
- father(abel, mary)
- ∀X∀Y father(X,Y) ∨ mother(X,Y) ⇒ parent(X,Y)
- ∀X∀Y∀Z father(X,Y) ∧ parent(Y,Z) ⇒ grandfather(X,Z)
- ∀X∀Y∀Z mother(X,Y) ∧ parent(Y,Z) ⇒ grandmother(X,Z)
- grandfather(adam, mary)의 추론과정
  - ∀X∀Y father(X,Y) ⇒ parent(X,Y)
    - {abel/X, mary/Y}
    - father(abel, mary) ⇒ parent(abel, mary)
  - ∀X∀Y∀Z father(X,Y) ∧ parent(Y,Z) ⇒ grandfather(X,Z)
    - {adam/X, abel/Y, mary/Z}
    - father(adam, abel) ∧ parent(abel, mary) ⇒ grandfather(adam, mary)
### 논리적 정당성(soundness)과 완전성(completeness)
- S를 공리들의 집합, L을 추론 규칙들의 집합이라고 할 때 S로부터 L을 이용하여 유도될 수 있는 모든 문장이 S의 논리적 귀결이면 추론 규칙 L을 논리적으로 정당(sound)하다고 한다.
- S의 논리적 귀결이 되는 모든 문장을 L을 이용하여 유도할 수 있다면 추론 규칙 L을 논리적으로 완전(complete)하다고 한다.
- 논리적 정당성과 완전성은 추론 규칙이 갖고 있어야 할 중요한 성질
### 단일화(unification)
- 두 개의 논리식이 일치하도록 하기 위해 필요한 대체를 결정하는 것
- 단일화(unification) 알고리즘을 이용하면 주어진 논리적 문장들의 집합으로부터 새로운 사실을 도출해내는 추론 시스템의 구현이 가능
- (ex) ∀X(man(X) ⇒ mortal(X))
  - {socrates/X}
  - man(socrates) ⇒ mortal(socrates)
#### 단일화 과정에서의 주의점
- 상수는 기초 사례 -> 다른 항과 대체 불가
- 단일화 과정에서 변수는 상수, 다른 변수, 함수 등 어떤 항과도 대체가 가능함. 그러나 하나의 변수가 두개 이상의 다른 항과 대체될 수 없음
- 변수는 그 변수를 포함하는 항과 대체될 수 없음
  - (ex) X와 p(X)는 단일화될 수 없음
- 단일화는 가능한한 일반적이어야 함
#### 단일화 과정에서의 복잡성을 줄이기 위해서는 모든 변수는 전체 한정사로 한정되도록 논리식을 변형시키는 것이 필요함
- 존재 한정된 변수를 해당되는 상수로 대체
  - ∃X parent(X,tom) ⇒ parent(bob,tom)
- 스콜렘 함수화
  - ∀X∃Y mother(Y,X) ⇒ ∀X mother(f(X),X)
#### 단일화 예시
```
foo(X,a,goo(Y))
foo(fred,a,goo(Z))    {fred/X, Z/Y}
foo(W,a,goo(jack))    {W/X, jack/Y}
foo(Z,a,goo(moo(Z))   {Z/X, moo(Z)/Y}

parents(X,father(X),mother(bill))
parents(bill,father(bill),Y)    {bill/X, mother(bill)/Y}
```
#### Examples of predicate calculus expressions written in list syntax
| PC SYNTAX | LIST SYNTAX |
| --- | --- |
| p(a,b) | (p a b) |
| p(f(a),g(X,Y)) | (p (f a) (g X Y)) |
| equal(eve,mother(cain)) | (equal eve (mother cain)) |
| p(X) ∧ q(Y) | ((p X) ∧ (q Y)) |
#### 단일화 알고리즘
![image](https://user-images.githubusercontent.com/57928612/110591909-f9388e00-81bc-11eb-8bba-0dbe865d8dec.png)
![image](https://user-images.githubusercontent.com/57928612/110591940-02295f80-81bd-11eb-8a79-068370da1d4c.png)
![image](https://user-images.githubusercontent.com/57928612/110591968-0b1a3100-81bd-11eb-8342-07bd00a4277d.png)

---

## Application: A Logic-Based Financial Advisor
### 투자 상담 지침
- People with inadequate savings should make increasing their savings their first priority, regardless of their income.
- People with adequate savings and an adequate income should consider a riskier but potentially more profitable investment in the stock market.
- People with a lower income who already have adequate savings may split their surplus income between savings and stocks.
- Adequate savings is to have at least $5000 in the bank for each dependent.
- An adequate income is steady, at least $15000 per year plus $4000 for each dependent.
### 투자 상담 지침을 술어 논리로 표현하기 위해 사용할 술어, 변수, 상수, 함수
- investment(stocks)
- investment(combination)
- savings_account(adequate)
- savings_account(inadequate)
- income(adequate)
- income(inadequate)
- earnings(X,steady)
- earnings(X,unsteady)
- greater(X,Y)
- amount_saved(X)
- dependents(X)
- minsavings(X) = 5000 \* X
- mimincome(X) = 15000 + 4000 \* X
### 투자 상담 지침을 술어 논리로 표현하기
#### Guideline 1
1. savings_account(inadequate) ⇒ investment(savings)
#### Guideline 2
2. savings_account(adequate) ∧ income(adequate) ⇒ investment(stocks)
#### Guideline 3
3. savings_account(adequate) ∧ income(inadequate) ⇒ investment(combination)
#### Guideline 4
4. amount_saved(X) ∧ (dependents(Y) ∧ greater(X,minsavings(Y))) ⇒ savings_account(adequate)
5. amount_saved(X) ∧ (dependents(Y) ∧ ¬greater(X,minsavings(Y))) ⇒ savings_account(inadequate)
<br>

where minsavings(X) = 5000 \* X
#### Guideline 5
6. earnings(X,steady) ∧ (dependents(Y) ∧ greater(X,minincome(Y))) ⇒ income(adequate)
7. earnings(X,steady) ∧ (dependents(Y) ∧ ¬greater(X,minincome(Y))) ⇒ income(inadequate)
8. earnings(X,unsteady) ⇒ income(inadequate)
<br>

where minincome(X) = 1500 + (4000 \* X)
#### 술어논리 표현
![image](https://user-images.githubusercontent.com/57928612/110593394-d9a26500-81be-11eb-9adc-8d658793a2fd.png)

### 부양가족이 3명, 수입은 매년 일정하게 $25000이고 $22000을 저축한 고객에 대해 투자 상담에 대한 결론을 도출하는 과정
- 고객에 대한 사실 추가
  - \9. amount_saved(22000)
  - \10. earnings(25000,steady)
  - \11. dependents(3)
- 7에 대해 {25000/X, 3/Y}로 대체하고 minincome(3)을 평가한 후 earnings(25000,steady) ∧ (dependents(3) ∧ ¬greater(25000,27000) ⇒ income(inadequate)를 10, 11과 함께 긍정논법을 적용하면 12. income(inadequate) 도출
- 4에 대해 {22000/X, 3/Y}로 대체하고 minsavings(3)을 평가한 후 amount_saved(22000) ∧ (dependents(3) ∧ greater(22000,15000)) ⇒ savings_account(adequate)를 9, 11과 함께 긍정논법을 적용하면 13. savings_account(adequate) 도출
- 3과 12, 13에 대해 긍정논법을 적용하면
  - savings_account(adequate) ∧ income(inadequate) ⇒ investment(combination)

## 요약
- 자연언어 형태의 문장은 1차 술어논리 하에서 술어, 함수, 변수, 상수, 한정자, 논리 연산자 등으로 구성된 기호 구조로 (기호적 표현으로) 번역됨
  - 지식의 기본적 단위를 기호로 표시하고 이러한 기호를 1차 술어논리의 구문 규칙에 따라 조합함으로써 일상의 문장 표현 가능
- 사실이나 절차 혹은 기타 여러 가지 지식을 기호적 문장으로 표현한 후에 추론 규칙을 적용하여 비교하거나, 조합하거나, 변형시키는 등의 방법으로 새로운 사실 생성 -> 자동 추론 가능
