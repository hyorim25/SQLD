# SQL_활용
## 1. 관계형 데이터베이스

* 메타 데이터를 총괄 관리할 수 있기 때문에 데이터의 성격, 속성 또는 표현 방법 등을 체계화할 수 있ㅇ
* 데이터 표준화를 통한 데이터 품질을 확보할 수 ㅇ
* DBMS는 인증된 사용자만이 참조할 수 있도록 보안 기능을 제공
* 테이블 생성 시에 사용할 수 있는 다양한 제약조건을 이용하여 사용자가 실수로 조건에 위배되는 데이터를 입력한다든지, 관계를 연결하는 중요 데이터를 삭제하는 것을 방지-> 데이터 무결성보장할 수 ㅇ  
*  DBMS는 시스템의 갑작스런 장애로부터 사용자가 입력, 수정, 삭제하던 데이터가 제대로 반영될 수 있도록 보장해주는 기능과, 시스템 다운, 재해 등의 상황에서도 데이터를 회복/복구할 수 있는 기능을 제공
## 2. SQL
![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_148.jpg)
* SQL 문장과 관련된 용어 중에서 먼저 테이블에 대한 내용은 건드리지 않고 단순히 조회를 하는 SELECT 문장이 있다. 
* 테이블에 들어 있는 데이터에 변경을 가하는 UPDATE, DELETE, INSERT 문장은 테이블에 들어 있는 데이터들을 조작하는 종류의 SQL 문장들이다. 
* 그 외, 테이블을 생성하고 수정하고 변경하고 삭제하는 테이블 관련 SQL 문장이 있고, 추가로 데이터에 대한 권한을 제어하는 SQL 문장도 있다.
## 3. TABLE
>![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_149.jpg)

>별도의 정리 작업을 하지 않은 왼쪽 내용은 본인이 아니라면 알아보기도 힘들고 다른 사용자에게 큰 도움이 되지 않는다. 
but 오른쪽의 내용은 선수별로 필요한 정보가 정리되어 관심 있는 다른 사용자에게 도움이 될 수 있다.  
![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_150.jpg)

>데이터는 관계형 데이터베이스의 기본 단위인 테이블 형태로 저장된다. 모든 자료는 테이블에 등록이 되고, 우리는 테이블로부터 원하는 자료를 꺼내 올 수 있다.  
테이블은 어느 특정한 주제와 목적으로 만들어지는 일종의 집합이다. 
이 표만 있다면 내가 좋아하는 선수들의 상세한 정보들을 볼 수 있고, 선수들의 정보를 상호간에 비교해 볼 수도 있다.
 새로운 선수를 입력하려고 할 때 새로운 테이블을 생성할 필요 없이 데이터만 추가함으로서 선수들의 정보를 모두 관리할 수 있다.

>![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_151.jpg)

>선수, 팀, 팀연고지, 포지션, 등번호, 생년월일, 키, 몸무게가 각각의 칼럼이 되며, 해당 테이블은 반드시 하나 이상의 칼럼을 가져야 한다.  
ex) 이청용 선수에 대한 정보는 아래와 같이 8개의 칼럼을 가지는 하나의 행으로 데이터화 되어 테이블에 저장된 것이다

![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_152.jpg)

> 테이블에는 등록된 자료들이 있으며, 이 자료들은 삭제하지 않는 한 지속적으로 유지된다. 
> 만약 우리가 자료를 입력하지 않는다면 테이블은 본래 만들어졌을 때부터 가지고 있던 속성을 그대로 유지하면서 존재하게 된다.

>![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_153.jpg)

>테이블에 대해서 좀 더 상세히 살펴보면 테이블(TABLE)은 데이터를 저장하는 객체로서 관계형 데이터베이스의 기본 단위이다. 
>모든 데이터를 칼럼과 행의 2차원 구조로 나타낸다. 
>**칼럼**:세로 방향
>**행**:가로 방향
>**필드**:칼럼과 행이 겹치는 하나의 공간
>선수정보 테이블을 예로 들면 선수명과 포지션 등의 칼럼이 있고, 각 선수에 대한 데이터를 행으로 구성하여 저장한다.

