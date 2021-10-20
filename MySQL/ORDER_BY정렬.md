# ORDER BY 정렬
## 1. WHERE 뒤에 ORDER BY 지정
```
SELECT * FROM user WHERE age > 21 ORDER BY age;
```
21살 보다 많은 나이 순서로 정렬
## 2. FROM 뒤에 ORDER BY 지정
```
SELECT * FROM user ORDER BY age;
```
## 3. 내림차순 DESC
```
SELECT * FROM user ORDER BY age DESC;
```
## 4. 오름차순 ASC
```
SELECT * FROM user ORDER BY age ASC;
```
오름차순은 자동으로 정렬되기때문에 사용하지 않아도되고 ASC를 사용해도된다.
그러므로 ORDER BY의 기본 정렬은 오름차순이다.
## 5. 대소관계
- 숫자형과 문자형으로 나눌수 있다.
- 숫자형의 경우 1, 2, 3 ~ 100 순으로 크기가 커지는데로 나눌 수 있다.
- 문자형의 숫자일 경우 1,2,10,11 이 아닌 1, 10, 11, 2 순으로 정렬된다.(**주의!!!**)
- 문자형의 경우 한글은 자음 ㄱ,ㄴ,ㄷ ~ ㅎ, 모음 ㅏ,ㅑ,ㅓ ~ ㅣ 순서로 정렬
- 문자형 영어는 알파벳 순서 a,b,c ~ z 순서로 정렬

## ORDER BY는 테이블에 영향을 주지 않는다!!!
SELECT문으로 데이터를 검색하는 명령이기때문에 테이블을 변경하지는 않는다.

# 복수의 열을 정렬
## 1. 조건이 있을 경우 WHERE문 사용 가능하다.
```
SELECT * FROM user WHERE age > 21 ORDER BY height[ASC,DESC] , weight[ASC,DESC];
```
키와 몸무게 2개의 컬럼이 있다고 가정한다.
## 2. 2개 이상의 열(컬럼)중 1개의 컬럼만 지정 
```
SELECT * FROM user ORDER BY height;
```
키만 정렬이 되고 몸무게는 따로 정렬이 되지 않는다.
## 3. 2개의 컬럼을 지정
```
SELECT * FROM user ORDER BY height,weight;
```
키와 몸무게 모두 정렬된다. 키를 기준으로 먼저 정렬하고 몸무게가 정렬
## 4. 컴럼의 위치 변경
```
SELECT * FROM user ORDER BY weight,height;
```
몸무게를 기준으로 먼저 정렬한다음 키가 정렬된다.
## 5. DESC를 사용하여 내림차순 정렬
```
SELECT * FROM user ORDER BY height ASC,weight DESC;
```
키를 먼저 오름차순으로 정렬하고 몸무게는 내림차순으로 정렬
## 6. NULL 값 정렬
MySQL에서는 NULL 값을 가장 작은 값으로 취급 ASC에서 가장 먼저 DESC에서 가장 나중에 표시된다.
