# 글로벌로 서비스되는 게임의 백 엔드 아키텍처

##해외로 서비스되는 게임이 늘어날수록 글로벌 플레이어에게 어떻게 더 양질의 서비스를 제공할 것인지가 과제로 대두됩니다. 실제 글로벌 서비스 게임의 프로젝트에서는 주로 다음과 같은 아키텍처를 많이 볼 수 있습니다.
#1，	서버 프록시미티 아키텍처, 즉 파티션 서버 아키텍처

<img width="391" alt="image" src="https://user-images.githubusercontent.com/92770458/142785916-d43017f8-6607-453a-a1f5-4a22897e4be3.png">

###파티션 서버 아키텍처는 그 명칭이 시사하는 바와 같이 각 지역에 배틀 서버가 배치되어 있고 플레이어는 자신과 가까운 배틀 서버에 액세스합니다. 물리적으로 서로 다른 에어리어의 플레이어를 분리합니다.
배틀 서버를 근접 배치할 경우 지역 내의 플레이어를 하나의 배틀 서버에 배치하여 플레이하게 되므로 플레이어 간의 레이턴시가 낮아지면서 더 나은 체험이 가능해진다는 장점이 있으며, 이는 경기성 높은 FPS 게임에 적합합니다.
하지만 백 엔드에서의 매칭이나 스케줄링의 로직이 복잡해지고 플레이어가 어느 서버에 액세스했는지를 판단하기 위해 속도 계측이나 스케줄링 등의 알고리즘이 필요해진다는 점을 단점으로 꼽을 수 있습니다. 동시에 서로 다른 지역의 플레이어끼리 매칭시켜 대전하는 것도 불가능해져 즐거움이 반감됩니다.

#2，	글로벌 서버 아키텍처
<img width="387" alt="image" src="https://user-images.githubusercontent.com/92770458/142785934-21d45d9a-34dd-400e-b58d-59dcb663ccec.png">

###글로벌 서버 아키텍처
###10년 전 조사에서는 20년 후에 플레이어가 가장 기대하는 게임 모드의 1위가 ‘글로벌 서버’였는데, 지금은 클라우드나 네트워크 기술의 진보에 따라 글로벌 서버 아키텍처를 채용한 게임이 늘어나고 있습니다.
원리는 간단합니다. 배틀 서버의 글로벌 클러스터를 중앙에 배치하고 전 세계의 플레이어가 게임에 액세스할 수 있도록 호스팅합니다.
아키텍처가 심플해져 운용 및 보수, 관리 비용을 줄일 수 있다는 뚜렷한 장점이 있습니다. 또한 백 엔드 매칭이나 스케줄링, 속도 계측 등을 담당하는 로직이나 모듈이 불필요해져 시스템의 신뢰성이 대폭으로 향상되었습니다. 전 세계의 플레이어가 팀을 짜서 동시에 플레이할 수 있다고 생각하면 가슴이 뜁니다.
반면에 주로 글로벌 네트워크의 레이턴시가 높아 특히 네트워크 품질이 불안정한 일부 지역에서 사용감이 떨어진다는 단점도 있습니다. 따라서 현재 글로벌 서버 아키텍처를 가진 게임은 주로 SLG나 RPG 등 레이턴시의 영향을 쉽게 받지 않는 게임이 많은 것 같습니다.

###다음 호에서는 글로벌 서버 아키텍처에 사용되는 구체적인 기술과 전략에 대해 소개하겠습니다.