![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_154.jpg)

>![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_155.jpg)

>선수와 관련된 데이터를 저장할 때 모든 데이터를 하나의 테이블로 저장하지 않는다.
>선수와 관련된 데이터를 선수 테이블과 구단 테이블이라는 복수의 테이블로 분할하여 저장하고 있다.  
분할된 테이블은 그 칼럼의 값에 의해 연결된다.
 이렇게 테이블을 분할하여 데이터의 불필요한 중복을 줄이는 것을 정규화
 데이터의 정합성 확보와 데이터 입력/수정/삭제시 발생할 수 있는 이상현상을 방지하기 위해 정규화는 관계형 데이터베이스 모델링에서 매우 중요한 프로세스이다.

>![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_156.jpg)

>각 행을 한 가지 의미로 특정할 수 있는 한 개 이상의 칼럼을 기본키라고 하며, 여기서는 <선수> 테이블의 ‘선수번호’와 <구단> 테이블의 ‘구단코드’가 기본키가 된다.
>  <선수> 테이블의 ‘구단코드’와 같이 다른 테이블의 기본 키로 사용되면서 테이블과의 관계를 연결하는 역할을 하는 칼럼을 외부키라고 한다.

>![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_157.jpg)
## 4. ERD(Entity Relationship Diagram)

팀 정보와 선수 정보 간에는 어떤 의미의 관계가 존재하며, 다른 테이블과도 어떤 의미의 연관성이나 관계를 가지고 있다. 

>![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_158.jpg)

>팀과 선수 간에는 “소속”이라는 관계가 맺어져 있다. 테이블 간 서로의 상관 관계를 그림으로 도식화한 것을 E-R 다이어그램이라고 하며, 간략히 ERD라고 한다. 
>* ERD의 구성 요소는 엔터티, 관계, 속성 3가지이며 현실 세계의 데이터는 이 3가지 구성 요소로 모두 표현이 가능하다.  
 K-리그의 테이블 관계를 IE 표기법과 Barker 표기법으로 표현한 ERD이다.

#### ERD
>![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_159.jpg)
>- 하나의 팀은 여러 명의 선수를 포함할 수 있다. - 한 명의 선수는 하나의 팀에 꼭 속한다.

>- 하나의 팀은 하나의 전용 구장을 꼭 가진다. - 하나의 운동장은 하나의 홈팀을 가질 수 있다.

>- 하나의 운동장은 여러 게임의 스케줄을 가질 수 있다. - 하나의 스케줄은 하나의 운동장에 꼭 배정된다.
![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_160.jpg)

>사원-부서 테이블 간의 양방향 관계는 다음과 같다.

>![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_161.jpg)

>- 하나의 부서는 여러 명의 사원을 보유할 수 있다. - 한 명의 사원은 하나의 부서에 꼭 소속된다.
## 5. DDL
#### 데이터 유형
![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_162.jpg)
#### CREATE TABLE

> 테이블은 일정한 형식에 의해서 생성된다. 테이블 생성을 위해서는 해당 테이블에 입력될 데이터를 정의하고, 정의한 데이터를 어떠한 데이터 유형으로 선언할 것인지를 결정해야 한다.

> #### 테이블과 칼럼 정의

>* 테이블에 존재하는 모든 데이터를 고유하게 식별할 수 있으면서 반드시 값이 존재하는 단일 칼럼이나 칼럼의 조합들(후보키) 중에 하나를 선정하여 기본키 칼럼으로 지정
>* 기본키는 단일 칼럼이 아닌 여러 개의 칼럼으로도 만들 ㅇ
>* 테이블과 테이블 간에 정의된 관계는 기본키(PRIMARY KEY)와 외부키(FOREIGN KEY)를 활용해서 설정
![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_163.jpg)

>-   K-리그와는 별개로 회사의 부서와 사원 테이블의 칼럼들도 정리한다.

>![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_164.jpg)

