#### PACELC
> if there is a partition (P) how does the system tradeoff between availability and consistency (A and C);
> else (E) when the system is running as normal in the absence of partitions, how does the system tradeoff between latency (L) and consistency (C)?

다시 말해, 장애 상황 (P)일 때는 Availability와 Consistency중 하나를 선택해야 하며, 장애 상황이 아닐 (E) 때는 Latency와 Consistency중 하나를 선택해야 한다는 것이다.

- **HBase** : PC/EC
> 장애 상황이면 Availability 대신 Consistency를 택함. 장애 상황이 아니어도 Latency를 위해 Consistency를 선택.

- **Cassandra** : PA/EL 가능
> 설정에 따라 Eventual Consistency를 가지는데, 이 경우 PA/EL.
> 장애 상황이면 가능한 노드에만 데이터를 반영하고 정상으로 복구되면 필요한 노드에 데이터를 모두 반영함.
> 장애 상황이 아니어도 Latency를 위해 모든 노드에 데이터를 반영하지 않음.

- **Brewer가 제시한 가상의 분산시스템** : PA/EC
> 정상적인 경우에는 모든 노드에서 같은 메세지를 볼 수 있도록 쓰기 연산이 일어남.
> 그러나 장애 상황인 경우, 이를 판단하여 일단 접근 가능한 만큼만 데이터를 반영함. 결과적으로 시스템은 디운되지 않지만 절단된 노드들 끼리는 데이터를 주고 받지 못하게 된다.
> 장애상황이 복구되면 이를 감지하여 전달하지 못한 데이터를 반영한다. 장애상황일때에만 C를 포기하고 보통의 상황에서는 강력한 C를 가져간다.

- **PNUTS** : PC/EL
> 장애상황일 때는 C를 위해 A를 희생하지만, 평소에는 L을 위해 C를 희생함.
> 시스템이 정상일 때에도 C를 충족시키지 못하는데 네트워크 장애일 때 C를 위해 A를 포기한다니 말이 안 되는 것 같지만, 여기서 PC의 의미는 평소만큼의 C를 보장하기 위해 A를 희생시킨다는 의미로 받아들이면 된다.
> PNUTS의 Consistency Level은 Timeline Consistency이다. 일반적으로 생각하는 Consistency보다는 약하지만, 장애상황일 때에도 정상상황일 때와 같은 Consistency Level을 보장하기 위해 요청 자체를 실패시킨다.
