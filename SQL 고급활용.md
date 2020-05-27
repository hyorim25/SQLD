# SQL 고급활용  
  
  
### 그룹 함수  
  
1. 데이터 분석 개요  
  
ANSI/ISO SQL 표준은 분석을 위해서 다음 세 가지 함수를 정의하고 있다  
- AGGREGATE FUNCTION
GROUP FUNCTION의 한 부분으로 분류 가능  
COUNT, SUM, AVG, MAX, MIN 외 각종 집계 함수들 포함  
- GROUP FUNCTION  
ROLLUP, CUBE, GROUPING SETS 결과에 대한 정렬 필요하 경우, ORDER BY 절에 정렬 칼럼을 명시
- WINDOW FUNCTION  
데이터 웨어 하우스에서 발전한 기능  
  
2. ROLLUP 함수  
  
Subtotal을 생성하기 위해 사용, Grouping Columns의 수를 N이라고 했을 때 N+1 Level의 Subtotal이 생성, 인수 순서에 주의  
  
3. CUBE 함수  
  
결합 가능한 모든 값에 대하여 다차원 집계를 생성, 시스템에 많은 부담을 주므로 사용에 주의  
  
4. GROUPING SETS 함수  
  
인수들에 대한 개별 집계를 구할 수 있음, 다양한 소계 집합 생성 가능  
  
###  윈도우 함수  
  
윈도우 함수 ? 행과 행간의 관계를 정의하거나 행과 행간을 비교, 연산하는 함수  
  
WINDOW FUNCTION 종류  
  
그룹 내 순위 관련 함수  
- RANK  
- DENSE_RANK  
- ROW_NUMBER  
  
그룹 내 집계 관련 함수  
- SUM  
- MAX  
- MIN  
- AVG  
- COUNT  
  
그룹 내 행 순서 관련 함수  
- FIRST_VALUE  
- LAST_VALUE  
- LAG  
- LEAD  
  
그룹 내 비율 관련 함수  
- CUME_DIST  
- PERCENT_RANK  
- NTILE  
- RATIO_TO_REPORT
  
1. 그룹 내 순위 함수  
  
**RANK 함수**  
  
ORDER BY를 포함한 QUERY문에서 특정 항목에 대한 순위를 구하는 함수  
특정 범위 내에서 순위를 구할 수도 있고 전체 데이터에 대한 순위를 구할 수도 있음  
동일한 값에 대해 동일한 순위 부여  
  
**DENSE_RANK 함수**  
  
RANK 함수와 흡사하나, 동일한 순위를 하나의 건수로 취급하는 것이 틀림  
  
**ROW_NUMBER 함수**  
  
RANK 나 DENSE_RANK 함수가 동일한 값에 대해서는 동일한 순위를 부여하는데 반해, 동일한 값이라도 고유한 순위를 부여함  
  
2. 일반 집계 함수  
  
**SUM 함수**  
  
SUM 함수를 이용해 파티션별 윈도우의 합을 구할 수 있다  
  
**MAX 함수**  
  
MAX 함수를 이용해 파티션별 윈도우의 최대값을 구할 수 있다  
  
**MIN 함수**  
  
MIN 함수를 이용해 파티션별 윈도우의 최소값을 구할 수 있다  
  
**AVG 함수**  
  
AVG 함수 파티션별 ROWS 윈도우를 이용해 원하는 조건에 맞는 데이터에 대한 통계값을 구할 수 있다  
  
**COUNT 함수**  
  
COUNT 함수와 파티션별 ROWS 윈도우를 이용해 원하는 조건에 맞는 데이터에 대한 통계값을 구할 수 있다  
  
3. 그룹 내 행 순서 함수  
  
**FIRST_VALUE 함수**  
  
FIRST_VALUE 함수를 이용해 파티션별 윈도우에서 가장 먼저 나온 값을 구함  
  
**LAST_VALUE 함수**  
  
LAST_VALUE 함수를 이용해 파티션별 윈도우에서 가장 나중에 나온 값을 구함  
  
**LAG 함수**  
  
LAG 함수를 이용해 파티션별 윈도우에서 이전 몇 번째 행의 값을 가져올 수 있음  
  
**LEAD 함수**  
LEAD 함수를 이용해 파티션별 윈도우에서 이후 몇 번째 행의 값을 가져올 수 있음  
  
4. 그룹 내 비율 함수  
  
**RATIO_TO_REPORT 함수**  
  
RATIO_TO_REPORT 함수를 이용해 파티션 내 전체 SUM값에 대한 행별 칼럼 값의 백분율을 소수점 구할 수 있음, 결과 값은 > 0 & < = 1 의 범위를 가짐  
  
**PERCENT_RANK 함수**  
  
