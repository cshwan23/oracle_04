# oracle_04
oracle -table 연습




테이블 만드는 방법

create + table + 테이블명 (    칼럼명 + 자료형 + 제약조건   );

숫자자료형

number( 2 ) 
: 숫자 자료형 정수 2자리 값까지 저장 된다는 뜻 (0~99)


문자자료형
varchar2(20)
: 문자자료형 (한글 10 영문20) 이 저장 되도록 설정


제약조건(비지마 ! )
not null
: 비지마!

제약조건(중복되지마 ! )

unique
: 중복되지마라.


PK설정(비지말고 중복되지말고 FK가 참조할수있는 제약조건)
primary key ( 칼럼명)
: 해당 칼럼명은 primary key 로 제약 조건 설정.
: primary key는 1. not null , 2. unique , 3. FK가 언젠가 참조할 수 있어 라는 제약조건을 의미.
: primary key 설정은 관용적으로 칼럼명 오른쪽에 설정하지 않고 모든 칼럼명을 선언한 이후 설정한다.



테이블에 행단위로 데이터 집어넣기
insert into 테이블명 ( 칼럼명 ) values ( 데이터 );
: 테이블명을 갖고있는 테이블에  행 단위로 칼럼명에 해당하는 데이터를 집어넣기. 
: create 로 만들때 나열했던 칼럼명 순서와 자료형 순서대로 데이터를 순서에 맞춰 집어넣어야 한다.
: 서로 자료형이 맞지 않으면 칼럼에 데이터를 넣을 수 없다.



테이블에 모든 행 보여주기
select * from 테이블명; 
: 테이블명에 해당하는 테이블의 모든 칼럼명과 데이터를 검색.(모든 행 보기)



여태까지 한 작업 인정하기
commit;
: 여태까지 한 입력 또는 수정 또는 삭제 작업을 실제로 인정하기.
: 입력 수정 삭제 작업은 가상 작업이므로 commit 을 실행해야 실제 작업으로 인정된다.



입력한 값이 없으면 디폴트로 0집어넣기

salary number(10) default 0
: 이 뜻은 salary 라는 칼럼명에 숫자정수 10자리까지 들어올 수 있고. 
: 들어오는 데이터가 없다면 디폴트 값으로 0을 집어넣으라는 제약조건이다.
: 자동으로 디폴트 값이 입력되므로 not null의 제약조건을 자동으로 가진다.



입력된 날짜 값이 없다면 디폴트로 현재날짜 집어넣기 
hire_date   date   default   sysdate
: hire_date 라는 칼럼명에 date 자료형 즉 날짜 자료형을 선언하고 날짜가 저장되도록 설정.
: 입력되지 않으면 현제 시스템 날짜 즉 현재 날짜값이 들어가도록 디폴트값 설정.
: sysdate는 현재 시스템 날짜를 의미한다.




FK설정하고 PK참조하기
foreign key(dep_no)   references  dept(dep_no)
: fk설정
: foreign key(현재테이블의 칼럼명) references 참조받을 테이블명 ( 참조받을 PK칼럼명 )



같은 테이블에 있는 PK를 참조하려고 할 때 FK 설정하기

constraint  employee_mgr_emp_no_fk  foreign key( mgr_emp_no )  references  employee ( emp_no )
: 같은 테이블에 있는 pk를 참조하고자할 시 fk 설정.
: pk 설정을 잠시 꺼두기 위해(제약 조건 무력화 시키기 위한 이름을 설정한다.)
: constraint 무력화 하기위한 새로운 이름 + foreign key(현재 테이블의 fk 칼럼명 )+ references 현재 테이블명(pk칼럼명)


해당 테이블을 삭제하기﻿

drop table 테이블명;
: 해당 테이블명의 테이블 내용 다 지우기


같은 테이블에 있는 PK를 참조할 제약조건을 잠시 끄기﻿

 alter table  employee  disable constraint  employee_mgr_emp_no_fk ; 
: alter( 바꾸다)
: disable(무력하게하다)
: alter + table + 해당 테이블명 + disable constraint + 제약 조건이 걸린 칼럼명 ;
: employee_mgr_emp_no_fk 라는 이름의 제약조건 끄기.


같은 테이블에 있는 PK를 참조할 제약조건을 켜기﻿

 alter table employee enable constraint employee_mgr_emp_no_fk ; 
: alter + table + 해당 테이블명 + enable constraint + 제약 조건이 걸린 칼럼명 ;
: employee_mgr_emp_no_fk 라는 이름의 제약조건 켜기.



