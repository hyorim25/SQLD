# 함수
## 1. 내장 함수

#### 1. 함수구분
1) 벤더에서 제공하는 함수인 내장 함수
 >* 단일행 함수:다시 함수의 입력 값이 단일행 값이 입력
 >* 다중행 함수:여러 행의 값이 입력
 >>* 집계 함수
 >>* 그룹 함수 
 >>* 윈도우 함수
2) 사용자가 정의할 수 있는 함수

#####  함수 정의
함수명 (칼럼이나 표현식 [, Arg1, Arg2, ... ])

![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_181.jpg)

#### 함수 특징
- SELECT, WHERE, ORDER BY 절에 사용 가능하다. 
-  각 행(Row)들에 대해 개별적으로 작용하여 데이터 값들을 조작하고, 각각의 행에 대한 조작 결과를 리턴한다. 
- 여러 인자(Argument)를 입력해도 단 하나의 결과만 리턴한다.
- 함수의 인자(Arguments)로 상수, 변수, 표현식이 사용 가능하고, 하나의 인수를 가지는 경우도 있지만 여러 개의 인수를 가질 수도 있다. 
-  특별한 경우가 아니면 함수의 인자(Arguments)로 함수를 사용하는 함수의 중첩이 가능하다.

#### 2.문자형 함수

> 문자형 함수는 문자 데이터를 매개 변수로 받아들여서 문자나 숫자 값의 결과를 돌려주는 함수이다. 

![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_182.jpg)


![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_183.jpg)

#### 3. 숫자형 함수

> 숫자형 함수는 숫자 데이터를 입력받아 처리하고 숫자를 리턴하는 함수이다.

![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_184.jpg)


![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_185.jpg)

#### 4. 날짜형 함수

> 날짜형 함수는 DATE 타입의 값을 연산하는 함수이다. 

* Oracle의 TO_NUMBER(TO_CHAR( )) 함수의 경우 변환형 함수로 구분할 수도 있으나 SQL Server의 YEAR, MONTH,DAY 함수와 매핑하기 위하여 날짜형 함수에서 설명한다. 
*  EXTRACT/DATEPART는 같은 기능을 하는 Oracle 내장 함수와 SQL Server 내장 함수를 표현한 것이다

![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_186.jpg)

* DATE 변수가 데이터베이스에 어떻게 저장되는지 살펴보면,  숫자 형식으로 변환하여 저장한다. (세기, 년, 월, 일, 시, 분, 초)


![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_187.jpg)

#### 5. 변환형 함수

>변환형 함수는 특정 데이터 타입을 다양한 형식으로 출력하고 싶을 경우에 사용되는 함수이다

![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_188.jpg)

* 명시적인 데이터 유형 변환 방법을 사용하는 것이 바람직하다.

* 명시적 데이터 유형 변환에 사용되는 대표적인 변환형 함수
>![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_189.jpg)

>* 변환형 함수를 사용하여 출력 형식을 지정할 때, 숫자형과 날짜형의 경우 상당히 많은 포맷이 벤더별로 제공
>* 벤더별 데이터 유형과 함께 데이터 출력의 포맷 부분은 벤더의 고유 항목이 많으므로 매뉴얼을 참고


#### 6. CASE 표현

> CASE 표현은 IF-THEN-ELSE 논리와 유사한 방식으로 표현식을 작성해서 SQL의 비교 연산 기능을 보완하는 역할을 한다. 

* ANSI/ISO SQL 표준에는 CASE Expression이라고 표시되어 있는데, 함수와 같은 성격을 가지고 있다. 
* Oracle의 Decode 함수와 같은 기능을 하므로 단일행 내장 함수에서 같이 설명을 한다.
* CASE 표현을 하기 위해서는 조건절을 표현하는 두 가지 방법이 있고, Oracle의 경우 DECODE 함수를 사용할 수도 있다.

![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_190.jpg)

* IF-THEN-ELSE 논리를 구현하는 CASE Expressions은 Simple Case Expression과 Searched Case Expression 두 가지 표현법 중에 하나를 선택해서 사용하게 된다.

