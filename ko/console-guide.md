## Compute > Monitoring v2 > 콘솔 사용 가이드


## 인스턴스 관리 페이지에서 단일 인스턴스에 대한 상태 조회하기

Toast 콘솔의 'Compute > Instance > 관리 > `조회 대상 인스턴스 선택` > Monitoring'에서는 해당 인스턴스의 모니터링 그래프를 조회할 수 있습니다.

> [주의]
> 기존 인스턴스(Monitoring v2 서비스 개시 이전에 생성된 인스턴스)에서 본 기능을 사용하기 위해서는 해당 인스턴스의 'Monitoring 탭'에서 제공되는 설치 가이드를 따라 에이전트를 설치해 주셔야 합니다.


제공되는 그래프는 다음과 같습니다.

| 그래프 | 설명  | 
|:--------|-------|
|CPU 사용률    <br>![cpu usage image <](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_001.jpg)    | softirq: 소프트웨어 인터럽트 처리에 소요된 CPU 사용률<br>irq: 하드웨어 인터럽트 처리에 소요된 CPU 사용률<br>sys: 커널 모드 작업에 소요된 CPU 사용률<br>usr: 유저 모드 작업에 소요된 CPU 사용률<br>iowait: 디스크 I/O 요청으로 인한 대기 상태에 소요된 CPU 사용률<br>steal: 가상(인스턴스) CPU가 물리 CPU 할당을 위한 대기 상태에 소요된 CPU 사용률<br>%nice: nice 명령을 통해 우선 순위가 변경된 프로세스 처리에 소요된 CPU 사용률 |
|CPU 부하      <br>![cpu load image <](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_002.jpg)     | load1: 지난 1분 동안 CPU 사용을 위해 대기한 평균 프로세스 개수<br>load5: 지난 5분 동안 CPU 사용을 위해 대기한 평균 프로세스 개수<br>load15: 지난 15분 동안 CPU 사용을 위해 대기한 평균 프로세스 개수 |
|Memory 사용률 <br>![memory usage image <](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_003.jpg) | pused: 메모리 사용률<br>swappused: 스왑 사용률 |
|Disk 사용률   <br>![disk usage image <](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_004.jpg)   | io: Disk 장치 사용률<br> used: Disk 저장 공간 사용률<br>참고: io 및 used는 디스크 파티션 별로 제공됨 |
|Disk 전송률   <br>![disk i/o image <](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_005.jpg)     | read: 디스크 읽기 전송률<br>write: 디스크 쓰기 전송률<br>참고1: read 및 write는 디스크 파티션 별로 제공됨<br>참고2: 기본 단위는 Bps(Bytes per Sec)이며, 크기에 따라 y축 단위가 변환됨 |
|Network 전송률<br>![network i/o image <](http://static.toastoven.net/prod_infrastructure/monitoring/v2/image_006.jpg)  | in: 네트워크 읽기 전송률<br>out: 네트워크 쓰기 전송률<br>참고1: in 및 out은 네트워크 장치 별로 제공됨<br>참고2: 기본 단위는 bps(Bits per Sec)이며, 크기에 따라 y축 단위가 변환됨 |



## 복수 인스턴스에 대한 상태 조회하기
Server Details 탭의 각 그래프에서는 선택된 인스턴스에 대한 지표를 동시에 보여줍니다.

## 알림 이력 조회하기

## 알람 정책 설정하기

## 알람 수신 설정하기