>#####  CREATE TABLE 구문형식
> **CREATE　TABLE　테이블이름 ( 칼럼명1 DATATYPE [DEFAULT 형식], 칼럼명2 DATATYPE [DEFAULT 형식], 칼럼명2 DATATYPE [DEFAULT 형식] ) ;**

>#### 테이블 생성 규칙

>- 테이블명은 객체를 의미할 수 있는 적절한 이름을 사용한다. 가능한 단수형을 권고한다. 
>-  테이블 명은 다른 테이블의 이름과 중복되지 않아야 한다.
>- 한 테이블 내에서는 칼럼명이 중복되게 지정될 수 없다. 
>- 테이블 이름을 지정하고 각 칼럼들은 괄호 "( )" 로 묶어 지정한다. 
>- 각 칼럼들은 콤마 ","로 구분되고, 테이블 생성문의 끝은 항상 세미콜론 ";"으로 끝난다. 
>-  칼럼에 대해서는 다른 테이블까지 고려하여 데이터베이스 내에서는 일관성 있게 사용하는 것이 좋다.(데이터 표준화 관점) 
>- 칼럼 뒤에 데이터 유형은 꼭 지정되어야 한다. 
>-  테이블명과 칼럼명은 반드시 문자로 시작해야 하고, 벤더별로 길이에 대한 한계가 있다. 
>- 벤더에서 사전에 정의한 예약어(Reserved word)는 쓸 수 없다. 
>-  A-Z, a-z, 0-9, _, $, # 문자만 허용된다. 
>- 테이블명이 잘못된 사례

>![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_165.jpg)


>#### 테이블 생성 예제에서 추가적인 주의 사항 
>- 테이블 생성시 대/소문자 구분은 하지 않는다. 
>-- 기본적으로 테이블이나 칼럼명은 대문자로 만들어진다. 
>- DATETIME 데이터 유형에는 별도로 크기를 지정하지 않는다. 
>- 문자 데이터 유형은 반드시 가질 수 있는 최대 길이를 표시해야 한다. 
>- 칼럼과 칼럼의 구분은 콤마로 하되, 마지막 칼럼은 콤마를 찍지 않는다. 
>- 칼럼에 대한 제약조건이 있으면 CONSTRAINT를 이용하여 추가할 수 있다.
>#####  제약조건
>![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_166.jpg)

>  NULL 의미

>>NULL(ASCII 코드 00번)은 공백(BLANK, ASCII 코드 32번)이나 숫자 0(ZERO, ASCII 48)과는 전혀 다른 값이며, 조건에 맞는 데이터가 없을 때의 공집합과도 다르다. ‘NULL’은 ‘아직 정의되지 않은 미지의 값’이거나 ‘현재 데이터를 입력하지 못하는 경우’를 의미한다.

> DEFAULT 의미

>> 데이터? 기본값(DEFAULT)을 사전에 설정할 수 있다. 데이터 입력시 명시된 값을 지정하지 않은 경우에 NULL 값이 입력되고, DEFAULT 값을 정의했다면 해당 칼럼에 NULL 값이 입력되지 않고 사전에 정의된 기본 값이 자동으로 입력된다.

##### 생성된 테이블 구조 확인

>테이블을 생성한 후 테이블의 구조가 제대로 만들어졌는지 확인할 필요가 있다. 
Oracle의 경우 “DESCRIBE 테이블명;” 또는 간략히 “DESC 테이블명;”으로 해당 테이블에 대한 정보를 확인할 수 있다.
SQL Server의 경우 “sp_help ‘dbo.테이블명’”으로 해당 테이블에 대한 정보를 확인할 수 있다.
##### ALTER TABLE
>업무적인 요구 사항이나 시스템 운영상 테이블을 사용하는 도중에 변경해야 할 일들이 발생할 수도 있다.

>**ADD COLUMN**
>>ALTER TABLE 테이블명 ADD 추가할 칼럼명 데이터 유형;

