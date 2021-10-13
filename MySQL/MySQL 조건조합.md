# 논리연산자의 종류
- **AND**
- **OR**
- **NOT**

# AND
복수의 조건을 조합할 경우 사용, 좌우에 항목이 필요한 이항 연산자
```
SELECT * FROM products WHERE a<>0 AND b<>0;
```
>a열과 b열 모두 0이 아닌 행 검색

```
SELECT * FROM products WHERE a=0 AND b=0;
```
>a열과 b열 모두 0인 행 검색

# OR
어느 한쪽이 참이되면 조건식은 참이 된다.
```
SELECT * FROM products WHERE a<>0 OR b<>0;
```
>a열이 0이 아니거나 b열이 0이 아닌 행 검색

```
SELECT * FROM products WHERE a=0 OR b=0;
```
>a열이 0이거나 b열이 0인 행 검색

and, or 같은 경우 공부하는 파이썬의 언어와 사용하는 부분에서 똑같았다.


# AND, OR 사용시 주의할 점
```
SELECT * FROM products WHERE id=1 or 2;
```
이 경우 상수 '2'의 경우 논리 연산으로 항상 참이 되기 때문에 모든 행을 반환하게 된다.

```
SELECT * FROM products WHERE id=1 OR id=2;
```
이렇게 조건식을 입력해야만 id가 1이거나 2인 값을 을 불러와. 1, 2행 모두 반환한다.

## AND와 OR 조합하여 사용
a,b에 데이터가 0, 1, 2 가 있다고 가정해보자
```
SELECT * FROM products WHERE a<>0 AND b<>0; 를 
SELECT * FROM products WHERE a=1 OR a=2 AND b=1 OR b=2; 변경
```
잠깐 보면 똑같은 행을 반환 할 것 같지만 그렇지 않다.
연산자에는 우선순위가 있기 때문이다.
AND 가 OR 보다 우선순위가 있기때문에
```
SELECT * FROM products WHERE a=1 OR (a=2 AND b=1) OR b=2;
```
이러한 형태로 진행된다고 생각하면된다.

그렇기 때문에 AND와 OR 을 조합해서 사용할 경우 OR조건에 괄호를 묶어서 사용해야한다.
```
SELECT * FROM products WHERE (a=1 OR a=2) AND (b=1 OR b=2);
```

# NOT으로 조합