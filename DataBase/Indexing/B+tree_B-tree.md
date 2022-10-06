# B+-tree B-tree

## B+-tree index

### 장점과 단점
- Disadvantage of indexed-sequential files
  - 파일의 크기가 커질수록 performance가 degrade된다. (Block의 overflow가 일어난다.)
  - 전체 파일에 대한 reorganization이 필요하다.
- Advanatage of B+-tree index:
  - 자동적으로 reorganize가 된다.(small, local, changes) (비용도 적게 든다)
  - 실행이 가능하기 위해 모든 file의 reorganization이 필요가 없다.
- Disadvantage of B+-trees
  - Insertion과 삭제가 발생할 때 overhead가 발생하고 tree 자체의 공간도 크다.


![B+-tree](https://user-images.githubusercontent.com/105041834/194281675-26c9f3af-396a-411b-8aa7-36a28e073ea4.jpg)
### 규칙
- root에서 leaf로 가는 모든 경로의 길이는 같다.
- 각 node(root와 leaf제외)는 ceiling(n/2) 에서 n개의 자식을 가질 수 있다.
- leaf node는 ceiling(n-1/2) 에서 n-1 개의 값이 존재한다.
- 특별한 경우
  - roof가 leaf가 아닌 경우 적어도 2개의 children을 갖는다.
  - root가 leaf이면 0에서 부터 (n-1) 개의 값을 가질 수 있다.

### node structure
![B+-tree node structure](https://user-images.githubusercontent.com/105041834/194282634-e963651b-f8ad-4c6c-a551-442ce5bcd97e.jpg)
- K : search-key value
- P : 자식을 가리키는 pointer (non-leaf) buckets of records (leaf node)
- Search-key들은 정렬이 되어 있다. (아니면 tree를 만드는 의미가 없음)

### 특징
- non-leaf levels of the B+-tree form a hierarchy of sparse indices.
- The B+-tree contains a relatively small number of levels
  - Level below root has at least 2*( ceiling(n/2) ) values
  - next level has at least 2*( ceiling(n/2) * ceiling(n/2) ) values
- K개의 search-key가 있으면 tree의 height는 ceiling( log(ceiling(n/2))(K) ) 보다 크지 않다.
- 삽입과 삭제가 logarithmic time이기 때문에 효율적이다.
- Node의 크기는 보편적으로 disk block의 크기와 같고 n은 100 근처이다.
- 모든 node의 access의 경우는 disk I/O가 필요할 수 있기 때문에 height가 작다는 것이 좋다.

### B+-tree File Organization
- Leaf node의 경우는 pointer 대신에 record를 저장한다.(clustered)
- Leaf node are still required to be half full
  - Record의 크기가 pointer 보다 크기 때문에 leaf node에 저장되어 있는 record의 개수는 nonleaf node의 pointer의 개수보다 작다.

### Issues
- 만약 record가 움직이게 되면 record를 가리키는 pointer들이 전부 최신화가 되어야 한다.
- 해결책
  - Record의 pointer 대신 search key를 사용한다.
    - 만약 search key가 non-unique 하다면 record의 id를 사용한다.
    - record의 id를 가지고 record를 찾아야한다는 overhead가 발생한다. (즉 query 비용 증가 + node split 비용 감소)

## b-tree index
B-tree의 경우 search-key가 정확히 한번 보이게 한다.(nonleaf에 한번 보이면 해당 search-key는 더이상 tree에서 보여지지 않는다.)

### node structure

- Leaf node
![B+-tree node structure](https://user-images.githubusercontent.com/105041834/194282634-e963651b-f8ad-4c6c-a551-442ce5bcd97e.jpg)
- non leaf node
![B-tree node](https://user-images.githubusercontent.com/105041834/194287152-d09ad876-9865-4d7e-8ea2-25687be050d8.jpg)
> leaf node가 아닌 경우에는 record file이 있는 bucket을 가리키는 pointer가 필요하다.

### 장점, 단점
#### 장점
- Record를 찾는데 B+-tree 보다 적은 node를 travel 한다. (non leaf node에 bucket pointer가 있다)(B+-tree는 leafnode까지 가야 bucket을 찾을 수 있다.)
#### 단점
- 전체의 search-key중 극히 일부만 일찍 찾아진다.
- non-leaf-node에 bucket pointer까지 저장되어 B+-tree보다 적은 개수가 저장됨 -> height가 높아진다.
- Insertion과 deletion도 더 복잡하고 구현도 힘들다.

## Reference
- [Reference](학교 강의 자료)
- Reference(book) : Database System Concepts (Abraham Silberschatz, Henry F. Korth etc.)