>**DROP COLUMN** 
>>ALTER TABLE 테이블명 DROP COLUMN 삭제할 칼럼명;
>
>**MODIFY COLUMN**
>>* [Oracle] ALTER TABLE 테이블명 MODIFY (칼럼명1 데이터 유형 [DEFAULT 식] [NOT NULL], 칼럼명2 데이터 유형 …);
>>* [SQL Server] ALTER TABLE 테이블명 ALTER (칼럼명1 데이터 유형 [DEFAULT 식] [NOT NULL], 칼럼명2 데이터 유형 …);

>**DROP COLUMN**
>>ALTER TABLE 테이블명 DROP CONSTRAINT 제약조건명;

>**ADD CONSTRAINT**
>>ALTER TABLE 테이블명 ADD CONSTRAINT 제약조건명 제약조건 (칼럼명);

>**RENAME TABLE**
>>* RENAME 명령어를 사용하여 테이블의 이름을 변경할 수 있다.
>RENAME 변경전 테이블명 TO 변경후 테이블명;
>>* SQL Server에서는 sp_rename을 이용하여 테이블 이름을 변경할 수 있다.
sp_rename 변경전 테이블명, 변경후 테이블명;

> **DROP TABLE**:테이블 과제
>>DROP TABLE 테이블명 [CASCADE CONSTRAINT];

> **TRUNCATE TABLE**
> TRUNCATE TABLE은 테이블 자체가 삭제되는 것이 아니고, 해당 테이블에 들어있던 모든 행들이 제거되고 저장 공간을 재사용 가능하도록 해제한다. 
>>TRUNCATE TABLE PLAYER;

## DML
#### 1. INSERT
테이블에 데이터를 입력하는 방법은 두 가지 유형이 있으며 한 번에 한 건만 입력된다.

>▶ INSERT INTO 테이블명 (COLUMN_LIST)VALUES (COLUMN_LIST에 넣을 VALUE_LIST); ▶ INSERT INTO 테이블명VALUES (전체 COLUMN에 넣을 VALUE_LIST);
[예제] 선수 테이블에 박지성 선수의 데이터를 일부 칼럼만 입력한다.
#### 2. UPDATE

UPDATE 다음에 수정되어야 할 칼럼이 존재하는 테이블명을 입력하고 SET 다음에 수정되어야 할 칼럼명과 해당 칼럼에 수정되는 값으로 수정이 이루어진다.

>UPDATE 테이블명 SET 수정되어야 할 칼럼명 = 수정되기를 원하는 새로운 값;

#### 3. DELETE

DELETE FROM 다음에 삭제를 원하는 자료가 저장되어 있는 테이블명을 입력하고 실행한다. 이때 FROM 문구는 생략이 가능한 키워드이며, 뒤에서 배울 WHERE 절을 사용하지 않는다면 테이블의 전체 데이터가 삭제된다.

>DELETE [FROM] 삭제를 원하는 정보가 들어있는 테이블명;

#### 4. SELECT

사용자가 입력한 데이터는 언제라도 조회가 가능하다. 
 - ALL : Default 옵션이므로 별도로 표시하지 않아도 된다. 중복된 데이터가 있어도 모두 출력한다. 
 -  DISTINCT : 중복된 데이터가 있는 경우 1건으로 처리해서 출력한다.
>#### DISTINCT 옵션

>[예제 및 실행 결과] SELECT ALL POSITION FROM PLAYER; ALL은 생략 가능한 키워드이므로 아래 SQL 문장도 같은 결과를 출력한다, SELECT POSITION FROM PLAYER; 480개의 행이 선택되었다.

>[예제] SELECT DISTINCT POSITION FROM PLAYER;

>[실행 결과] Oracle POSITION -------- GK DF FW MF 5개의 행이 선택되었다.
>실행 결과를 보면 480개의 행이 모두 출력된 것이 아니라 포지션의 종류인 4개의 행과 포지션 데이터가 아직 미정인 NULL까지 5건의 데이터만 출력이 되었다.

>-   **WILDCARD 사용하기**

