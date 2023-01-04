# Normalization (정규화)
테이블 간에 중복된 data를 허용하지 않는다는 것이다. 중복된 데이터를 허용하지 않는다는 것이다.
중복된 데이터를 허용하지 않음으로써 무결성(integrity)를 유지할 수 있으며, DB의 저장 용량
역시 줄일 수 있다.

## 제1 정규화
테이블의 컬럼이 원자갑(Atomic Value, 하나의 값)을 갖도록 테이블을 분해하는 것이다.

![1 정규화 ex_1](https://user-images.githubusercontent.com/105041834/210511621-f4b517df-7060-45d6-a603-589ff657547d.jpg)

위의 여러 개의 취미를 가지고 있기 때문에 아래로 바꿔야 지만 제 1 정규화를 만족한다.

![1 정규화 ex_2](https://user-images.githubusercontent.com/105041834/210511630-c6f1b0cb-469d-4db4-9afb-636ff276b0c1.jpg)

## 제2 정규화
제 1 정규화를 진행한 테이블에 대해 완전 함수 종속을 만족하도록 테이블을 분해하는 것이다.
> 기본키의 부분집합이 어떤 다른 att도 결정해서는 안된다. 기본키 전체가 있어야 나머지 att가 결정 될 수 있도록 한다.

![2 정규화 ex_1](https://user-images.githubusercontent.com/105041834/210512244-a1b66ea7-0879-40f4-92fb-d1982349c072.jpg)

위의 경우는 primary key 가 (학생번호, 강좌이름)이다. 그런데 강의실은 강좌이름에 대해서 결정되기
때문에 아래와 같이 바꿔야지만 2 정규화를 만족 할 수 있다.

![2 정규화 ex_2](https://user-images.githubusercontent.com/105041834/210512254-96354bc4-28ef-49d5-b2eb-a2d833bc1b73.jpg)

## 제 3 정규화
제 2 정규화를 진행한 테이블에 대해 이행적 종속을 없애도록 테이블을 분해하는 것이다.

> 이행적 종속 : A -> B, B -> C 가 성립할 때 A -> C가 성립되는 것을 의미한다. 

![3 정규화 ex_1](https://user-images.githubusercontent.com/105041834/210514531-599c7c2f-8b8c-4c53-b79c-d911011ed110.jpg)

학생번호가 강좌이름을 결정하고 강좌이름이 수강료를 결정하기 때문에 이를 분해하여 아래와 같이 바꾼다.

![3 정규화 ex_2](https://user-images.githubusercontent.com/105041834/210514541-c8d00d62-94a0-4b89-a049-8a3e45722383.jpg)

> ex) 501번 학생이 스포츠경영학으로 강좌를 바꾸게 되면 수강료 또한 바꿔야 하지만 이의 불편함이
> 있기 때문에 아예 2개로 나눠서 강좌이름으로 수강료를 참조하도록 한다.

## BCNF 정규화
BCNF 정규화란 제 3 정규화를 진행한 테이블에 대해 모든 결정자가 후보키가 되도록 테이블을 분해한다.

![BCNF ex](https://user-images.githubusercontent.com/105041834/210515426-477e5295-48aa-44c3-aac1-f4061c8be6b2.jpg)

교수가 특강이름을 결정하는 결정자 이지만 후보키(Candidate key)가 아니다. 따라서 이를 아래와 같이
분해하면 모든 결정자가 candidate key가 될 수 있도록 한다.

![BCNF ex_2](https://user-images.githubusercontent.com/105041834/210515435-58c1e7f3-db75-4a86-a006-0eedcdbe22cc.jpg)


## Reference
- [Reference](https://mangkyu.tistory.com/110)