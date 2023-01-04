# Window Functions
SQL의 윈도우 함수란 행과 행 간을 비교, 연산, 정의하기 위한 함수이다. 분석함수 또는 순위함수라고
하기도 한다. 다른 함수들처럼 중첩해서 사용할 수는 없지만 서브쿼리에서는 사용가능하다.

- 윈도우 함수는 GROUP BY 구문과 병행하여 사용할 수 없다.
## Window Funciton 기본 문법
```
SELECT WINDOW_FUNCTION (ARGUMENTS) OVER ([PARTITION BY 칼럼] [ORDER BY 칼럼] [WINDOWING 절] )
FROM 테이블 명;
```

- Arguments : 윈도우 함수에 따라서 0~N개의 인수를 설정한다.
- Partition BY : 전체 집합을 기준에 의해 소그룹으로 나눈다. (Group by 역할)
- ORDER BY : 어떤 항목에 대해서 정렬한다.
- WINDOWING : 행 기준 범위를 정한다. (Row 또는 RANGE WHERE 역할)

## Window Function 종류

![Window 함수 예시](https://user-images.githubusercontent.com/105041834/210501493-88922215-1eaf-4fd3-9702-a4ae43f836ea.jpg)

### Ranking Function
- row_number() : 일렬 번호
  - window partition 내의 행의 순서에 따라 한 행부터 시작하여 각 행에 대해 고유한 일렬 번호를 반환합니다.

## Reference
- [Reference](https://for-my-wealthy-life.tistory.com/48)
- [Reference](https://velog.io/@yewon-july/Window-Function)
- [Reference](https://velog.io/@ena_hong/SQL-Analytic-Function-%EB%B6%84%EC%84%9D%ED%95%A8%EC%88%98)