>>입력한 정보들을 보기위해 PLAYER 테이블에서 보고 싶은 정보들이 있는 칼럼들을 선택하여 조회해보는 것이다. 
>해당 테이블의 모든 칼럼 정보를 보고 싶을 경우에는 와일드카드로 애스터리스크(*)를 사용하여 조회할 수 있다.
>
>>SELECT * FROM 테이블명;

>>실행 결과 화면을 보면 칼럼 레이블(LABLE)이 맨 위에 보이고, 레이블 밑에 점선이 보인다.
> 실질적인 자료는 다음 줄부터 시작된다. 
> 레이블은 기본적으로 대문자로 보이고, 첫 라인에 보이는 레이블의 정렬은 다음과 같다.
>>  좌측 정렬 : 문자 및 날짜 데이터 - 우측 정렬 : 숫자 데이터

>-   **ALIAS 부여하기**

>조회된 결과에 일종의 별명(ALIAS, ALIASES)을 부여해서 칼럼 레이블을 변경할 수 있다. 칼럼 별명(ALIAS)에 대한 사항을 정리하면 다음과 같다.

>>- 칼럼명 바로 뒤에 온다. 
>>-  칼럼명과 ALIAS 사이에 AS, as 키워드를 사용할 수도 있다.  
>>-  이중 인용부호(Double quotation)는 ALIAS가 공백, 특수문자를 포함할 경우와 대소문자 구분이 필요할 경우 사용된다.


#### 5. 산술 연산자와 합성 연산자

-   산술 연산자

> 산술 연산자는 수학에서와 같이 (), *, /, +, - 의 우선순위를 가진다.

>![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_169.jpg)
-   합성(CONCATENATION) 연산자

>문자와 문자를 연결하는 합성(CONCATENATION) 연산자를 사용하면 별도의 프로그램 도움 없이도 SQL 문장만으로도 유용한 리포트를 출력할 수 있다. 합성(CONCATENATION) 연산자의 특징은 다음과 같다.

>문자와 문자를 연결하는 경우 2개의 수직 바(||)에 의해 이루어진다. 
>* (Oracle) - 문자와 문자를 연결하는 경우 + 표시에 의해 이루어진다. 
>* (SQL Server) - 두 벤더 모두 공통적으로 CONCAT (string1, string2) 함수를 사용할 수 있다. 
>- 칼럼과 문자 또는 다른 칼럼과 연결시킨다. 
>- 문자 표현식의 결과에 의해 새로운 칼럼을 생성한다.
## 트랜젝션
#### 1. Definition
>트랜잭션(TRANSACTION)이란 밀접히 관련되어 분리될 수 없는 한 개 이상의 데이터베이스 조작을 가리킨다. 
>하나의 트랜잭션에는 하나 이상의 SQL 문장이 포함된다. 
>트랜잭션은 분할할 수 없는 최소의 단위이다.
>
![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_170.jpg)
#### 2. COMMIT

입력한 자료나 수정한 자료에 대해서 또는 삭제한 자료에 대해서 전혀 문제가 없다고 판단되었을 경우 COMMIT 명령어를 통해서 트랜잭션을 완료할 수 있다.
- 단지 메모리 BUFFER에만 영향을 받았기 때문에 데이터의 변경 이전 상태로 복구 가능하다. 
-  현재 사용자는 SELECT 문장으로 결과를 확인 가능하다. 
-  다른 사용자는 현재 사용자가 수행한 명령의 결과를 볼 수 없다. 
-  변경된 행은 잠금(LOCKING)이 설정되어서 다른 사용자가 변경할 수 없다.
>  **SQL Server의 COMMIT**
Oracle은 DML을 실행하는 경우 DBMS가 트랜잭션을 내부적으로 실행하며 DML 문장 수행 후 사용자가 임의로 COMMIT 혹은 ROLLBACK을 수행해 주어야 트랜잭션이 종료된다.
#### 3. ROLLBACK