1) CASE SIMPLE_CASE_EXPRESSION 조건 

> SIMPLE_CASE_EXPRESSION: CASE 다음에 바로 조건에 사용되는 칼럼이나 표현식을 표시하고, 다음 WHEN 절에서 앞에서 정의한 칼럼이나 표현식과 같은지 아닌지 판단하는 문장

> EQUI(=) 조건만 사용한다면, SEARCHED_CASE_EXPRESSION보다 간단하게 사용할 수 있는 장점이 있다. 
Oracle의 DECODE 함수와 기능면에서 동일하다.

>* CASE EXPR WHEN COMPARISON_EXPR THEN RETURN_EXPR ELSE 표현절 END

2) SEARCHED_CASE_EXPRESSION 조건 ELSE 표현절 END

> SEARCHED_CASE_EXPRESSION: CASE 다음에는 칼럼이나 표현식을 표시하지 않는다.
> 다음 WHEN 절에서 EQUI(=) 조건 포함 여러 조건(>, >=, <, <=)을 이용한 조건절을 사용할 수 있기 때문에 SIMPLE_CASE_EXPRESSION보다 훨씬 다양한 조건을 적용할 수 있는 장점이 있다.

>* CASE WHEN CONDITION THEN RETURN_EXPR ELSE 표현절 END

> CASE 표현은 함수의 성질을 가지고 있으므로, 다른 함수처럼 중첩해서 사용할 수 있다

#### 7. NULL 관련 함수

##### 1) NVL/ISNULL 함수

- 널 값은 아직 정의되지 않은 값으로 0 또는 공백과 다르다. 0은 숫자이고, 공백은 하나의 문자이다. 
-  테이블을 생성할 때 NOT NULL 또는 PRIMARY KEY로 정의되지 않은 모든 데이터 유형은 널 값을 포함할 수 있다. 
-  널 값을 포함하는 연산의 경우 결과 값도 널 값이다. 모르는 데이터에 숫자를 더하거나 빼도 결과는 마찬가지로 모르는 데이터인 것과 같다. 
-  결과값을 NULL이 아닌 다른 값을 얻고자 할 때 NVL/ISNULL 함수를 사용한다.

![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_191.jpg)

>Q:칼럼 간 계산을 수행하는 경우 NULL 값이 존재하면 해당 연산 결과가 NULL 값이 되므로 원하는 결과를 얻을 수 없는 경우가 발생하면? 
NVL 함수 연산을 해서 원하는 데이터를 얻는다. 관계형 데이터베이스의 중요한 데이터인 NULL을 처리하는 주요 함수는 다음과 같다.

![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_192.jpg)

*Oracle의 경우 NVL 함수를 사용한다.
 NVL (NULL 판단 대상,‘NULL일 때 대체값’)

*SQL Server의 경우 ISNULL 함수를 사용한다.
ISNULL (NULL 판단 대상,‘NULL일 때 대체값’)

#####  2) NULL과 공집합

-   일반적인 NVL/ISNULL 함수 사용

STEP1. 정상적으로 매니저 정보를 가지고 있는 SCOTT의 매니저를 출력한다.

-   공집합의 NVL/ISNULL 함수 사용

SELECT 1 FROM DUAL WHERE 1 = 2; 와 같은 조건이 대표적인 공집합을 발생시키는 쿼리이며, 위와 같이 조건에 맞는 데이터가 한 건도 없는 경우를 공집합이라고 하고, NULL 데이터와는 또 다르게 이해해야 한다.

STEP1. 공집합을 발생시키기 위해 사원 테이블에 존재하지 않는 'JSC'라는 이름으로 데이터를 검색한다.

>[예제 및 실행 결과] SELECT MGR FROM EMP WHERE ENAME='JSC'; 데이터를 찾을 수 없다. 
☞ EMP 테이블에 ENAME이‘JSC’란 사람은 없으므로 공집합이 발생한다.

