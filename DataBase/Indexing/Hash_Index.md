# Hash index

## Basic information
- bucket : unit of storage containing one or more entries (대부분 disk block)
  - Hash function을 통해 구한 search-key value를 이용하여 bucket을 얻는다.
- Hash function : search-key value K를 bucket의 address로 mapping 해주는 function
- Bucket은 여러 entry를 담고 있기 때문에 bucket을 결국에 sequentially하게 검사해야 함.
- Hash index 의 경우 bucket들은 record에 대한 주소값을 저장한다.
- hash file-organization의 경우 bucket은 record를 store 한다. (Hash function이라기 보다는 attribute를 key로 사용)
- hash index
![Hash indexes](https://user-images.githubusercontent.com/105041834/194301052-c09624ea-9d06-4070-af79-6092bbbffa4b.jpg)
- hash file organization
![Hash file organization](https://user-images.githubusercontent.com/105041834/194301067-2f96b347-bbf6-43b5-a755-cc18009b5497.jpg)

## Bucket issues
Bucket의 경우 크기가 한정이 되어 있기 때문에 overflow가 발생할 수 있다.
- reason
  - bucket의 개수가 크지 않을 경우
  - record의 distribution이 몰릴 경우 (hash function 수정 필요)
- Solution
  - Overflow chaining : bucket이 overflow가 일어날 경우 linked list로 구현(closed addressing)

## Comparison of Ordered Indexing and Hashing
- Hashing의 경우 특정 record 즉, (=) operator를 사용하는 query에 유리하다.
- Ordered Index의 경우 range query를 사용할 때 유리하다.

##