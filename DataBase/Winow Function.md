# Window Functions
A window function performs a calculation across a set of table rows that are somehow
related to the current row. Unlike regular aggregate functions, use of window function
does not cause rows to become grouped into a single output row - the row retain their seperate identities.
Behind the scenes, the window function is able to access more than just the current row of the query result.

> Window function 의 경우 현재의 row 와 관련이 있는 여러 row 들에 대한 calculation을 한다.
> Aggregate function 과의 주된 차이 점은 window function 의 경우 row 들이 한 개의 output row
> 로 group 되지 않는 다는 점이다.

## Window Funciton 기본 문법
```
SELECT WINDOW_FUNCTION (ARGUMENTS) OVER ([PARTITION BY 칼럼] [ORDER BY 칼럼] [WINDOWING 절] )
FROM 테이블 명;
```

- Arguments : 윈도우 함수에 따라서 0~N개의 인수를 설정한다.
- Partition BY : 전체 집합을 기준에 의해 소그룹으로 나눈다. (Group by 역할)
- ORDER BY : 어떤 항목에 대해서 정렬한다.
- WINDOWING : 행 기준 범위를 정한다. (Row 또는 RANGE WHERE 역할)

### WINDOWING
- ROWS : 부분집합인 window 크기를 물리적 단위로 행의 집합을 지정한다.
- RANGE : 논리적 주소에 의해 행 집합을 지정한다.
- BETWEEN~AND : 윈도우의 시작과 끝 위치를 지정한다.
- UNBOUNDED PRECEDING : 윈도우 시작 위치가 첫 번째 행 임을 의미한다.
- UNBOUNDED FOLLOWING : 윈도우 마지막 위치가 마지막 행임을 의미한다.
- CURRENT ROW : 윈도우 시작 위치가 현재 행임을 의미한다.

## Example
### First example
```
SELECT start_terminal,
       duration_seconds,
       SUM(duration_seconds) OVER
         (PARTITION BY start_terminal ORDER BY start_time)
         AS running_total
  FROM tutorial.dc_bikeshare_q1_2012
 WHERE start_time < '2012-01-08'
```
1. 위의 query 는 start_terminal 에 대해서 grouping 이 일어나고 ordering 이 생긴다.
2. 각 start_terminal value 마다 내부적으로는 start_time에 의해 ordering 이 생긴다.
3. Start_terminal 이 바뀌기 직전 까지 계속 duration seconds에 대하여 sum 을 계산한다.

### Second example
```
SELECT start_terminal,
       start_time,
       duration_seconds,
       ROW_NUMBER() OVER (ORDER BY start_time)
                    AS row_number
  FROM tutorial.dc_bikeshare_q1_2012
 WHERE start_time < '2012-01-08'
```

## Window Function 종류

![Window 함수 예시](https://user-images.githubusercontent.com/105041834/210501493-88922215-1eaf-4fd3-9702-a4ae43f836ea.jpg)

### Ranking Function
- row_number() : 일렬 번호
  - window partition 내의 행의 순서에 따라 한 행부터 시작하여 각 행에 대해 고유한 일렬 번호를 반환합니다.

## Reference
- [Reference](https://for-my-wealthy-life.tistory.com/48)
- [Reference](https://velog.io/@yewon-july/Window-Function)
- [Reference](https://velog.io/@ena_hong/SQL-Analytic-Function-%EB%B6%84%EC%84%9D%ED%95%A8%EC%88%98)
- [Reference](https://mode.com/sql-tutorial/sql-window-functions/)