STEP2. NVL/ISNULL 함수를 이용해 공집합을 9999로 바꾸고자 시도한다.

>[예제 및 실행 결과] SELECT NVL(MGR, 9999) MGR FROM EMP WHERE ENAME='JSC'; 데이터를 찾을 수 없다. 
☞ 많은 분들이 공집합을 NVL/ISNULL 함수를 이용해서 처리하려고 하는데, 인수의 값이 공집합인 경우는 NVL/ISNULL 함수를 사용해도 역시 공집합이 출력된다.
 ☞ NVL/ISNULL 함수는 NULL 값을 대상으로 다른 값으로 바꾸는 함수이지 공집합을 대상으로 하지 않는다.

STEP3. 적절한 집계 함수를 찾아서 NVL 함수 대신 적용한다.

>[예제 및 실행 결과] SELECT MAX(MGR) MGR FROM EMP WHERE ENAME='JSC'; MGR ----- 1개의 행이 선택되었다. 
☞ 빈 칸으로 표시되었지만 실 데이터는 NULL이다. 
☞ 다른 함수와 달리 집계 함수와 Scalar Subquery의 경우는 인수의 결과 값이 공집합인 경우에도 NULL을 출력한다.

STEP4. 집계 함수를 인수로 한 NVL/ISNULL 함수를 이용해서 공집합인 경우에도 빈칸이 아닌 9999로 출력하게 한다.

>[예제 및 실행 결과] SELECT NVL(MAX(MGR), 9999) MGR FROM EMP WHERE ENAME='JSC'; MGR ----- 9999 1개의 행이 선택되었다. 
>☞ 공집합의 경우는 NVL 함수를 사용해도 공집합이 출력되므로, 그룹함수와 NVL 함수를 같이 사용해서 처리한다.


##### 3) NULLIF

>NULLIF 함수는 EXPR1이 EXPR2와 같으면 NULL을, 같지 않으면 EXPR1을 리턴한다. 특정 값을 NULL로 대체하는 경우에 유용하게 사용할 수 있다.

* NULLIF (EXPR1, EXPR2)

##### 4) 기타 NULL 관련 함수 (COALESCE)

> COALESCE 함수는 인수의 숫자가 한정되어 있지 않으며, 임의의 개수 EXPR에서 NULL이 아닌 최초의 EXPR을 나타낸다. 
> 만일 모든 EXPR이 NULL이라면 NULL을 리턴한다.

* COALESCE (EXPR1, EXPR2, …)
## 2. 집계 함수(Aggregate Function)

#### 집계함수 특성
- 여러 행들의 그룹이 모여서 그룹당 단 하나의 결과를 돌려주는 함수이다. 
- - GROUP BY 절은 행들을 소그룹화 한다. 
- - SELECT 절, HAVING 절, ORDER BY 절에 사용할 수 있다.

**집계 함수명 ( [DISTINCT | ALL] 칼럼이나 표현식 )** 
>- ALL : Default 옵션이므로 생략 가능함 
> - DISTINCT : 같은 값을 하나의 데이터로 간주할 때 사용하는 옵션임


![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_193.jpg)

#### 2. GROUP BY 절

>WHERE 절을 통해 조건에 맞는 데이터를 조회했지만 테이블에 1차적으로 존재하는 데이터 이외의 정보
GROUP BY 절은 SQL 문에서 FROM 절과 WHERE 절 뒤에 오며, 데이터들을 작은 그룹으로 분류하여 소그룹에 대한 항목별로 통계 정보를 얻을 때 추가로 사용된다.

#### SELECT [DISTINCT] 칼럼명 [ALIAS명] FROM 테이블명 [WHERE 조건식] [GROUP BY 칼럼(Column)이나 표현식] [HAVING 그룹조건식] ;

GROUP BY 절과 HAVING 절 특성

