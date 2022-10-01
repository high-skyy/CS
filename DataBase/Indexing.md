# Clustering and Non-clustering Index

## Basic Concepts
- Indexing mechanisms used to speed up access to desired data
- **Search key** : Attribute or set of attributes used to look up records in a file
> Search key는 table의 attribute를 바탕으로 해당 record를 바로 찾을 수 있게 한다.
- Index file consists of records (index entries)
![1](https://user-images.githubusercontent.com/105041834/193393356-52a18701-15c9-4498-a5c1-67066fa5a67a.jpg)

- **index files** are typically much smaller than the original file
> Index file은 위와 같은 index entries들로 이루어져 있으며 원본 파일 보다 크기가 작기 때문에 사용하기 유용해다.

- Two basic kinds of indices
  - **Ordered Indices** : Search keys are stored in sorted order (ex : 알파벳 순서, 크기 ...)
  - **Hash indices**: Search keys are distributed uniformly across "buckets" using a "hash function"

## Dense Index Files
Index record appears for every search-key value in the file  
> 해당 (search-key로 설정한)attribute의 모든 값 마다 index가 존재한다.

![2](https://user-images.githubusercontent.com/105041834/193393774-531dc9b5-8f25-4fd0-a8b4-b7f9ad4fdc32.jpg)

(E.g. index on ID attribute of instructor relation)

![3](https://user-images.githubusercontent.com/105041834/193393819-1fda0d36-a80a-440b-98e7-949afb70ddd5.jpg)

## Sparse Index Files
Contains index records for only some search-key values.
> 사용이 가능할려면 record(원본 파일의 내용)들이 해당 search-key값에 따라 순서대로 정렬이 되어 있어야 사용이 가능하다.

- 예시
  - To locate a record with search-key value K
    - Find the record with largest search-key value < K
    - Search file sequentially starting at the record to which the index record points

![4](https://user-images.githubusercontent.com/105041834/193394001-d5c8f013-2d39-4d4d-875c-0590a2d0aa21.jpg)

> Search-key value의 값들중 K보다 작으면서 가장 큰 값을 찾는다. 해당 index entry의 주소값을 기준으로 sequentially하게 찾는다.
> (위에서 언급했듯이 이게 가능할려면 원본 table과 해당 index file이 선택한 attribute를 기준으로 순서대로 정렬이 되어 있어야 한다.
> 
> 보통 clustering index가 sparse index의 형태를 띤다.
> 
> non-clustering index에도 사용할 수 있다. multilevel index로 구현이 가능하다. index에 대한 또 index로 표현한다.

## Ordered indices
Index entries are stored sorted on the search key value

### Clustering index(Primary index)
- In a sequentially ordered file, the index whose search key specifies the sequential order of the file
  - The search key of a primary index is usually but not necessarily the primary key
> Clustering index의 경우에는 원본 파일도 sorted가 되어 있고 해당 원본 파일의 특정 attribute(보통 primary key)를 사용하여 index를 만들 때
> 그 index들도 원본 파일의 순서 그대로를 반영(보존)해서 저장이 된다.

### Secondary index(non-clustering index)
Index whose search key specifies an order different from the sequential order of the file (**non-clustering index**)
> non-clustering index의 경우는 search key가 정렬된 형태로 있기는 한데 원본 파일의 정렬된 순서와는 다르다. 
> 
> ex) 원본 파일은 primary key(ex : student ID)를 바탕으로 순서가 정렬되어 있고 non-clustering index file의 경우는 다른 attribute(ex : name)
> 정렬이 되어 있는 경우


## Reference
- 학교 강의 자료
- Book : Database System Concepts (Abraham Silberschatz, Henry F. Koreth etc.)