테이블 내 입력한 데이터나, 수정한 데이터, 삭제한 데이터에 대하여 COMMIT 이전에는 변경 사항을 취소할 수 있는데 데이터베이스에서는 롤백 기능을 사용한다. 
롤백은 데이터 변경 사항이 취소되어 데이터의 이전 상태로 복구되며, 관련된 행에 대한 잠금이 풀리고 다른 사용자들이 데이터 변경을 할 수 있게 된다.
>**예제**
> PLAYER 테이블에 데이터를 입력하고 ROLLBACK을 실행한다.
>>[예제] Oracle INSERT INTO PLAYER (PLAYER_ID, TEAM_ID, PLAYER_NAME, POSITION, HEIGHT, WEIGHT, BACK_NO) VALUES ('1999035', 'K02', '이운재', 'GK', 182, 82, 1); 1개의 행이 만들어졌다. 
>ROLLBACK; 롤백이 완료되었다.
>
>PLAYER 테이블에 있는 데이터를 수정하고 ROLLBACK을 실행한다.
>>[예제] Oracle UPDATE PLAYER SET HEIGHT = 100; 480개의 행이 수정되었다. ROLLBACK; 롤백이 완료되었다.
>
> PLAYER 테이블에 있는 데이터를 삭제하고 ROLLBACK을 실행한다.
>>[예제] Oracle DELETE FROM PLAYER; 480개의 행이 삭제되었다. ROLLBACK; 롤백이 완료되었다.

>**SQL Server의 ROLLBACK**
SQL Server는 위에서 언급한 바와 같이 AUTO COMMIT이 기본 방식이므로 임의적으로 ROLLBACK을 수행하려면 명시적으로 트랜잭션을 선언해야 한다. 
#### 4. SAVEPOINT

복잡한 대규모 트랜잭션에서 에러가 발생했을 때 SAVEPOINT까지의 트랜잭션만 롤백하고 실패한 부분에 대해서만 다시 실행할 수 있다. 
복수의 저장점을 정의할 수 있으며, 동일이름으로 저장점을 정의했을 때는 나중에 정의한 저장점이 유효하다.

>>SAVEPOINT SVPT1;
>
>저장점까지 롤백할 때는 ROLLBACK 뒤에 저장점 명을 지정한다.
>>ROLLBACK TO SVPT1;
>
>위와 같이 롤백(ROLLBACK)에 SAVEPOINT 명을 부여하여 실행하면 저장점 설정 이후에 있었던 데이터 변경에 대해서만 원래 데이터 상태로 되돌아가게 된다. SQL Server는 SAVE TRANSACTION을 사용하여 동일한 기능을 수행할 수 있다. 다음의 SQL문은 SVTR1이라는 저장점을 정의하고 있다.
>
>>SAVE TRANSACTION SVTR1;
>
>저장점까지 롤백할 때는 ROLLBACK 뒤에 저장점 명을 지정한다.
>
>>ROLLBACK TRANSACTION SVTR1;
![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_171.jpg)
## WHERE 조건절
#### 1. WHERE 조건절 정의
>SELECT [DISTINCT/ALL] 칼럼명 [ALIAS명] FROM 테이블명 WHERE 조건식;
>
WHERE 절은 FROM 절 다음에 위치하며, 조건식은 아래 내용으로 구성된다.

- 칼럼(Column)명 (보통 조건식의 좌측에 위치)
-  비교 연산자 
-  문자, 숫자, 표현식 (보통 조건식의 우측에 위치) 
- 비교 칼럼명 (JOIN 사용시)
#### 2. 연산자의 종류
WHERE 절에 사용되는 연산자는 3가지 종류가 있다.

* 비교 연산자 (부정 비교 연산자 포함) 
*  SQL 연산자 (부정 SQL 연산자 포함) 
*  논리 연산자

![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_172.jpg)

![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_173.jpg)

연산자의 우선순위를 살펴보면 다음과 같다.

- 괄호로 묶은 연산이 제일 먼저 연산 처리된다. - 연산자들 중에는 부정 연산자(NOT)가 먼저 처리되고, - 비교 연산자(=,>,>=,<,<=), SQL 비교 연산자(BETWEEN a AND b, IN (list), LIKE, IS NULL)가 처리되고, - 논리 연산자 중에서는 AND, OR의 순으로 처리된다.

#### 3. 비교 연산자