- GROUP BY 절을 통해 소그룹별 기준을 정한 후, SELECT 절에 집계 함수를 사용한다. 
-  집계 함수의 통계 정보는 NULL 값을 가진 행을 제외하고 수행한다. 
-  GROUP BY 절에서는 SELECT 절과는 달리 ALIAS 명을 사용할 수 없다. 
-  집계 함수는 WHERE 절에는 올 수 없다. (집계 함수를 사용할 수 있는 GROUP BY 절보다 WHERE 절이 먼저 수행된다) 
-  WHERE 절은 전체 데이터를 GROUP으로 나누기 전에 행들을 미리 제거시킨다. 
-  HAVING 절은 GROUP BY 절의 기준 항목이나 소그룹의 집계 함수를 이용한 조건을 표시할 수 있다. 
-  GROUP BY 절에 의한 소그룹별로 만들어진 집계 데이터 중, HAVING 절에서 제한 조건을 두어 조건을 만족하는 내용만 출력한다. 
-  HAVING 절은 일반적으로 GROUP BY 절 뒤에 위치한다.


#### 3. HAVING 절


* GROUP BY 절과 HAVING 절의 순서를 바꾸어서 수행하더라도 문법 에러도 없고 결과물도 동일한 결과를 출력한다. 
* SQL 내용을 보면, 포지션이란 소그룹으로 그룹핑되어 통계 정보가 만들어지고, 이후 적용된 결과 값에 대한 HAVING 절의 제한 조건에 맞는 데이터만을 출력하는 것
 -> GROUP BY 절과 HAVING 절의 순서를 지킨다.

* Q: GROUP BY 소그룹의 데이터 중 일부만 필요한 경우? GROUP BY 연산 전 WHERE 절에서 조건을 적용하여 필요한 데이터만 추출하여 GROUP BY 연산을 하는 방법과, GROUP BY 연산 후 HAVING 절에서 필요한 데이터만 필터링 하는 두 가지 방법을 사용할 수 있다. 


#### 4. CASE 표현을 활용한 월별 데이터 집계

“집계 함수(CASE( ))~GROUP BY” : 모델링의 제1정규화로 인해 반복되는 칼럼의 경우 구분 칼럼을 두고 여러 개의 레코드로 만들어진 집합을, 정해진 칼럼 수만큼 확장해서 집계 보고서를 만드는 유용한 기법이다. 


#### 5. 집계 함수와 NULL

* 리포트의 빈칸을 NULL이 아닌 ZERO로 표현하기 위해 NVL(Oracle)/ISNULL(SQL Server) 함수를 사용하는 경우가 많은데,  NVL 함수를 다중 행 함수 안에 사용할 필요가 없다. 
* 다중 행 함수는 입력 값으로 전체 건수가 NULL 값인 경우만 함수의 결과가 NULL이 나오고 전체 건수 중에서 일부만 NULL인 경우는 NULL인 행을 다중 행 함수의 대상에서 제외한다. 
* 리포트 출력 때 NULL이 아닌 0을 표시하고 싶은 경우에는 NVL(SUM(SAL),0)이나, ISNULL(SUM(SAL),0)처럼 전체 SUM의 결과가 NULL인 경우(대상 건수가 모두 NULL인 경우)에만 한 번 NVL/ISNULL 함수를 사용하면 된다.
* ##  ORDER BY절 정렬

 ####  ORDER BY정렬

* ORDER BY 절은 SQL 문장으로 조회된 데이터들을 다양한 목적에 맞게 특정 칼럼을 기준으로 정렬하여 출력하는데 사용한다. 
*  ORDER BY 절에 칼럼(Column)명 대신에 SELECT 절에서 사용한 ALIAS 명이나 칼럼 순서를 나타내는 정수도 사용 가능하다. 
* 정렬 방식을 지정하지 않으면 기본적으로 오름차순이 적용되며, SQL 문장의 제일 마지막에 위치한다.

