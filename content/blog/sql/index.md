---
title: SQL
date: "2020-11-03T22:04:37.121Z"
description: "프로그래머스 코딩테스트 문제"
---

# SELECT
### 1. 모든 레코드 조회하기
#### 동물 보호소에 들어온 모든 동물의 정보를 ANIMAL_ID순으로 조회하는 SQL문을 작성해주세요.
```
SELECT *
FROM ANIMAL_INS
ORDER BY ANIMAL_ID;
```

### 2. 역순 정렬하기
#### 동물 보호소에 들어온 모든 동물의 이름과 보호 시작일을 조회하는 SQL문을 작성해주세요. 이때 결과는 ANIMAL_ID 역순으로 보여주세요.
```
SELECT NAME, DATETIME
FROM ANIMAL_INS
ORDER BY ANIMAL_ID DESC;
```

### 3. 아픈 동물 찾기
#### 동물 보호소에 들어온 동물 중 아픈 동물(INTAKE_CONDITION이 Sick 인 경우)의 아이디와 이름을 조회하는 SQL 문을 작성해주세요. 이때 결과는 아이디 순으로 조회해주세요.
```
SELECT ANIMAL_ID, NAME
FROM ANIMAL_INS
WHERE INTAKE_CONDITION = 'Sick';
```

### 4. 어린 동물 찾기
#### 동물 보호소에 들어온 동물 중 젊은 동물(INTAKE_CONDITION이 Aged가 아닌 경우)의 아이디와 이름을 조회하는 SQL 문을 작성해주세요. 이때 결과는 아이디 순으로 조회해주세요.
```
SELECT ANIMAL_ID, NAME
FROM ANIMAL_INS
WHERE INTAKE_CONDITION <> 'Aged'
ORDER BY ANIMAL_ID;
```

### 5. 동물의 아이디와 이름
#### 동물 보호소에 들어온 모든 동물의 아이디와 이름을 ANIMAL_ID순으로 조회하는 SQL문을 작성해주세요.
```
SELECT ANIMAL_ID, NAME
FROM ANIMAL_INS
ORDER BY ANIMAL_ID;
```

### 6. 여러 기준으로 정렬하기
#### 동물 보호소에 들어온 모든 동물의 아이디와 이름, 보호 시작일을 이름 순으로 조회하는 SQL문을 작성해주세요. 단, 이름이 같은 동물 중에서는 보호를 나중에 시작한 동물을 먼저 보여줘야 합니다.
```
SELECT ANIMAL_ID, NAME, DATETIME
FROM ANIMAL_INS
ORDER BY NAME ASC, DATETIME DESC;
```

### 7. 상위 n개 레코드
#### 동물 보호소에 가장 먼저 들어온 동물의 이름을 조회하는 SQL 문을 작성해주세요.
```
-- subquery
SELECT NAME
FROM ANIMAL_INS
WHERE DATETIME = (SELECT MIN(DATETIME) FROM ANIMAL_INS);
```

# SUM, MAX, MIN
### 1. 최댓값 구하기
#### 가장 최근에 들어온 동물은 언제 들어왔는지 조회하는 SQL 문을 작성해주세요.
```
SELECT MAX(DATETIME) as 시간
FROM ANIMAL_INS;
```

### 2. 최솟값 구하기
#### 동물 보호소에 가장 먼저 들어온 동물은 언제 들어왔는지 조회하는 SQL 문을 작성해주세요.
```
SELECT MIN(DATETIME) as 시간
FROM ANIMAL_INS;
```

### 3. 동물 수 구하기
#### 동물 보호소에 동물이 몇 마리 들어왔는지 조회하는 SQL 문을 작성해주세요.
```
SELECT COUNT(ANIMAL_ID)
FROM ANIMAL_INS;
```

### 4. 중복 제거하기
#### 동물 보호소에 들어온 동물의 이름은 몇 개인지 조회하는 SQL 문을 작성해주세요. 이때 이름이 NULL인 경우는 집계하지 않으며 중복되는 이름은 하나로 칩니다.
```
-- 단, COUNT(*) 는 null값을 포함하여 집계한다.
SELECT COUNT(DISTINCT(NAME))
FROM ANIMAL_INS;
```

# GROUP BY
### 1. 고양이와 개는 몇 마리 있을까
#### 동물 보호소에 들어온 동물 중 고양이와 개가 각각 몇 마리인지 조회하는 SQL문을 작성해주세요. 이때 고양이를 개보다 먼저 조회해주세요.
```
SELECT ANIMAL_TYPE , COUNT(*)
FROM ANIMAL_INS
GROUP BY ANIMAL_TYPE
ORDER BY ANIMAL_TYPE;
```

### 2. 동명 동물 수 찾기
#### 동물 보호소에 들어온 동물 이름 중 두 번 이상 쓰인 이름과 해당 이름이 쓰인 횟수를 조회하는 SQL문을 작성해주세요. 이때 결과는 이름이 없는 동물은 집계에서 제외하며, 결과는 이름 순으로 조회해주세요.
```
SELECT NAME, COUNT(NAME)
FROM ANIMAL_INS
GROUP BY NAME
HAVING COUNT(NAME) > 1
ORDER BY NAME;
```
