# Bitmap Indices

## Brief information
- Bitmap indices are a special type of index designed for efficient querying on mulitple keys
- Records in a relation are assumed to be numbered sequentially from 0
  - record가 고정된 길이 일 때 좋다.
- 값이 다양하지 않을 때 좋다. (ex : gender)
- array of bits

## How it works
- Bitmap indices are useful for queries on multiple attributes
- Intersection과 Union을 bit연산을 통해 구현할 수 있다.
- example
![bitmap example](https://user-images.githubusercontent.com/105041834/194301907-9524575d-5696-4cf0-a744-5c88018b0fd4.jpg)
> males with income level L1 : 10010 AND 10100 = 10000
- 보통 relation의 size보다 작다.

## Efficient Implementation of Bitmap Operations
- Bitmap은 보통 word(CPU instruction)로 구현한다. (coputest 32 or 64 bits per operation)
- 1의 갯수를 counting하는 것을 빠르게 할 수 있다.
  - 2진수를 1의 갯수로 mapping 시켜주는 array를 미리 만들고 각 byte를 index로 사용하면 이를 쉽게 구현할 수 있다.
  - tradeoff with memory and operation cost
- B+tree의 leaf level에서 tuple-ID 대신에 사용이 가능하다.
  - Matching 되는 record의 갯수가 많을 경우에 좋다.