#### SELECT 칼럼명 [ALIAS명] FROM 테이블명 [WHERE 조건식] [GROUP BY 칼럼(Column)이나 표현식] [HAVING 그룹조건식] [ORDER BY 칼럼(Column)이나 표현식 [ASC 또는 DESC]] ; 
>ASC(Ascending) : 조회한 데이터를 오름차순으로 정렬한다.(기본 값이므로 생략 가능) 
DESC(Descending) : 조회한 데이터를 내림차순으로 정렬한다.

ORDER BY 절 사용 특징

- 기본적인 정렬 순서는 오름차순(ASC)이다. 
-  숫자형 데이터 타입은 오름차순으로 정렬했을 경우에 가장 작은 값부터 출력된다. 
-  날짜형 데이터 타입은 오름차순으로 정렬했을 경우 날짜 값이 가장 빠른 값이 먼저 출력된다. 
-  Oracle에서는 NULL 값을 가장 큰 값으로 간주하여 오름차순으로 정렬했을 경우에는 가장 마지막에, 내림차순으로 정렬했을 경우에는 가장 먼저 위치한다. 
-  SQL Server에서는 NULL 값을 가장 작은 값으로 간주하여 오름차순으로 정렬했을 경우에는 가장 먼저, 내림차순으로 정렬했을 경우에는 가장 마지막에 위치한다.

Case1. 칼럼명 사용 ORDER BY 절 사용

[예제] SELECT DNAME, LOC, DEPTNO FROM DEPT ORDER BY DNAME, LOC, DEPTNO DESC;

>[실행 결과] DNAME LOC DEPTNO ----------- --------- ------ ACCOUNTING NEW YORK 10 OPERATIONS BOSTON 40 RESEARCH DALLAS 20 SALES CHICAGO 30 4개의 행이 선택되었다.

Case2. 칼럼명 + ALIAS 명 사용 ORDER BY 절 사용

[예제] SELECT DNAME DEPT, LOC AREA, DEPTNO FROM DEPT ORDER BY DNAME, AREA, DEPTNO DESC;

>[실행 결과] DEPT AREA DEPTNO ---------- --------- ------ ACCOUNTING NEW YORK 10 OPERATIONS BOSTON 40 RESEARCH DALLAS 20 SALES CHICAGO 30 4개의 행이 선택되었다.

Case3. 칼럼 순서번호 + ALIAS 명 사용 ORDER BY 절 사용

[예제] SELECT DNAME, LOC AREA, DEPTNO FROM DEPT ORDER BY 1, AREA, 3 DESC;

>[실행 결과] DNAME AREA DEPTNO ----------- ---------- ------ ACCOUNTING NEW YORK 10 OPERATIONS BOSTON 40 RESEARCH DALLAS 20 SALES CHICAGO 30 4개의 행이 선택되었다.

#### 2. SELECT 문장 실행 순서

GROUP BY 절과 ORDER BY가 같이 사용될 때 SELECT 문장은 6개의 절로 구성이 되고, SELECT 문장의 수행 단계는 아래와 같다.

1. SELECT 칼럼명 [ALIAS명]
 1. FROM 테이블명 
 2. WHERE 조건식 
 3.  GROUP BY 칼럼(Column)이나 표현식 
 4.  HAVING 그룹조건식 
 5.  ORDER BY 칼럼(Column)이나 표현식

 1.발췌 대상 테이블을 참조한다. (FROM) 
 2. 발췌 대상 데이터가 아닌 것은 제거한다. (WHERE) 
 3. 행들을 소그룹화 한다. (GROUP BY) 
 4.  그룹핑된 값의 조건에 맞는 것만을 출력한다. (HAVING) 
 5.  데이터 값을 출력/계산한다. (SELECT) 
 6. 데이터를 정렬한다. (ORDER BY)


[예제] SELECT 절에 없는 EMP 칼럼을 ORDER BY 절에 사용한다.

[예제] SELECT EMPNO, ENAME FROM EMP ORDER BY MGR;

>[실행 결과] EMPNO ENAME ----- ------- 7902 FORD 7788 SCOTT 7900 JAMES 7499 ALLEN 7521 WARD 7844 TURNER 7654 MARTIN 7934 MILLER 7876 ADAMS 7698 BLAKE 7566 JONES 7782 CLARK 7369 SMITH 7839 KING 14개의 행이 선택되었다.