PERCENT_RANK 함수를 이용해 파티션별 윈도우에서 제일 먼저 나오는 것을 0으로, 제일 늦게 나오는 것을 1로 하여, 값이 아닌 행의 순서별 백분율을 구함, 결과 값은 >= 0 & <= 1 의 범위를 가짐  
  
**CUME_DIST 함수**  
  
CUME_DIST 함수를 이용해 파티션별 윈도우의 전체건수에서 현재 행보다 작거나 같은 건수에 대한 누적백분율을 구함, 결과 값은 > 0 & <= 1 의 범위를 가짐  
  
**NTILE 함수**  
  
NTILE 함수를 이용해 파티션별 전체 건수를 ARGUMENT 값으로 N 등분한 결과를 구할 수 있음
  
### DCL  
  
DCL ? 유저 생성하고 권한을 제어할 수 있는 명령어  
  
**ORACLE과 SQL SERVER의 사용자 아키텍처 차이**  
  
ORACLE : 유저를 통해 DB에 접속을 하는 형태, ID와 PW 방식으로 인스턴스에 접속을 하고 그에 해당하는 스키마에 오브젝트 생성 등의 권한을 부여받게 됨  
SQL Server  : 인스턴스에 접속하기 위해 로그인이라는 것을 생성하게 되며, 인스턴스 내에 존재하는 다수의 DB에 연결하여 작업하기 위해 유저를 생성한 후 로그인과 유저를 매핑해 주어야 한다. WINDOWS 인증 방식과 혼합 모드 방식이 존재함  
  
시스템 권한  : 사용자가 SQL 문을 실행하기 위해 필요한 적절한 권한  
  
GRANT : 권한 부여  
  
REVOKE  : 권한 취소  
  
```
GRANT CREATE USER TO SCOTT;  
CONN SCOTT/TIGER(ID/PW)

CREATE USER PJS IDENTIFIED BY KOREA7;

GRANT CREATE SESSION TO PJS;

GRANT CREATE TABLE TO PJS;

REVOKE CREATE TABLE FROM PJS;
```
  
모든 유저는 각각 자신이 생성한 테이블 외에 다른 유저의 테이블에 접근하려면 해당 테이블에 대한 오브젝트 권한을 소유자로부터 부여받아야 함  
  
ROLE  : 유저에게 알맞은 권한들을 한 번에 부여하기 위해 사용하는 것  
  
```
CREATE ROLE LOGIN_TABLE;

GRANT CREATE TABLE TO LOGIN_TABLE;
DROP USER PJS CASCADE;  
```  
   
CASCADE  : 하위 오브젝트까지 삭제  
  
###  절차형 SQL  
  
절차형 SQL ? SQL문의 연속적인 실행이나 조건에 따른 분기처리를 이용하여 특정 기능을 수행하는 저장 모듈을 생성할 수 있다, Procedure, User Defined Function, Trigger 등이 있음  
  
저장 모듈 ? PL/SQL 문장을 DB 서버에 저장하여 사용자와 애플리케이션 사이에서 공유할 수 있도록 만든 일종의 SQL 컴포넌트 프로그램, 독립적으로 실행되거나 다른 프로그램으로부터 실행될 수 있는 완전한 실행 프로그램  
  
**PL/SQL 특징**  
1. Block 구조로 되어있어 각 기능별로 모듈화 가능  
2. 변수, 상수 등을 선언하여 SQL 문장 간 값을 교환  
3. IF, LOOP 등의 절차형 언어를 사용하여 절차적인 프로그램이 가능하도록 한다  
4. DBMS 정의 에러나 사용자 정의 에러를 정의하여 사용할 수 있다  
5. PL/SQL은 ORACLE에 내장되어 있으므로 호환성 좋음  
6. 응용 프로그램의 성능을 향상시킨다  
7. BLOCK 단위로 처리 -> 통신량을 줄일 수 있다  
  
DECLARE : BEGIN~END 절에서 사용될 변수와 인수에 대한 정의 및 데이터 타입 선언부  
  
BEGIN~END  : 개발자가 처리하고자 하는 SQL문과 여러 가지 비교문, 제어문을 이용 필요한 로직 처리  
  
EXCEPTION  : BEGIN~END 절에서 실행되는 SQL문이 실행될 때 에러가 발생하면 그 에러를 어떻게 처리할지 정의하는 예외 처리부  
  
```
CREATE Procedure Procedure_name  
REPLACE Procedure Procedure_name  
DROP Procedure Procedure_name  
```  
  
T-SQL  : 근본적으로 SQL Server를 제어하는 언어  
  
```
CREATE Procedure schema_NAME.Procedure_name  
```
  
Trigger  : 특정한 테이블에 INSERT, UPDATE, DELETE와 같은 DML문이 수행되었을 때, DB에서 자동으로 동작하도록 작성된 프로그램, 사용자 호출이 아닌 DB 자동 수행  
  
```
CREATE Trigger Trigger_name
```
