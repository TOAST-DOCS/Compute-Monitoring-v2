## Compute > Monitoring v2 > 콘솔 사용 가이드


## 인스턴스 관리 페이지에서 단일 인스턴스에 대한 상태 조회하기

Toast 콘솔의 'Compute > Instance > 관리 > `조회 대상 인스턴스 선택` > Monitoring 탭'에서는 해당 인스턴스의 모니터링 그래프를 조회할 수 있습니다.

> [알림]
> Monitoring v2 서비스 제공 이전에 생성된 인스턴스에 대해 본 기능을 사용하기 위해서는, 해당 인스턴스의 'Monitoring 탭'에서 제공되는 설치 가이드를 따라 에이전트를 설치해야 합니다.<br>
> 에이전트 설치 후 'Monitoring 탭'에서 그래프가 노출되면, 그 시점부터 Monitoring v2의 기능을 활용할 수 있게 됩니다.


제공되는 그래프는 다음과 같습니다.

| 그래프 | 설명  | 
|:--------|-------|
|CPU 사용률    <br>![cpu usage image <](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_001.jpg)    | softirq: 소프트웨어 인터럽트 처리에 소요된 CPU 사용률<br>irq: 하드웨어 인터럽트 처리에 소요된 CPU 사용률<br>sys: 커널 모드 작업에 소요된 CPU 사용률<br>usr: 유저 모드 작업에 소요된 CPU 사용률<br>iowait: 디스크 I/O 요청으로 인한 대기 상태에 소요된 CPU 사용률<br>steal: 가상(인스턴스) CPU가 물리 CPU 할당을 위한 대기 상태에 소요된 CPU 사용률<br>%nice: nice 명령을 통해 우선 순위가 변경된 프로세스 처리에 소요된 CPU 사용률 |
|CPU 부하      <br>![cpu load image <](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_002.jpg)     | load1: 지난 1분 동안 CPU 사용을 위해 대기한 평균 프로세스 개수<br>load5: 지난 5분 동안 CPU 사용을 위해 대기한 평균 프로세스 개수<br>load15: 지난 15분 동안 CPU 사용을 위해 대기한 평균 프로세스 개수<br> *[참고] windows 인스턴스에서는 그래프는 노출되지만 데이터는 제공되지 않습니다.* |
|Memory 사용률 <br>![memory usage image <](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_003.jpg) | pused: 메모리 사용률<br>swappused: 스왑 사용률<br>*[참고] linux 인스턴스에서의 메모리 사용률 계산 시 buffer 및 cache 영역은 사용 가능한 영역으로 간주합니다.* |
|Disk 사용률   <br>![disk usage image <](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_004.jpg)   | io: Disk 장치 사용률<br> used: Disk 저장 공간 사용률<br>[참고] io 및 used는 파일 시스템(혹은 디스크 파티션) 별로 제공됨 |
|Disk 전송률   <br>![disk i/o image <](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_005.jpg)     | read: 디스크 읽기 전송률<br>write: 디스크 쓰기 전송률<br>[참고1] read 및 write는 파일 시스템(혹은 디스크 파티션) 별로 제공됨<br>[참고2] 기본 단위는 Bps(Bytes per Sec)이며, 크기에 따라 y축 단위가 변환됨 |
|Network 전송률<br>![network i/o image <](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_006.jpg)  | In: 네트워크 읽기 전송률<br>Out: 네트워크 쓰기 전송률<br>[참고1] In 및 Out은 네트워크 장치 별로 제공됨<br>[참고2] 기본 단위는 bps(Bits per Sec)이며, 크기에 따라 y축 단위가 변환됨 |

여기서 제공되는 모든 그래프는 '-5분 ~ 조회 시점'에 속하는 데이터를 보여주며, 그래프 자동 갱신 기능은 제공하지 않습니다.
대신 수동 리프레쉬 버튼을 이용해서, 그래프의 데이터를 현 시점 기준으로 갱신시킬 수 있습니다.



## 복수 인스턴스에 대한 상태 조회하기
Server Details 탭의 각 그래프에서는 선택된 인스턴스에 대한 지표를 동시에 보여줍니다.

## 알림 이력 조회하기

## 알람 정책 설정하기

## 알람 수신 설정하기

## 모니터링 에이전트에 대한 참고 사항
