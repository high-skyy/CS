# Entity-Relationship Modeling (Conceptual Design)

> Example
![E-R modeling](https://user-images.githubusercontent.com/105041834/214232976-61e41b39-fe08-46ee-a0d2-adeb860ed839.jpg)
- Entity set depicted as square / Relationship depicted as a diamond.

- A database can be modeled as : a collection of entities and relationships among entities
> Database 는 entity(record) 의 collection 과 이들 간의 관계로 설게 할 수 있다.

## Design flow
1. Identify entity sets
2. Remove duplicate entity sets
3. List the attributes of each entity set
4. Mark the primary keys
5. Define the relationship sets
6. Describe the cardinality and optionality of the relationship sets
7. Remove redundant relationship sets

## Components
### Entity set
- Entity : object that exists and is distinguishable from other objects
- Entities have attributes
  - Example : people have names and addresses
- entity set : set of entities of the same type that share the same properties
  - Example : set of all persons, companies, trees, holidays

> Entity 라는 것은 하나의 row(record) 라고 생각하면 되고 entity set은 하나의 table 이라고 생각하면 된다.

### Attribute
- Domain : the set of permitted values of each attribute
- Attribute types
  - Simple and composite attributes
  - Single-valued and multivalued attributes (보통 multivalued attribute 는 허용하지 않는다.)
  - Derived attributes (Can be computed from other attributes)

> Domain 은 Table 에서 attribute constraint 의 집합이라고 생각하면 된다.

### Relationship Sets
- Relationship : association among several entities
- Relationship set : set of relationships of the same type that share the same properties
- Detail
  - An attribute can also be property of a relationship set.

> 요약 : Relationship 은 entity(row / record) 사이의 관계를 의미한다.

#### Representing Relationship Sets
- Many-to-many relationship set : schema with attributes for the primary keys of the two participating entity sets and any descriptive attributes of the relationship set.
  - 각각 table 에서 primary key 를 얻어 오고 foreign key 로 referencing 할 수 있도록.
- Many-to-one and one-to-many relationship sets that are total on the many-side can be represented by adding an extra attribute to the "many" side, containing the primary key of the "one" side
  - 추가 적인 attribute 를 "many" side 에 집어 넣는 형태로 구현 한다. (foreign key)
  - one-to-one 의 경우 에는 어떠한 쪽에 놓아도 상관이 없다.

## Foreign key
The FOREIGN KEY constraint is used to prevent actions that would destroy links between tables.
A FOREIGN KEY is a field (or collection of fields) in one table, that refers to the PRIMARY KEY in another table.
The table with the foreign key is called the child table, and the table with the primary key is called the referenced or parent table.
> Foreign key 의 경우는 다른 table의 primary key 를 참조하기 때문에 부모 table 에 해당 record 가 없을 경우의 integrity 를 유지시켜준다.

### Usage of Foreign key
- Performance
  - Foreign keys don't improve performance, at least not directly.
  - The performance gain is achieved by the use of indexes
> Foreign key 자체적으로는 performance 에 큰 영향이 없지만 index 를 통해서 performance 를 증가 시킬 수 있음.

- Cascading deletes
  - Inherent to setting **ON DELETE CASCADE** on the foreign key.

- Integrity
  - 가장 중요한 점은 신뢰성이 높아진다는 것이다. (orphan 이 없음)
  
## Cardinality Constraints
- Express the number of entities to which another entity can be associated via a relationship set
> 각 entity(record / row) 와 관련된 entity 의 갯수

### 종류
- one to one
  - one entity is at most associated with one entity
- many to many
  - (bidirectionally) one entity is associated with several (including 0) entities
- one to many
  - one entity is associated with several (including 0) entities
- Total participation : every entity(record) in the entity set participates in at least one relationship in the relationship set
- Partial participation : some entities may not participate in any relationship in the relationship set.

## Keys
- Super key : set of one or more attributes whose values uniquely determine each entity
  - 유일한 entity(record) 를 정의하는 attribute 들의 집합 
- Candidate key : entity set is a minimal super key
  - Attribute 의 갯수가 최소가 되는 superkey
- Primary key : Candidate key 중에 선택한 primary key.


## Reference
- [Reference](https://www.guru99.com/er-diagram-tutorial-dbms.html)
- [Reference](https://www.w3schools.com/sql/sql_foreignkey.asp)
- [Reference](https://softwareengineering.stackexchange.com/questions/375704/why-should-i-use-foreign-keys-in-database)
- [Reference](학교 ppt 자료)