* 실행 결과에서 ORDER BY 절에서 SELECT 절에서 정의하지 않은 칼럼을 사용해도 문제없음을 확인할 수 있다.

[예제] 인라인 뷰에 정의된 SELECT 칼럼을 메인쿼리에서 사용한다.

>[예제 및 실행 결과] SELECT EMPNO FROM (SELECT EMPNO, ENAME FROM EMP ORDER BY MGR); 14개의 행이 선택되었다.

* 실행 결과에서 2장에서 배울 인라인 뷰의 SELECT 절에서 정의한 칼럼은 메인쿼리에서도 사용할 수 있는 것을 확인할 수 있다.

[예제] 인라인 뷰에 미정의된 칼럼을 메인쿼리에서 사용해본다.

> [예제 및 실행 결과] SELECT MGR FROM (SELECT EMPNO, ENAME FROM EMP ORDER BY MGR); SELECT MGR FROM ; * ERROR: "MGR": 부적합한 식별자

* GROUP BY 이후 수행 절인 SELECT 절이나 ORDER BY 절에서 개별 데이터를 사용하는 경우 에러가 발생한다. 
결과적으로 SELECT 절에서는 그룹핑 기준과 숫자 형식 칼럼의 집계 함수를 사용할 수 있지만, 그룹핑 기준 외의 문자 형식 칼럼은 정할 수 없다.

[예제] GROUP BY 절 사용시 SELECT 절에 일반 칼럼을 사용해본다.

> [예제 및 실행 결과] SELECT JOB, SAL FROM EMP GROUP BY JOB HAVING COUNT(*) > 0 ORDER BY SAL; SELECT JOB, SAL ; * ERROR: GROUP BY 표현식이 아니다.

[예제] GROUP BY 절 사용시 ORDER BY 절에 일반 칼럼을 사용해본다.

> [예제 및 실행 결과] SELECT JOB FROM EMP GROUP BY JOB HAVING COUNT(*) > 0 ORDER BY SAL; ORDER BY SAL; * ERROR: GROUP BY 표현식이 아니다.

[예제] GROUP BY 절 사용시 ORDER BY 절에 집계 칼럼을 사용해본다.

[예제] SELECT JOB FROM EMP GROUP BY JOB HAVING COUNT(*) > 0 ORDER BY MAX(EMPNO), MAX(MGR), SUM(SAL), COUNT(DEPTNO), MAX(HIREDATE);

>[실행 결과] JOB --------- MANAGER PRESIDENT SALESMAN ANALYST CLERK 5개의 행이 선택되었다.

* SELECT SQL에서 GROUP BY 절이 사용되었기 때문에 SELECT 절에 정의하지 않은 MAX, SUM, COUNT 집계 함수도 ORDER BY 절에서 사용할 수 있는 것을 실행 결과에서 확인할 수 있다.

#### 3. Top N 쿼리

-   ROWNUM

Oracle에서 순위가 높은 N개의 로우를 추출하기 위해 ORDER BY 절과 WHERE 절의 ROWNUM 조건을 같이 사용하는 경우가 있는데 이 두 조건으로는 원하는 결과를 얻을 수 없다.

[예제] 사원 테이블에서 급여가 높은 3명만 내림차순으로 출력하고자 하는데, 잘못 사용된 SQL의 사례이다.

[예제] SELECT ENAME, SAL FROM EMP WHERE ROWNUM < 4 ORDER BY SAL DESC;

>[실행 결과] ENAME SAL ------ ---- ALLEN 1600 WARD 1250 SMITH 800 3개의 행이 선택되었다.

실행 결과의 3명은 급여가 상위인 3명을 출력한 것이 아니라, 급여 순서에 상관없이 무작위로 추출된 3명에 한해서 급여를 내림차순으로 정렬한 결과이므로 원하는 결과를 출력한 것이 아니다.


