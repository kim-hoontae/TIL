# LIKE 패턴
> WHERE 열(컬럼) LIKE '패턴'

패턴을 정의할 때 사용할 수 있는 메타문자

- **' % '**는 임의의 문자열을 의미 
- **' _ '**는 임의의 문자하나를 의미

## 1. 전방일치
```
SELECT * FROM products WHERE description LIKE 'text%'
```
'text'라는 문자열로 시작되는 행만을 검색

## 2. 중간일치
```
SELECT * FROM products WHERE description LIKE '%text%'
```
'text'라는 문자열이 포함된 모든 행을 검색
> % 는 임의의 문자열과 매치하며, 빈문자열도 매치함
그렇기에 문자열의 앞과 뒤에 문자열이 없어도 검색함


## 3. 후방일치
```
SELECT * FROM products WHERE description LIKE '%text'
```
'text'라는 문자열로 끝나는 행만을 검색

# %검색하기
> WHERE 열(컬럼) LIKE '%\%%'

' \ '이스케이프를 사용 하여 메타문자가 아닌 일반문자로 의미하게 할 수 있다.

# ' 의 이스케이프사용
' it's '의 같은 경우 ' it''s ' 로 '를 2개를 사용하여 이스케이프 할 수 있다.

