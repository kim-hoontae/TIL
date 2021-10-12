# SELECT 구에서 열 지정
```
SELECT id, name FROM users;
```
자신이 테이블의 필요한 열만 지정할 경우 ' , '를 이용하여 필요한 여러개의 열을 지정할 수 있다.
# WHERE 구에서 행 지정
```
SELECT * FROM users WHERE id = 7;
SELECT * FROM users WHERE id < 7;
SELECT id, name FROM users WHERE name = '김철수';
```
- select 구 뒤에 열을 지정하고 where구로 행을 지정 할 수 있다. 
- where 구에서 지정한 값이 없는 경우에는 아무것도 반환하지 않는다.
- id = 7같은 경우 연산자를 사용할 수 있다. '<>'를 사용할 경우 그 값을 제외한 나머지를 불러온다.
- 김철수 같이 문자열 인 경우 (' ')를 사용해야한다.
- 날짜시간의 경우에도 (' ')를 사용한다. 그리고 날짜의 경우 연월일은 (-)으로 구분하고 시간은(:)으로 구분한다.
### WHERE 구에 사용 가능한 연산자
- **' = '**
- **' <> '**
- **' < '** 
- **' > '**
- **' >= '**
- **' <= '**

# NULL값 검색
```
SELECT * FROM users WHERE phone_number = NULL; X
SELECT * FROM users WHERE phone_number IS NULL; O

SELECT * FROM users WHERE phone_number IS NOT NULL;
```
- NULL 값을 검색할 때는 = 연산자가 아닌 IS NULL을 사용해야한다.
- NULL 값이 아닌 값을 검색 할 때는 IS NOT NULL을 사용한다.


