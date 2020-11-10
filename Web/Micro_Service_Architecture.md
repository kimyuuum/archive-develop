# Micro Service Architecture



하나의 큰 Application을 독립적으로 실행 가능하고, 배포 가능한 단위의 작은 서비스로 쪼개어 변경과 조합이 가능하도록 만든 아키텍쳐입니다.

### Monolithic Architecture

SW의 모든 구성 요소가 한 project에 통합되어있는 형태.

모든 구조가 하나의 project에 묶여있는것. 규모가 커지면, 빌드 시 소요 시간이 늘어난다. 하나의 서비스가 문제가 생길 경우, 다른 서비스에도 영향을 끼친다.

장점

- project에 대해 구조를 간단하게 가져갈 수 있다.
- business 가치를 봤을 때, MSA로 전환하는 비용이 더 크다면 monolithic을 가져갈 것 같다.



</br>



### Micro Service

스스로 돌아갈 수 있는, 독립적 배포가 가능한 작은 서비스입니다. 배포나 확장 관점에서 쉽고 빠르며, 유동적입니다. transaction과 관련된 복잡도는 증가합니다.

1. MSA는 주로 HTTP 통신을 사용한다. Network는 IO를 통해서 다른 서버까지 다녀와야 함에 대한 성능 이슈가 존재하지만, 성능보다는 유지보수에 무게를 둔다면 이는 장점으로 보완 가능하다.
2. MSA는 cloud 환경과 밀접하게 관련이 있다. 각 서비스 마다 다른 서버에 올려야 하는데, 물리 서버를 사용할 경우 관리가 힘들다. cloud를 사용하여 이런 이슈를 AWS와 같은 solution에서 해결해준다.

    금전과 관련한 service는 문제가 발생할 경우, 손실이 크게 작용하므로 두개 이상의 instance에 동일 서비스를 올려 문제를 해결해야 한다. ⇒ instance 개수에 대한 issue 해결 : **auto scaling ( scale out )**

3. MSA는 대용량 트래픽 처리에도 장점을 보이지만, 애자일하게 바뀌는 업무 흐름에 대해서도 유동적으로 처리할 수 있다. 서비스를 Bounded Context 단위로 나누고, Bounded Context는 하나의 Aggregate(합성)를 가지는 것이 좋다.
4. MSA는 데이터의 일관성을 보장하기가 힘들다. 전체 서비스가 엮이면, @Transactional이 적용되지 않기 때문이다.

    ### @Transactional

    Spring에서는 @transactional이라는 annotation만 달아주면, 자동으로 transaction 처리가 가능하다. 그러나 서비스가 각각 나뉘면, transaction 관리가 복잡해진다. 필요하다면 transaction과 관련된 service 로직을 추가해야 한다. 그래서 service 분리 시, transaction의 경계도 고려해야 한다.