# 생활코딩 db1(개요), 2(MySQL)

목표 학습기간: 2021년 7월 21일 → 2021년 7월 24일
학습주제: 데이터

---
## 목차

* [학습 목표](#학습-목표)
* [DB1: DB개요](#db1_db개요)
    * [db기능이 방대한 이유](#db기능이-방대한-이유)
    * [db 공부할 때 가장 먼저 다뤄야 하는 것](#db-공부할-때-가장-먼저-다뤄야-하는-것)
    * [요약_crud](#요약_crud)
    * [db이해를 위한 예시](#db이해를-위한-예시)
    * [db 판단 기준](#db-판단-기준)
    * [어떤 db언어를 배울 것인가](#어떤-db언어를-배울-것인가)
    * [언어 소개](#언어-소개)
* [db2_My SQL](#db2_My-SQL)
---

## 학습 목표

1. 학습한 공공데이터 감을 잃지 않기 → 최소한의 공부라고 생각하며 감잃지 않기 위해 넣는 인풋
2. db활용 예시 파악
3. db를 가르치는 다른 강사의 다른 시각으로 db의 필요성, 중요성, 활용을 더 폭넓게 이해
---

## db1_db개요

### db기능이 방대한 이유

데이터 관련해서 일어날 수 있는 일이 굉장히 많아서.

### db 공부할 때 가장 먼저 다뤄야 하는 것

### 요약_crud

* 데이터 입력과 출력 방법 먼저 공부! → 데이터의 50%!
    * input : create, update, delete
    * output : read
    * 데이터 관련해서 **crud 외는 복잡하지만, 이 crud를 보좌하는 부가적 기능**이다.
* 따라서, crud 파악 및 익히기가  매우, 가장 중요하다!


### db이해를 위한 예시

1. db X → 윈도우 폴더, 파일
    내가 작가일 경우 작업물을 다루는 방식
    → db 방대한 경우, 원하는 방법을 찾거나, 정렬 방법을 바꾸는 등 활용 및 관리가 어렵다

2. db X (db로 가는 길목) → 스프레드시트
    데이터를 구조적으로 정돈할 수 있다.
    구조를 먼저 작성 : 제목, 본문...(속성 제목으로 쓰이는 애트리뷰트-열- 쓴다고.)
    → 데이터 비교적 자유자재로 정렬, 검색 등 활용 가능


### db 판단 기준

db는 프로그래밍적으로 데이터 crud 가능한 것을 말한다. : **프로그래밍적으로→자동화할 수 있다**는 특징!


### 어떤 db언어를 배울 것인가

1. 소속 직장이나 동료가 쓰는 언어
2. 아직 정해져있지 않다면? : 통계 기반으로.
[database ranking 2021 db-엔진스(링크)](https://db-engines.com/en/ranking)

지금도 db시장 강자는 rdbms(관계형 db모델)이다.
그리고 수업은 2017년인데, 당시 1~4위가 2021년 7월 현재와 일치한다.

3. 관계형dbms 중 하나, 관계형 아닌 것도 하나 공부해보기 → 공통과 차이가 보인다. 공통은 본질!
→**나는 mysql과 몽고db**를 선택한다! 몽고db가 현재 5위이기 때문. 1년전, 1개월전 대비 이용률 성장세이기도 하고.


### 언어 소개

1. 오라클
오랫동안 절대강자.
관공서, 큰 기업에서 쓴다. 비싸서.

2. (얘랑) my sql
무료. 오픈소스.
sns처럼 대규모 데이터가 생성되지만, 데이터 신뢰성이 아주 중요하지는 않은 기업에서는 좋은 서비스.
초심자에게 추천!

3. (얘) 몽고db
**관계형dbms가 아니다.**
*참고로, 2010부터 관계형 아닌 게 쏟아져나옴. *관계형은 70년대부터 썼다고 한다.*

---
---

## db2_My SQL