-   TOP ( )

반면 SQL Server는 TOP 조건을 사용하게 되면 별도 처리 없이 관련 Order By 절의 데이터 정렬 후 원하는 일부 데이터만 쉽게 출력할 수 있다.

TOP (Expression) [PERCENT] [WITH TIES]

* TOP 절을 사용하여 결과 집합으로 반환되는 행 수를 제한할 수 있다. 
* WITH TIES 옵션은 ORDER BY 절의 조건 기준으로 TOP N의 마지막 행으로 표시되는 추가 행의 데이터가 같을 경우 N+ 동일 정렬 순서 데이터를 추가 반환하도록 지정하는 옵션이다.

[예제] 사원 테이블에서 급여가 높은 2명을 내림차순으로 출력하고자 한다.

[예제] SELECT TOP(2) ENAME, SAL FROM EMP ORDER BY SAL DESC;

>[실행 결과] ENAME SAL ------ ---- KING 5000 SCOTT 3000 2개의 행이 선택되었다.

[예제] 사원 테이블에서 급여가 높은 2명을 내림차순으로 출력하는데 같은 급여를 받는 사원이 있으면 같이 출력한다.

[예제] SELECT TOP(2) WITH TIES ENAME, SAL FROM EMP ORDER BY SAL DESC;

>[실행 결과] ENAME SAL ----- --- KING 5000 SCOTT 3000 FORD 3000 3개의 행이 선택되었다.

TOP(2) WITH TIES 옵션은 동일 수치의 데이터를 추가로 더 추출하는 것으로, SCOTT과 FORD의 급여가 공동 2위이므로 TOP(2) WITH TIES의 실행 결과는 3건의 데이터가 출력된다.

## JOIN 

두 개 이상의 테이블 들을 연결 또는 결합하여 데이터를 출력하는 것을 JOIN이라고 한다.

#### 1. EQUI JOIN

EQUI(등가) JOIN: 두 개의 테이블 간에 칼럼 값들이 서로 정확하게 일치하는 경우에 사용되는 방법으로 대부분 PK ↔ FK의 관계를 기반으로 한다. 
그러나 일반적으로 테이블 설계 시에 나타난 PK ↔ FK의 관계를 이용하는 것이지 반드시 PK ↔ FK의 관계로만 EQUI JOIN이 성립하는 것은 아니다. 

SELECT 테이블1.칼럼명, 테이블2.칼럼명, ... FROM 테이블1, 테이블2 WHERE 테이블1.칼럼명1 = 테이블2.칼럼명2; → WHERE 절에 JOIN 조건을 넣는다.

같은 내용을 ANSI/ISO SQL 표준 방식으로 표현하면 아래와 같다.

SELECT 테이블1.칼럼명, 테이블2.칼럼명, ... FROM 테이블1 INNER JOIN 테이블2 ON 테이블1.칼럼명1 = 테이블2.칼럼명2; → ON 절에 JOIN 조건을 넣는다.

[예제] 선수 테이블과 팀 테이블에서 선수 이름과 소속된 팀의 이름을 출력하시오.

>[예제] SELECT PLAYER.PLAYER_NAME 선수명, TEAM.TEAM_NAME 소속팀명 FROM PLAYER, TEAM WHERE PLAYER.TEAM_ID = TEAM.TEAM_ID; 
>또는 INNER JOIN을 명시하여 사용할 수도 있다.
> SELECT PLAYER.PLAYER_NAME 선수명, TEAM.TEAM_NAME 소속팀명 FROM PLAYER INNER JOIN TEAM ON PLAYER.TEAM_ID = TEAM.TEAM_ID;

#### 2. Non EQUI JOIN

