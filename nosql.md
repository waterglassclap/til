# CAP 이론
분산 시스템에서는 세가지 속성을 동시에 모두 갖는 것이 불가능하다
  - Consistency
  - Availability
  - Partitions Tolerance

#### Consistency
Every node must **show** same data at same time

#### Availability
Even if specific node **fails**, service must be served
 kinda tricky?

#### Partitions Tolerance
Even if specific node **cannot reach another node**, service must be served

![#f03c15](https://placehold.it/15/f03c15/000000?text=+) Relational
![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Key-value
![#c5f015](https://placehold.it/15/c5f015/000000?text=+) Column-oriented
![#15FFFF](https://placehold.it/15/15FFFF/000000?text=+) Document-oriented

#### CA
**pros :** show same data at same time, even if one node fails, service can be served
**cons :** If specific node cannot reach another node, service cannot be served
- ![#f03c15](https://placehold.it/15/f03c15/000000?text=+) RDBMS(mysql, postgres, etc)
- ![#f03c15](https://placehold.it/15/f03c15/000000?text=+) Aster Data
- ![#f03c15](https://placehold.it/15/f03c15/000000?text=+) Greenplum
- ![#c5f015](https://placehold.it/15/c5f015/000000?text=+) Vertica

>  C : 모든 사람에게 동일한 대답을 해준다. 그래서 동기화 시간이 생기는데, 때문에 좀 느릴 수 있다.
>  A : 노드가 죽어도 서비스가 된다
>  P! : 네트워크 단절나면 서비스가 안된다


#### CP
**pros :** show same data at same time, event if specific node cannot reach another node, service can be served
**cons :** If one node fails, service cannot be served
- ![#c5f015](https://placehold.it/15/c5f015/000000?text=+) BigTable
- ![#15FFFF](https://placehold.it/15/15FFFF/000000?text=+) MongoDB
- ![#c5f015](https://placehold.it/15/c5f015/000000?text=+) HBase
- ![#c5f015](https://placehold.it/15/c5f015/000000?text=+) Hypertable
- ![#15FFFF](https://placehold.it/15/15FFFF/000000?text=+) Terrastore
- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Scalaris
- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Redis
- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Memcache

>  C : 모든 사람에게 동일한 대답을 해준다. 그래서 동기화 시간이 생기는데, 때문에 좀 느릴 수 있다.
>  !A : 노드가 죽으면 서비스가 안된다
>  P : 네트워크 단절이 나도 노드가 살아만 있으면 서비스가 가능은 하다


#### AP
**pros :** event if specific node cannot reach another node or dies, service can be served
**cons :** Might not show same data at the same time
- ![#c5f015](https://placehold.it/15/c5f015/000000?text=+) Cassandra
- ![#15FFFF](https://placehold.it/15/15FFFF/000000?text=+) CouchDB
- ![#1589F0](https://placehold.it/15/1589F0/000000?text=+) Voldemort

> 가. !C : 사용자의 요청들에 다른 대답을 할 가능성이 있다.
> 나. A : 여러 노드간에 데이터가 좀 달라도 상관없다고 했으니 (C를 포기) 하나의 노드에 문제가 있어도 그냥 리턴한다.
> 다. P : 네트워크가 끊어져도 서비스에 문제가 없고, 어짜피 C를 포기했으니 커넥션에 문제가 있는 놈은 없애버리고 잘되는 놈으로만 서비스한다.
