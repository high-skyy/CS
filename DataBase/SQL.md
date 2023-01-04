# SQL

## SQL SELECT query 실행 순서 처리 과정
1. FROM (Table을 MM에 올려야 함)
2. ON (JOIN이 있다면 조건식)
3. JOIN (JOIN 실행)
4. WHERE (JOIN된 table에서 선택 / WHERE가 두 개의 table의 att에서 선택 될 수 있음.)
5. GROUP BY (먼저 묶고)
6. Having (GROUP BY 중 선택)
7. SELECT (선택)
8. ORDER BY (순서 정하기)

> 가장 먼저 메모리에 TABLE을 올려야 해서 FROM 그리고 전체가 필요해서 ON(조건) + JOIN 이 일어나고
> 이 중 조건에 맞는 것 선택을 하고 GROUP BY로 묶은 뒤 묶음에 대한 선택 COLUMN 선택 후 ORDER BY 선택

## Window 함수와 집계 함수(Aggregate function)
- 집계함수 : 여러행의 수치를 단 1개의 수치로 반환 (GROUP BY)와 사용
- Window 함수 : 각 행마다 1개의 값을 반환

## GROUP BY and 집계 함수
1. Grouping 할 행의 범위를 정할 때 GROUP BY 를 사용합니다.
2. 특정 열 내의 값을 값을 가지고 행을 합칩니다.
3. GROUP BY에서 명시된 열로만 행을 합칠 수 있습니다.

## Window 함수
1. Grouping을 할 행의 범위를 정할 때 OVER()를 사용합니다.
2. 집계 함수 이외에도 다른 함수와 함께 사용할 수 있습니다.
3. 특정 열 내의 값 이외에도 순위, 퍼센타일 등을 가지고도 행을 합칠 수 있습니다.
4. 기존 행에 변화를 주지 않습니다.
5. 현재 행과 연관 있는 구간만 설정해 계싼할 수 있습니다.

## Detail
- AS 삭제 가능.



## Reference
- [Reference](https://myjamong.tistory.com/172)
- [Reference](https://kimsyoung.tistory.com/entry/SQL-%EB%82%B4-%EC%A7%91%EA%B3%84-%ED%95%A8%EC%88%98-vs-%EC%9C%88%EB%8F%84%EC%9A%B0-%ED%95%A8%EC%88%98-%EC%9C%A0%EC%82%AC%EC%A0%90%EA%B3%BC-%EC%B0%A8%EC%9D%B4%EC%A0%90)