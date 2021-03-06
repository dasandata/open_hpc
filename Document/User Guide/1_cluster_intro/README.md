[userguide]: https://github.com/dasandata/Open_HPC/tree/master/Document/User%20Guide#-%EB%AA%A9%EC%B0%A8
[ohpc]: http://openhpc.community/
[slurm]: https://slurm.schedmd.com/
[1]: https://github.com/dasandata/Open_HPC/tree/master/Document/User%20Guide/1_cluster_intro

# [# 1. 클러스터 개요][userguide]

안녕하세요 다산데이타 입니다.   

HPC 클러스터를 사용하는 목적과 어떤 구성요소로 되어 있는지 알아 보겠습니다.  


## [## 1.1.  클러스터 사용 목적][1]

|구 분|내  용|
|:-:|---|
| 1 | 다수의 사용자가, 다수의 시스템을 <br> 유휴되는 자원이 없도록 시스템 전체를 효율적으로 사용.|
| 2 | 운영체제 설치, 응용프로그램 및 라이브러리 설치, 사용자 계정 동기화 등 <br> 공통된 시스템 사용환경을 구축하는 작업을 간소화.  |


***

아래 표와 같이 네 가지 상황을 살펴 보겠습니다.  

<img src="https://github.com/dasandata/Open_HPC/blob/master/Document/User%20Guide/images/dasandata_cluster_keymap1.png" width="600">  

***

시스템의 수가 많아질 경우  
OS 와 프로그램 설치 작업이 반복되며,  
변경사항이 발생할 때마다 모든 시스템에 반영하기 위한 작업도 반복적으로 해야 합니다.  

사용자의 수가 많아지는 경우  
다른 사용자가 시스템을 사용중인지, 언제까지 사용하는지 확인하고,  
끝나기를 기다렸다가 작업을 시작해야 하는 상황이 발생 합니다.  

이러한 문제를 해결하고 자원을 효율적으로 사용하기 위해  
 **배포 및 관리도구** 와 **리소스 매니저**가 필요 합니다.  

<img src="https://github.com/dasandata/Open_HPC/blob/master/Document/User%20Guide/images/dasandata_cluster_keymap2.png" width="600">  

<img src="https://github.com/dasandata/Open_HPC/blob/master/Document/User%20Guide/images/dasandata_cluster_keymap3.png" width="600">  

<img src="https://github.com/dasandata/Open_HPC/blob/master/Document/User%20Guide/images/dasandata_cluster_keymap4.png" width="600">  

***

저희는 배포 및 관리도구 와 리소스 매니저를 손쉽게 설치하고 구성할 수 있는  
**[OpenHPC][ohpc]** 를 사용해서 HPC 클러스터를 구성하여 제공하고 있습니다.  
(Resouce Manager는 [SLURM][slurm] 을 사용 합니다.)  

***

## [## 1.2. 클러스터의 구성 요소][1]

HPC 클러스터는 다음과 같은 요소들로 구성되어 있습니다.  

|구분 | 요 소                               | 종 류  |
|:---:|------------------------------------|-------|
| H/W | 독립된 전용(내부) <br> 네트워크      | Ethernet, InfiniBand|
| H/W | 공유 저장소 (스토리지)               | NFS(Network File Sytem), <br> PFS(Parallel File System), DFS(Distributed File System)|
| H/W | 관리 노드 <br> (master, mgmt Node) | 노드배포 와 사용자 계정등록, NFS를 통해 home 디렉토리등 공유 저장소 제공, 관리자만 접속 |
| H/W | 로그인 노드 <br> (login node)      | 사용자들의 클러스터 접속 경로. <br> 자원 관리자를 통하지 않고 간단한 작업 (Debug) 을 돌리거나, <br> 자원 요청 및 작업 제출을 수행하는 위치 |
| H/W | 계산 노드 및 <br> 자원(Resource)   | CPU, Memory (RAM), GPU (VGA Card)|
| S/W | 응용프로그램 <br> 실행환경 관리도구 | Anaconda, Module, <br> Container (Docker, Singularity) |
| S/W | 응용프로그램                       | C, Python, Pytorch, Tensorflow|
| S/W | 자원 관리자(Resource Manager)      | SLURM(Simple Linux Utility Resource Management), <br> PBS(Portable Batch System)|

<img src="https://github.com/dasandata/Open_HPC/blob/master/Document/User%20Guide/images/openhpc-project-overview-and-updates-8-638.jpg">  

***

**자원관리자(Resource Manager)** 는 보통 HPC 클러스터 환경에서만 접할 수 있는 도구로,
기본적으로 아래 그림과 같이(Backfil) 작업의 크기에 따라 가용한 자원에 작업을 분배하고  
자원이 모두 사용중일 때는 **대기열(queue)** 에 작업을 쌓아 두었다가  
사용가능한 자원이 확보되면, 대기하고 있던 작업을 시작시켜주는 역할을 하게 됩니다.

### ### Resource Manager 의 Backfill

<img src="http://docs.adaptivecomputing.com/torque/5-0-1/Content/Resources/Graphics/backfill.gif">  

***

기본적으로 FIFO (First In, First Out) 방식 이지만,  
무분별한 자원 점유를 방지하고 자원을 공정하게 분배 하거나   
특정 사용자 와 그룹의 작업을 우선 배정하는 **우선순위(Priority)** 조정 기능도 지원 됩니다.

### [### SLURM - Priority_and_Fair_Trees](https://slurm.schedmd.com/SLUG19/Priority_and_Fair_Trees.pdf)

<img src="https://github.com/dasandata/Open_HPC/blob/master/Document/User%20Guide/images/SLURM_Priority_and_Fair_Trees.png">

***
## [## 끝][userguide]
