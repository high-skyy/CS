# Indexing of Spatial Data

## Spatial Data
- Database가 line, polygon 또는 raster image를 불러올 수 있다.
  - Allows relational DB to store and retrieve spatial information
  - Queries can use spatial conditions (e.g. contain, overlaps)
  - queries can mix spatial and nonspatial conditions

## efficient query types
- Nearest neighbor queries
  - Given a point or an object, find the nearest object that satisfies given condistions
- Range queries
  - Deal with spatial regions, ask for objects that lie partially or fully inside a specified region.
- Queries that compute intersections or unions of regions
- Spatial join
  - two spatial relations with the location playing the role of join attribute

## Indexing of Spatial Data
![example](https://user-images.githubusercontent.com/105041834/194305358-688fd13d-cc64-4070-b16e-0cfeb3e94853.jpg)

### k-d tree
- Each level of a k-d tree partitions the space into two.
  - Choose one dimension for partitioning at the root level of the tree
> 각 level마다 공간을 2개 씩 나누고 level을 한 단계씩 내려갈 때 마다 하나의 공간씩 선택을 한다.
- 모든 point들을 대략적으로 반씩 나누어서 공간을 활용한다.
- 설정한 point의 개수보다 node가 가지고 있는 point의 개수가 적을 때 멈춘다.
- k-d-b tree
  - K-d tree랑 동일한데 공간을 한번에 2개 씩 나누는 것이 아닌 한번에 여러 개로 나눌 수 있도록한다.

### Division of Space by Quadtrees
- Each node of a quadtree is associated with a rectangular regoin of space the top node is associated with the entire target space
- Each non-leaf nodes divides its region into four equal sized quadrants
- leaf nodes have between zero and some fixed maximum number of points
> root노드는 전체 공간을 의미하고 level을 하나씩 내려갈 때마다 공간을 4등분한다.

![quadtress](https://user-images.githubusercontent.com/105041834/194307516-4803b042-0f12-44ef-85d1-5084cc4eaec7.jpg)

### R-Trees
- R-Trees are a N-dimenstional extension of B+-trees, useful for indexing sets of rectangles and other polygons
- Basic idea
  - B+-tree node 하나당 직사각형의 형태를 띠는 interval로 만든다.
- Bounding box : minimum sized rectangle that contains all the rectangles/polygons associated with the node
![R-tree example](https://user-images.githubusercontent.com/105041834/194308167-e4f422c0-02a9-45dd-a9ff-24301ef4bccc.jpg)

#### Search in R-trees
- Find data items intersecting a given query point/region
  - If the node is a leaf node, output the data items whose keys intersect the given query point/region
  - Else, for each child of the current node whose bounding box intersects the query point/region, recursively serach the child
> 위 그림에서는 bounding box의 level이 없지만 bounding box를 매우 작은 단위로 잡는게 더 나을것 같기도 하다.
> Bounding box를 따라서 tree를 내려가고 결국 해당 영역들의 비교를 통해 구현한다.