![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_174.jpg)


![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_175.jpg)

#### 4. SQL 연산자

SQL 연산자는 SQL 문장에서 사용하도록 기본적으로 예약되어 있는 연산자로서 모든 데이터 타입에 대해서 연산이 가능한 4가지 종류가 있다.

![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_176.jpg)


-   IN (list) 연산자

[예제] 소속팀 코드와 관련된 IN (list) 형태의 SQL 비교 연산자를 사용하여 WHERE 절에 사용한다.

[예제] SELECT PLAYER_NAME 선수이름, POSITION 포지션, BACK_NO 백넘버, HEIGHT 키 FROM PLAYER WHERE TEAM_ID IN ('K02','K07');

[실행 결과] 선수이름 포지션 백넘버 키 ------ ---- ---- --- 데니스 FW 11 176 서정원 FW 14 173 손대호 DF 17 186 오규찬 MF 24 178 윤원일 MF 45 176 김동욱 MF 40 176 김회택 DF 서현옥 DF 정상호 DF 최철우 DF 정영광 GK 41 185 ：：：： 100개의 행이 선택되었다.

[예제] 사원 테이블에서 JOB이 MANAGER이면서 20번 부서에 속하거나, JOB이 CLERK이면서 30번 부서에 속하는 사원의 정보를 IN 연산자의 다중 리스트를 이용해 출력하라.

[예제] SELECT ENAME, JOB, DEPTNO FROM EMP WHERE (JOB, DEPTNO) IN (('MANAGER',20),('CLERK',30));

[실행 결과] ENAME JOB DEPTNO ------ -------- ------ JONES MANAGER 20 JAMES CLERK 30 2개의 행이 선택되었다.

사용자들이 잘 모르고 있는 다중 리스트를 이용한 IN 연산자는 SQL 문장을 짧게 만들어 주면서도 성능 측면에서도 장점을 가질 수 있는 매우 유용한 연산자이므로 적극적인 사용을 권고한다. 다만, 아래 SQL 문장과는 다른 결과가 나오게 되므로 용도를 구분해서 사용해야 한다.

[예제] SELECT ENAME, JOB, DEPTNO FROM EMP WHERE JOB IN ('MANAGER','CLERK') AND DEPTNO IN (20,30);

[실행 결과] ENAME JOB DEPTNO ------ ------- ------ SMITH CLERK 20 JONES MANAGER 20 BLAKE MANAGER 30 ADAMS CLERK 20 JAMES CLERK 30 5개의 행이 선택되었다.

-   LIKE 연산자

>[예제] SELECT PLAYER_NAME 선수이름, POSITION 포지션, BACK_NO 백넘버, HEIGHT 키 FROM PLAYER WHERE POSITION LIKE 'MF';

>[예제] SELECT PLAYER_NAME 선수이름, POSITION 포지션, BACK_NO 백넘버, HEIGHT 키 FROM PLAYER WHERE POSITION LIKE 'MF';

>[실행 결과] 선수이름 포지션 백넘버 키 ------ ----- ----- --- 가비 MF 10 177 강대희 MF 26 174 고종수 MF 22 176 고창현 MF 8 170 정기범 MF 28 173 정동현 MF 25 175 정두현 MF 4 175 정준 MF 44 170 ：：：： 162개의 행이 선택되었다.

LIKE의 사전적 의미는 ‘~와 같다’이다. 
따라서 위와 같은 경우라면 비교 연산자인 ‘=’을 사용해서 작성해도 같은 결과를 얻을 수 있을 것이다. 
그러나 만약 “장”씨 성을 가진 선수들을 조회할 경우는 어떻게 할까? 이런 문제를 해결하기 위해서 LIKE 연산자에서는 와일드카드(WildCard)를 사용할 수 있다. 
와일드카드(WildCard)란 한 개 혹은 0개 이상의 문자를 대신해서 사용하기 위한 특수 문자를 의미하며, 이를 조합하여 사용하는 것도 가능하므로 SQL 문장에서 사용하는 스트링(STRING) 값으로 용이하게 사용할 수 있다.

