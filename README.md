# JSP_Basic

## 테이블 생성해주기
```create table member(
    id varchar2(10)not null,
    pass varchar2(10) not null,
    name varchar2(3) not null,
    regidate date default sysdate not null,
    primary key(id));

alter table member MODIFY name VARCHAR(30);

create table board(
    num number primary key,
    title varchar2(200) not null,
    content varchar2(2000) not null,
    id varchar2(10) not null,
    postdate date default sysdate not null,
    visitcount number(6));
    
alter table board
    add constraint board_mem_fk foreign key(id)
    REFERENCES member(id);
    
create sequence seq_board_num 
    increment by 1
    start with 1
    minvalue 1
    nomaxvalue 
    nocycle
    nocache;
    
insert into board (num, title, content, id, postdate, visitcount)
    values (seq_board_num.nextval, '제목1입니다', '내용1입니다', 'musthave',
        sysdate, 0);
        
insert into member (id,pass,name) values ('musthave', '1234', '머스트해브');

commit; ```

### 5장 공부 내용 요약
```
1. JDBC 프로그래밍 순서 
+ JDBC 드라이버 로드 
+ 데이터베이스 연결 (JDBConnect)
+ 쿼리문 작성
+ 쿼리문(Statement) 객체 생성
+ 쿼리 실행 (ResultSet)
+ 실행 결과 처리 while(rs.next) -> false or true
+ 연결 해제 

2. 테이블에 저장된 레코드를 변경하지 않는 SELECT 문은 executeQuery() 메서드 사용
  레코드를 변경하는 INSERT, UPDATE, DELETE문은 executeUpdate()
```
        
