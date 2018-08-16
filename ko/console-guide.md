## Compute > Monitoring v2 > 콘솔 사용 가이드


## 인스턴스 관리 페이지에서 단일 인스턴스에 대한 상태 조회하기

Toast 콘솔의 'Compute > Instance > 관리 > `조회 대상 인스턴스 선택` > Monitoring 탭'에서는 해당 인스턴스의 모니터링 그래프를 조회할 수 있습니다.

> [알림]
> Monitoring v2 서비스 제공 이전에 생성된 인스턴스에 대해 본 기능을 사용하기 위해서는, 해당 인스턴스의 'Monitoring 탭'에서 제공되는 설치 가이드를 따라 에이전트를 설치해야 합니다.<br>
> 에이전트 설치 후 'Monitoring 탭'에서 그래프가 노출되면, 그 시점부터 Monitoring v2의 기능을 활용할 수 있게 됩니다.


`여기에 모니터링 탭 포함된 이미지 추가(수동 리프레쉬 버튼 적용 후)`

각 그래프에 대한 설명은 다음과 같습니다.

| 그래프 | 설명  | 
|:--------|-------|
|CPU 사용률    <br>![cpu usage image <](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_001.jpg)    | sys: 커널 모드 작업에 소요된 CPU 사용률<br>usr: 유저 모드 작업에 소요된 CPU 사용률 |
|CPU 부하 평균 <br>![cpu load image <](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_002.jpg)     | load1: 지난 1분 동안 CPU를 사용(대기 상태 포함)한 프로세스 개수의 평균<br>load5: 지난 5분 동안 CPU를 사용(대기 상태 포함)한 프로세스 개수의 평균<br>load15: 지난 15분 동안 CPU를 사용(대기 상태 포함)한 프로세스 개수의 평균<br> *[참고] 본 지표는 linux 운영체제 전용 지표입니다.<br>(windows 인스턴스에서는 그래프는 노출되지만 데이터는 제공되지 않습니다.)* |
|Memory 사용률 <br>![memory usage image <](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_003.jpg) | pused: 메모리 사용률<br>swappused: 스왑 사용률<br>*[참고] linux 인스턴스에서의 메모리 사용률 계산 시 buffer 및 cache 영역은 사용 가능한 영역으로 간주합니다.* |
|Disk 사용률   <br>![disk usage image <](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_004.jpg)   | io: Disk 장치 사용률<br> used: Disk 저장 공간 사용률<br>[참고] io 및 used는 파일 시스템(혹은 디스크 파티션) 별로 제공됨 |
|Disk 전송률   <br>![disk i/o image <](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_005.jpg)     | read: 디스크 읽기 전송률<br>write: 디스크 쓰기 전송률<br>[참고1] read 및 write는 파일 시스템(혹은 디스크 파티션) 별로 제공됨<br>[참고2] 기본 단위는 Bps(Bytes per Sec)이며, 크기에 따라 y축 단위가 변환됨 |
|Network 전송률<br>![network i/o image <](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_006.jpg)  | In: 네트워크 읽기 전송률<br>Out: 네트워크 쓰기 전송률<br>[참고1] In 및 Out은 네트워크 장치 별로 제공됨<br>[참고2] 기본 단위는 bps(Bits per Sec)이며, 크기에 따라 y축 단위가 변환됨 |

여기서 제공되는 모든 그래프는 '조회 시점을 기준으로 지난 5분 간의 데이터'를 제공하며, 자동 갱신 기능은 제공되지 않습니다.
대신 리프레쉬 버튼을 이용해서, 최신 데이터 기반의 그래프를 조회할 수 있습니다. (수동 갱신 기능 제공)



## 복수 인스턴스에 대한 상태 조회하기
Server Details 탭(아래 그림)의 각 그래프에서는 선택한 인스턴스에 대한 지표를 동시에 보여줍니다.
![server details image<](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_007.jpg)

### 인스턴스 목록 (화살표 1 영역)
에이전트 구동 이력이 있는 인스턴스의 목록이 제공됩니다.
> [참고]
> 에이전트 구동 이력이 있으나 현재 에이전트가 종료된 인스턴스, 혹은 종료 상태의 인스턴스도 해당 목록에 포함됩니다. 
> 이와 같은 상태의 인스턴스는 목록의 상태 필드 값이 'inActive'로 표시됩니다.

원하는 인스턴스를 목록에서 선택하면, 그래프에 자동으로 반영됩니다.
복수의 인스턴스를 선택하는 경우, 각 그래프 별로 해당 인스턴스들에 대한 정보가 모두 표시됩니다.

인스턴스 목록을 통해서도 각 인스턴스에 대한 기본 정보 및 리소스 사용률(조회 시점 기준)을 확인할 수 있습니다.
또한 모든 필드에 대한 검색 기능을 통해, 원하는 대상만을 쉽게 골라서 볼 수 있습니다.

### 그래프 (화살표 2 영역)
제공되는 그래프 종류는 인스턴스의 모니터링 탭을 통해 제공되는 것과 동일합니다.
단, 
### 조회 기간 지정 (화살표 3 영역)

### 그래프 갱신 주기 설정 (화살표 4 영역)

## 알림 이력 조회하기

## 알람 정책 설정하기

## 알람 수신 설정하기

## 모니터링 에이전트에 대한 참고 사항
