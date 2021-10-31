# CASE 문
```
CASE WHEN 조건식1 THEN 식1
     WHEN 조건식2 THEN 식2
     ELSE 식3
END
```
 - NULL값은 RDBMS에 갖추어져 있는 기존의 연산자나 함수만으로는 처리할 수 없다.
 - WHEN 절에는 참과 거짓을 반환하는 조건식을 기술한다.
 - 참이되는 경우는 THEN 절에 적용한 식이 처리된다.
 - ELSE절의 경우 어느 것에도 참에 해당하지 못할 경우 적용된다.
 - ELSE는 생략이 가능하며 생략시 'ELSE NULL'로 간주하여 ELSE 값들은 NULL이된다.
# NULL 값을 0으로 변환하기
```
SELECT upper_code, CASE WHEN upper_code IS NULL THEN 0 ELSE upper_code END "upper_code(null=0)" FROM options;
```
- upper_code 가 IS NULL 일 경우 0을 반환하고 아닌경우(ELSE) upper_code의 값을 반환
## COALESCE
```
SELECT upper_code, COALESCE(upper_code,0) FROM options;
```
- COALESCE 함수를 사용하면 간편하게 NULL을 변환할 수 있다.
- NULL이 아닌 경우 가장 앞에 있는 인수의 값을 반환
- 앞에 있는 인수가 NULL일 경우 뒤에 값을 반환하여 0이 반환된다.
# 또 다른 CASE문
```
1. 검색 CASE
SELECT upper_code AS '상위코드', 
CASE WHEN upper_code=0 THEN '면허' 
     WHNE upper_code=1 THEN '언어' 
     ELSE '그외' 
END AS '코드' from options;
```
```
2. 단순 CASE
SELECT upper_code AS '상위코드', 
CASE upper_code 
WHEN 0 THEN '면허' 
WHNE 1 THEN '언어' 
ELSE '그외' 
END AS '코드' from options;
```
- `검색` CASE의 경우 WHEN 뒤에 '조건식' THEN 뒤에 '식'
- `단순` CASE의 경우 WHEN 뒤에 '식' THEN 뒤에 '식'
- 숫자로 이루어진 코드를 알아보기 더 쉽게 문자열로 변환하는 경우 CASE문을 사용
- 디코드는 문자화 시키는것 1 = '언어'
- 인코드는 수치화 시키는것 '언어' = 1

# CASE 사용시 주의사항
- SELECT , WHERE, ORDER BY 구에서 사용할 수 있다.
- ELSE를 생략할 경우 NULL이 되기에 지정하는 편이 낫다.

# WHEN에 NULL 지정하기
```
1. 검색 CASE (사용O)
SELECT upper_code AS '상위코드', 
CASE WHEN upper_code=0 THEN '면허' 
     WHEN upper_code=1 THEN '언어' 
     WHEN upper_code IS NULL THEN '데이터 없음'
ELSE END AS '코드' from options;
```
```
2. 단순 CASE (사용X)
SELECT upper_code AS '상위코드', 
CASE upper_code 
WHEN 0 THEN '면허' 
WHEN 1 THEN '언어'
WHEN NULL THEN '데이터 없음'
ELSE END AS '코드' from options;
```
- 단순 CASE의 경우 upper_code=0, upper_code=1, upper_code=NULL 형식으로 처리됨  
- 따라서 비교연산자로 a = NULL은 참이 되지 않기에 단순 CASE에서 사용 불가
- 검색 CASE로 사용가능