* Non EQUI(비등가) JOIN은 두 개의 테이블 간에 칼럼 값들이 서로 정확하게 일치하지 않는 경우에 사용된다.
* Non EQUI JOIN의 경우에는 “=” 연산자가 아닌 다른(Between, >, >=, <, <= 등) 연산자들을 사용하여 JOIN을 수행하는 것이다. 
* 두 개의 테이블이 PK-FK로 연관관계를 가지거나 논리적으로 같은 값이 존재하는 경우에는 “=” 연산자를 이용하여 EQUI JOIN을 사용한다. 
 * 두 개의 테이블 간에 칼럼 값들이 서로 정확하게 일치하지 않는 경우에는 EQUI JOIN을 사용할 수 없다. 
#### SELECT 테이블1.칼럼명, 테이블2.칼럼명, ... FROM 테이블1, 테이블2 WHERE 테이블1.칼럼명1 BETWEEN 테이블2.칼럼명1 AND 테이블2.칼럼명2;


#### 3. 3개 이상 TABLE JOIN
선수 테이블, 팀 테이블, 운동장 테이블을 예로 들었을때, 선수들 별로 홈그라운드 경기장이 어디인지를 출력하고 싶다고 했을 때, 선수 테이블과 운동장 테이블이 서로 관계가 없으므로 중간에 팀 테이블이라는 서로 연관관계가 있는 테이블을 추가해서 세 개의 테이블을 JOIN 해야만 원하는 데이터를 얻을 수 있다.

[예제] 앞의 예제에서 보았듯이 선수 테이블의 소속팀코드(TEAM_ID)가 팀 테이블의 팀코드(TEAM_ID)와 PK-FK의 관계가 있다는 것을 알 수 있고, 운동장 테이블의 운동장코드(STADIUM_ID)와 팀 테이블의 전용구장코드(STADIUM_ID)가 PK-FK 관계인 것을 생각하며 다음 SQL을 작성한다. 세 개의 테이블에 대한 JOIN이므로 WHERE 절에 2개 이상의 JOIN 조건이 필요하다.

[예제] [예제] SELECT P.PLAYER_NAME 선수명, P.POSITION 포지션, T.REGION_NAME 연고지, T.TEAM_NAME 팀명, S.STADIUM_NAME 구장명 FROM PLAYER P, TEAM T, STADIUM S WHERE P.TEAM_ID = T.TEAM_ID AND T.STADIUM_ID = S.STADIUM_ID ORDER BY 선수명; 또는 INNER JOIN을 명시하여 사용할 수도 있다. SELECT P.PLAYER_NAME 선수명, P.POSITION 포지션, T.REGION_NAME 연고지, T.TEAM_NAME 팀명, S.STADIUM_NAME 구장명 FROM PLAYER P INNER JOIN TEAM T ON P.TEAM_ID = T.TEAM_ID INNER JOIN STADIUM S ON T.STADIUM_ID = S.STADIUM_ID ORDER BY 선수명;

>[실행 결과] 선수명 포지션 연고지 팀명 구장명 ------ ----- ----- --------- ------------- 가비 MF 수원 삼성블루윙즈 수원월드컵경기장 가이모토 DF 성남 일화천마 성남종합운동장 강대희 MF 수원 삼성블루윙즈 수원월드컵경기장 강성일 GK 대전 시티즌 대전월드컵경기장 강용 DF 포항 스틸러스 포항스틸야드 강정훈 MF 대전 시티즌 대전월드컵경기장 강철 DF 전남 드래곤즈 광양전용경기장 고관영 MF 전북 현대모터스 전주월드컵경기장 고규억 DF 광주 광주상무 광주월드컵경기장 고민기 FW 전북 현대모터스 전주월드컵경기장 고병운 DF 포항 스틸러스 포항스틸야드 고종수 MF 수원 삼성블루윙즈 수원월드컵경기장 고창현 MF 수원 삼성블루윙즈 수원월드컵경기장 공오균 MF 대전 시티즌 대전월드컵경기장 곽경근 FW 인천 유나이티드 인천월드컵경기장 곽기훈 FW 울산 울산현대 울산문수경기장 곽기훈 FW 울산 울산현대 울산문수경기장 곽치국 MF 성남 일화천마 성남종합운동장 … … … … … 480개의 행이 선택되었다.