![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_177.jpg)

-   BETWEEN a AND b 연산자

>[예제] 세 번째로 키가 170 센티미터 이상 180센티미터 이하인 선수들의 정보를 BETWEEN a AND b 연산자를 사용하여 WHERE 절을 완성한다.
>
>[예제] SELECT PLAYER_NAME 선수이름, POSITION 포지션, BACK_NO 백넘버, HEIGHT 키 FROM PLAYER WHERE HEIGHT BETWEEN 170 AND 180; BETWEEN a AND b는 범위에서 'a'와 'b'의 값을 포함하는 범위를 말하는 것이다.

>[실행 결과] 선수이름 포지션 백넘버 키 ------ ---- ---- --- 장철우 DF 7 172 홍광철 DF 4 172 강정훈 MF 38 175 공오균 MF 22 177 정국진 MF 16 172 정동선 MF 9 170 최경규 MF 10 177 최내철 MF 24 177 배성재 MF 28 178 샴 MF 25 174 김관우 MF 8 175 ：：：： 259개의 행이 선택되었다.

-   IS NULL 연산자

NULL(ASCII 00)은 값이 존재하지 않는 것으로 확정되지 않은 값을 표현할 때 사용한다. 따라서 어떤 값보다 크거나 작지도 않고 ‘ ’(공백, ASCII 32)이나 0(Zero, ASCII 48)과 달리 비교 자체가 불가능한 값인 것이다. 연산 관련 NULL의 특성은 다음과 같다.

>- NULL 값과의 수치연산은 NULL 값을 리턴한다. 
>- NULL 값과의 비교연산은 거짓(FALSE)을 리턴한다. 
>- 어떤 값과 비교할 수도 없으며, 특정 값보다 크다, 적다라고 표현할 수 없다.

따라서 NULL 값의 비교는 비교 연산자인 “=”, “>”, “>=”, “<”, “=”를 통해서 비교할 수도 없고, 만일 비교 연산을 하게 되면 결과는 거짓(FALSE)을 리턴하고, 수치 연산자(+,-,*,/ 등)를 통해서 NULL 값과 연산을 하게 되면 NULL 값을 리턴한다. NULL 값의 비교 연산은 IS NULL, IS NOT NULL 이라는 정해진 문구를 사용해야 제대로 된 결과를 얻을 수 있다.


#### 5. 논리 연산자

논리 연산자는 비교 연산자나 SQL 비교 연산자들로 이루어진 여러 개의 조건들을 논리적으로 연결시키기 위해서 사용되는 연산자라고 생각하면 된다. 
![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_178.jpg)

![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_179.jpg)



#### 6. 부정 연산자

비교 연산자, SQL 비교 연산자에 대한 부정 표현을 부정 논리 연산자, 부정 SQL 연산자로 구분할 수 있다.

![sql가이드](http://www.dbguide.net/publishing/img/knowledge/SQL_180.jpg)

#### 7. ROWNUM, TOP 사용

-   ROWNUM

Oracle의 ROWNUM은 칼럼과 비슷한 성격의 Pseudo Column으로써 SQL 처리 결과 집합의 각 행에 대해 임시로 부여되는 일련번호이며, 테이블이나 집합에서 원하는 만큼의 행만 가져오고 싶을 때 WHERE 절에서 행의 개수를 제한하는 목적으로 사용한다.

건의 행만 가져오고 싶을 때는 - SELECT PLAYER_NAME FROM PLAYER WHERE ROWNUM = 1; 이나 - SELECT PLAYER_NAME FROM PLAYER WHERE ROWNUM <= 1; 이나 - SELECT PLAYER_NAME FROM PLAYER WHERE ROWNUM < 2; 처럼 사용할 수 있다.

두 건 이상의 N 행을 가져오고 싶을 때는 ROWNUM = N; 처럼 사용할 수 없으며 - SELECT PLAYER_NAME FROM PLAYER WHERE ROWNUM <= N; 이나 - SELECT PLAYER_NAME FROM PLAYER WHERE ROWNUM
