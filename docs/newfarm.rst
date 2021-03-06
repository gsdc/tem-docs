************************
GSDC TEM 신규 데이터 분석 팜
************************

1. EL7 신규 데이터 분석 팜 자원 현황
=============================

+--------------+---------------------------------+---------------------------------------------------------------------------+-----------------+
| Category     | Name                            | Specification                                                             | Resources size  |
+--------------+---------------------------------+---------------------------------------------------------------------------+-----------------+
| Login        | **tem-ui-el7.sdfarm.kr**        | - CPU : Intel(R) Xeon(R) Gold 6150 CPU @ 2.70GHz 18Core * 2 CPUs          | 72 cores (H/T)  |
|              |                                 | - RAM : DDR-4 2,666MHz 16GB * 24EA (384GB)                                |                 |
|              |                                 | - HDD : 12G SAS HDD 1.2TB * 2EA (RAID-1)                                  |                 |
+--------------+---------------------------------+---------------------------------------------------------------------------+-----------------+
| Web-Login    | **tem-cs-el7.sdfarm.kr**        | - CPU : Intel(R) Xeon(R) CPU E5-2697v3 @ 2.60GHz 14Core * 2 CPUs          | 56 cores (H/T)  |
| (CryoSPARC)  |                                 | - RAM : DDR4 8GB * 24 (192GB)                                             |                 |
|              |                                 | - HDD : 12G SAS HDD 1.2TB * 2EA (RAID-1)                                  |                 |
+--------------+---------------------------------+---------------------------------------------------------------------------+-----------------+
| Computing    | tem-ce-el7.sdfarm.kr            | - CPU : Intel(R) Xeon(R) CPU E5-2697v3 @ 2.60GHz 14Core * 2 CPUs          | 56 cores (H/T)  |
| (master)     |                                 | - RAM : DDR4 8GB * 24 (192GB)                                             |                 |
|              |                                 | - HDD : 12G SAS HDD 1.2TB * 2EA (RAID-1)                                  |                 |
+--------------+---------------------------------+---------------------------------------------------------------------------+-----------------+
| Computing    | tem-wn[1001-1002]-el7.sdfarm.kr | - CPU : Intel(R) Xeon(R) Gold 6150 CPU @ 2.70GHz 18Core * 2 CPUs          | 380 cores       |
| (workers)    |                                 | - RAM : DDR-4 2,666MHz 16GB * 24EA (384GB)                                |                 |
|              |                                 | - HDD : 12G SAS HDD 1.2TB * 2EA (RAID-1)                                  |                 |
|              +---------------------------------+---------------------------------------------------------------------------+                 |
|              | tem-wn[1003-1013]-el7.sdfarm.kr | - CPU : Intel(R) Xeon(R) CPU E5-2697v3 @ 2.60GHz 14Core * 2 CPUs          |                 |
|              |                                 | - RAM : DDR4 8GB * 24 (192GB)                                             |                 |
|              |                                 | - HDD : 12G SAS HDD 1.2TB * 2EA (RAID-1)                                  |                 |
|              +---------------------------------+---------------------------------------------------------------------------+-----------------+
|              | tem-gpu[01-05]-el7.sdfarm.kr    | - CPU : Intel® Xeon® CPU E5-2690v4 @ 2.60GHz 14Core * 2 CPUs              | - 140 cores     |
|              |                                 | - RAM : DDR4 16GB * 24 (384GB)                                            | - 10 GPGPUs     |
|              |                                 | - SSD : 6G SATA SSD 800GB * 2EA (RAID-1)                                  |                 |
|              |                                 | - GPU : NVIDIA P100 * 2ea (each tem-gpu[01-03]-el has 2 P100 GPU devices) |                 |
|              |                                 | - GPU : NVIDIA  P40 * 2ea (each tem-gpu[04-05]-el has 2 P40 GPU devices)) |                 |
+--------------+---------------------------------+---------------------------------------------------------------------------+-----------------+
| Storage      | Dell EMC Isilon NAS             | Network attached storage 800 TB                                                             |
+--------------+---------------------------------+---------------------------------------------------------------------------+-----------------+
| Total                                          | 612 CPU cores (physical), 10 GPGPUs, 800TB Storage                                          |
+--------------+---------------------------------+---------------------------------------------------------------------------+-----------------+

2. 신규 분석 팜 관리 소프트웨어
========================

+--------------+------------------------+------------------------------------------------------------+--------------------------------+
| Category     | Name                   | Description                                                | Version                        |
|              |                        |                                                            | (module path)                  |
+--------------+------------------------+------------------------------------------------------------+--------------------------------+
| OS           | Scientific Linux       | Operating system                                           | 7.9                            |
+--------------+------------------------+------------------------------------------------------------+--------------------------------+
| System       | Environment module     | - Module environment                                       | v4.4.1                         |
| M/W          |                        | - https://modules.readthedocs.io/en/latest                 |                                |
|              +------------------------+------------------------------------------------------------+--------------------------------+
|              | OpenPBS(torque)        | - Cluster resources management                             | v6.1.2                         |
|              |                        | - http://www.adaptivecomputing.com/products/torque         |                                |
|              +------------------------+------------------------------------------------------------+--------------------------------+
|              | OpenMPI                | - Messaging Pass Interface(MPI)                            | | v4.0.3                       |
|              |                        | - Reference implementation for MPI standard                | | (mpi/gcc/openmpi/4.0.3)      |
|              |                        | - https://www.open-mpi.org                                 |                                |
|              +------------------------+------------------------------------------------------------+--------------------------------+
|              | cuda                   | - Compute Unified Device Architecture(CUDA)                | 9.2 (cuda/9.2)                 |
|              |                        | - NVIDIA CUDA Runtime & Toolkit                            |                                |
|              |                        | - https://developer.nvidia.com/cuda-toolkit                |                                |
|              +------------------------+------------------------------------------------------------+--------------------------------+
|              | Anaconda               | - Python based virtual environemnt                         | 2020.11 (conda/2020.11)        |
|              |                        | - https://www.anaconda.com/                                |                                |
|              +------------------------+------------------------------------------------------------+--------------------------------+
|              | Python                 | - Python runtime                                           | v2.7.5                         |
+--------------+------------------------+------------------------------------------------------------+--------------------------------+


3. 데이터 분석 도구
===============

+----------+-------------+--------------------------------------------------------------------+----------------------------------------+
| Category | Name        | Description                                                        | Version                                |
|          |             |                                                                    | (module path)                          |
+----------+-------------+--------------------------------------------------------------------+----------------------------------------+
| Tools    | **Relion**  | | A stand-alone computer program that employs an empirical Bayesian|                                        |
|          |             | | approach to refinement of (multiple) 3D reconstructions or 2D    |                                        |
|          |             | | class averages in electron cryo-microscopy (cryo-EM).            |                                        |
|          |             |                                                                    | | v3.0.7                               |
|          |             |                                                                    | | (apps/relion/cpu/3.0.7)              |
|          |             |                                                                    | | (apps/relion/gpu/3.0.7)              |
|          |             | - https://www3.mrc-lmb.cam.ac.uk/relion/index.php                  |                                        |
|          |             |                                                                    |                                        |
|          |             |                                                                    | | v3.1.0                               |
|          |             |                                                                    | | (apps/relion/cpu/3.1.0)              |
|          |             |                                                                    | | (apps/relion/gpu/3.1.0)              |
|          |             |                                                                    |                                        |
|          |             |                                                                    |                                        |
|          +-------------+--------------------------------------------------------------------+----------------------------------------+
|          | **cisTEM**  | | User-friendly software to process cryo-EM images of              | | v1.0.0                               |
|          |             | | macromolecular complexes and obtain high-resolution 3D           | | (apps/cistem/1.0.0)                  |
|          |             | | reconstructions.                                                 |                                        |
|          |             |                                                                    |                                        |
|          |             | - https://cistem.org                                               |                                        |
|          +-------------+--------------------------------------------------------------------+----------------------------------------+
|          | CryoSPARC   | | CryoSPARC is the state-of-the-art platform used globally for     | | v3.0.1                               |
|          |             | | obtaining 3D structural information from single particle cryo-EM |                                        |
|          |             | | data.                                                            |                                        |
|          |             |                                                                    |                                        |
|          |             | - https://cryosparc.com                                            |                                        |
|          +-------------+--------------------------------------------------------------------+----------------------------------------+
|          |             |                                                                    |                                        |
+----------+-------------+--------------------------------------------------------------------+----------------------------------------+


4. EL7 신규 분석 팜 접속
====================

리눅스/맥 사용자
------------

.. code-block:: bash

  $> ssh -Y -o Port=<port> <userID>@tem-ui-el7.sdfarm.kr

-Y (or -X) options : enable trusted X11 (or untrusted X11) forwarding


윈도우즈 사용자
-----------

기존에 사용하시던 MobaXTerm, Putty 등의 SSH 클라이언트 프로그램을 사용하는 것은 같습니다. 다만, 접속 로그인 노드는 tem-ui-el7.sdfarm.kr를 사용하셔야 합니다.


5. 데이터 분석 도구 모듈 경로 및 작업 제출 템플릿
======================================

데이터 분석 도구들의 Module 경로
--------------------------

.. code-block:: bash

  $> module avail
  -------- /tem/el7/Modules/apps --------
  apps/cistem/1.0.0      
  apps/relion/cpu/3.0.7  
  apps/relion/cpu/3.1.0  
  apps/relion/gpu/3.0.7  
  apps/relion/gpu/3.1.0  

  ---- /tem/el7/Modules/acceleration ----
  cuda/9.2  

  -------- /tem/el7/Modules/mpi ---------
  mpi/gcc/openmpi/4.0.3  

  ----- /tem/el7/Modules/virtualenv -----
  conda/2020.11  

  ------- /tem/el7/Modules/tools --------
  tools/ctffind/4.1.14    
  tools/gctf/1.18_b2      
  tools/motioncor2/1.3.1  
  tools/resmap/1.1.4      
  tools/summovie/1.0.2    
  tools/unblur/1.0.2      


데이터 분석 작업 PBS 작업 템플릿 경로
-----------------------------

.. code-block:: bash

  /tem/el7/qsub-cisTEM-cpu-noout.sh             ## output, error 로그 파일을 생성하지 않는 cisTEM 작업 템플릿
  /tem/el7/qsub-cisTEM-cpu.sh                   ## output, error 로그 파일을 생성하는 cisTEM 작업 템플릿
  /tem/el7/qsub-relion-3.0.7-cpu.bash           ## Relion 3.0.7 CPU MPI 작업 템플릿
  /tem/el7/qsub-relion-3.1.0-cpu.bash           ## Relion 3.1.0 CPU MPI 작업 템플릿
  /tem/el7/qsub-relion-3.0.7-gpu.bash           ## Relion 3.0.7 GPU 가속 활용하는 MPI 작업 템플릿
  /tem/el7/qsub-relion-3.1.0-gpu.bash           ## Relion 3.1.0 GPU 가속 활용하는 MPI 작업 템플릿


6. EL7 신규 분석 팜 배치 큐 (Batch Queues) 
======================================

+--------------+-----------------+-----------------------------------------------------------------------+------------------------------------+
| Category     | Queue Name      | Assigned Computing Resources                                          | Remarks                            |
+--------------+-----------------+-----------------------------------------------------------------------+------------------------------------+
| Shared       | **cpuQ**        | - tem-wn[1001-1002]-el7.sdfarm.kr (36 cores and 384GB memory per node)| - 380 Physical CPU cores           |
|              |                 | - tem-wn[1003-1013]-el7.sdfarm.kr (28 cores and 192GB memory per node)|                                    |
|              +-----------------+-----------------------------------------------------------------------+------------------------------------+
|              | **gpuQ**        | - tem-gpu[01-03]-el7.sdfarm.kr (28 cores, 2 P100 GPUs and 384GB mem.) | - 140 Physical CPU cores           | 
|              |                 | - tem-gpu04-el7.sdfarm.kr (28 cores, 2 P40 GPGPUs and 128GB memory)   | - 10 GPGPUs                        |
|              |                 | - tem-gpu05-el7.sdfarm.kr (28 cores, 2 P40 GPGPUs and 256GB memory)   | - P100 has 16GB device memory      |
|              |                 |                                                                       | - P40 has 24GB device memory       |
+--------------+-----------------+-----------------------------------------------------------------------+------------------------------------+


배치 큐 이름 및 상태 확인
-------------------

.. code-block:: bash

  $> qstat -Qf
  Queue: cpuQ
    queue_type = Execution
    total_jobs = 0
    state_count = Transit:0 Queued:0 Held:0 Waiting:0 Running:0 Exiting:0 Complete:0
    resources_default.neednodes = cpuQ
    resources_default.nodes = 1
    acl_group_enable = True
    acl_groups = tem_users
    acl_group_sloppy = True
    mtime = 1610553300
    resources_assigned.nodect = 0
    enabled = True
    started = True

  Queue: gpuQ
    queue_type = Execution
    total_jobs = 0
    state_count = Transit:0 Queued:0 Held:0 Waiting:0 Running:0 Exiting:0 Complete:0
    resources_default.neednodes = gpuQ
    resources_default.nodes = 1
    acl_group_enable = True
    acl_groups = tem_users
    acl_group_sloppy = True
    mtime = 1610553300
    resources_assigned.nodect = 0
    enabled = True
    started = True



전체 계산자원 현황 확인
-----------------

.. code-block:: bash

  $> pbsnodes -a 
  tem-wn1001-el7.sdfarm.kr
    state = free
    power_state = Running
    np = 36
    properties = cpuQ
    ntype = cluster
    status = opsys=linux,uname=Linux tem-wn1001-el7.sdfarm.kr 3.10.0-1160.6.1.el7.x86_64 #1 SMP Tue Nov 10 08:19:23 CST 2020 x86_64,sessions=2125,nsessions=1,nusers=1,idletime=3189604,totmem=400927652kb,availmem=386021536kb,physmem=394636200kb,ncpus=36,loadave=0.02,gres=,netload=368024574355580,state=free,varattr= ,cpuclock=Fixed,macaddr=34:80:0d:46:cc:88,version=6.1.2,rectime=1610587316,jobs=
    mom_service_port = 15002
    mom_manager_port = 15003

  tem-wn1002-el7.sdfarm.kr
    state = free
    power_state = Running
    np = 36
    properties = cpuQ
    ntype = cluster
    status = opsys=linux,uname=Linux tem-wn1002-el7.sdfarm.kr 3.10.0-1160.2.2.el7.x86_64 #1 SMP Mon Oct 19 10:20:12 CDT 2020 x86_64,sessions=1980,nsessions=1,nusers=1,idletime=3189585,totmem=400927812kb,availmem=386052592kb,physmem=394636360kb,ncpus=36,loadave=0.00,gres=,netload=467274352677137,state=free,varattr= ,cpuclock=Fixed,macaddr=f4:e9:d4:67:a5:0c,version=6.1.2,rectime=1610587321,jobs=
    mom_service_port = 15002
    mom_manager_port = 15003

  tem-wn1003-el7.sdfarm.kr
    state = free
    power_state = Running
    np = 28
    properties = cpuQ
    ntype = cluster
    status = opsys=linux,uname=Linux tem-wn1003-el7.sdfarm.kr 3.10.0-1160.11.1.el7.x86_64 #1 SMP Tue Dec 15 08:51:23 CST 2020 x86_64,sessions=16988 30464,nsessions=2,nusers=2,idletime=77442,totmem=204113112kb,availmem=197470212kb,physmem=197821660kb,ncpus=28,loadave=0.00,gres=,netload=7771760205,state=free,varattr= ,cpuclock=Fixed,macaddr=24:6e:96:01:df:d0,version=6.1.2,rectime=1610587306,jobs=
    mom_service_port = 15002
    mom_manager_port = 15003

  tem-wn1004-el7.sdfarm.kr
    state = free
    power_state = Running
    np = 28
    properties = cpuQ
    ntype = cluster
    status = opsys=linux,uname=Linux tem-wn1004-el7.sdfarm.kr 3.10.0-1160.11.1.el7.x86_64 #1 SMP Tue Dec 15 08:51:23 CST 2020 x86_64,sessions=21911,nsessions=1,nusers=1,idletime=84377,totmem=204113112kb,availmem=197460724kb,physmem=197821660kb,ncpus=28,loadave=0.19,gres=,netload=9209594231,state=free,varattr= ,cpuclock=Fixed,macaddr=24:6e:96:01:df:c0,version=6.1.2,rectime=1610587297,jobs=
    mom_service_port = 15002
    mom_manager_port = 15003

  tem-wn1005-el7.sdfarm.kr
    state = free
    power_state = Running
    np = 28
    properties = cpuQ
    ntype = cluster
    status = opsys=linux,uname=Linux tem-wn1005-el7.sdfarm.kr 3.10.0-1160.11.1.el7.x86_64 #1 SMP Tue Dec 15 08:51:23 CST 2020 x86_64,sessions=2032,nsessions=1,nusers=1,idletime=84135,totmem=204113112kb,availmem=197566008kb,physmem=197821660kb,ncpus=28,loadave=0.00,gres=,netload=9652090409,state=free,varattr= ,cpuclock=Fixed,macaddr=24:6e:96:02:de:b0,version=6.1.2,rectime=1610587295,jobs=
    mom_service_port = 15002
    mom_manager_port = 15003

  tem-wn1006-el7.sdfarm.kr
    state = free
    power_state = Running
    np = 28
    properties = cpuQ
    ntype = cluster
    status = opsys=linux,uname=Linux tem-wn1006-el7.sdfarm.kr 3.10.0-1160.11.1.el7.x86_64 #1 SMP Tue Dec 15 08:51:23 CST 2020 x86_64,sessions=22262,nsessions=1,nusers=1,idletime=84367,totmem=204113112kb,availmem=197470252kb,physmem=197821660kb,ncpus=28,loadave=0.00,gres=,netload=9653528113,state=free,varattr= ,cpuclock=Fixed,macaddr=24:6e:96:01:e1:70,version=6.1.2,rectime=1610587303,jobs=
    mom_service_port = 15002
    mom_manager_port = 15003

  tem-wn1007-el7.sdfarm.kr
    state = free
    power_state = Running
    np = 28
    properties = cpuQ
    ntype = cluster
    status = opsys=linux,uname=Linux tem-wn1007-el7.sdfarm.kr 3.10.0-1160.11.1.el7.x86_64 #1 SMP Tue Dec 15 08:51:23 CST 2020 x86_64,sessions=15172,nsessions=1,nusers=1,idletime=84349,totmem=204113112kb,availmem=197490356kb,physmem=197821660kb,ncpus=28,loadave=0.08,gres=,netload=7246363991,state=free,varattr= ,cpuclock=Fixed,macaddr=24:6e:96:02:e3:80,version=6.1.2,rectime=1610587301,jobs=
    mom_service_port = 15002
    mom_manager_port = 15003

  tem-wn1008-el7.sdfarm.kr
    state = free
    power_state = Running
    np = 28
    properties = cpuQ
    ntype = cluster
    status = opsys=linux,uname=Linux tem-wn1008-el7.sdfarm.kr 3.10.0-1160.11.1.el7.x86_64 #1 SMP Tue Dec 15 08:51:23 CST 2020 x86_64,sessions=22147,nsessions=1,nusers=1,idletime=84323,totmem=204113112kb,availmem=197470664kb,physmem=197821660kb,ncpus=28,loadave=0.00,gres=,netload=6170249241,state=free,varattr= ,cpuclock=Fixed,macaddr=24:6e:96:02:df:50,version=6.1.2,rectime=1610587299,jobs=
    mom_service_port = 15002
    mom_manager_port = 15003

  tem-wn1009-el7.sdfarm.kr
     state = job-exclusive
     power_state = Running
     np = 28
     properties = cpuQ
     ntype = cluster
     jobs = 0-13/307.tem-ce-el7.sdfarm.kr,14-27/308.tem-ce-el7.sdfarm.kr
     status = opsys=linux,uname=Linux tem-wn1009-el7.sdfarm.kr 3.10.0-1160.11.1.el7.x86_64 #1 SMP Tue Dec 15 08:51:23 CST 2020 x86_64,sessions=1637 21403 21462,nsessions=3,nusers=2,idletime=124523,totmem=204113112kb,availmem=82190600kb,physmem=197821660kb,ncpus=28,loadave=28.02,gres=,netload=5715573075825,state=free,varattr= ,cpuclock=Fixed,macaddr=ec:f4:bb:e9:cd:28,version=6.1.2,rectime=1611712971,jobs=307.tem-ce-el7.sdfarm.kr 308.tem-ce-el7.sdfarm.kr
     mom_service_port = 15002
     mom_manager_port = 15003

  tem-wn1010-el7.sdfarm.kr
     state = job-exclusive
     power_state = Running
     np = 28
     properties = cpuQ
     ntype = cluster
     jobs = 0-13/307.tem-ce-el7.sdfarm.kr,14-27/308.tem-ce-el7.sdfarm.kr
     status = opsys=linux,uname=Linux tem-wn1010-el7.sdfarm.kr 3.10.0-1160.11.1.el7.x86_64 #1 SMP Tue Dec 15 08:51:23 CST 2020 x86_64,sessions=10683 10742 21656,nsessions=3,nusers=2,idletime=125228,totmem=204113112kb,availmem=82076700kb,physmem=197821660kb,ncpus=28,loadave=28.41,gres=,netload=10000812494662,state=free,varattr= ,cpuclock=Fixed,macaddr=ec:f4:bb:e9:c8:e0,version=6.1.2,rectime=1611712972,jobs=307.tem-ce-el7.sdfarm.kr 308.tem-ce-el7.sdfarm.kr
     mom_service_port = 15002
     mom_manager_port = 15003

  tem-wn1011-el7.sdfarm.kr
     state = job-exclusive
     power_state = Running
     np = 28
     properties = cpuQ
     ntype = cluster
     jobs = 0-13/307.tem-ce-el7.sdfarm.kr,14-27/308.tem-ce-el7.sdfarm.kr
     status = opsys=linux,uname=Linux tem-wn1011-el7.sdfarm.kr 3.10.0-1160.11.1.el7.x86_64 #1 SMP Tue Dec 15 08:51:23 CST 2020 x86_64,sessions=10368 10428 21655,nsessions=3,nusers=2,idletime=128086,totmem=204113112kb,availmem=81587604kb,physmem=197821660kb,ncpus=28,loadave=28.16,gres=,netload=5807235665327,state=free,varattr= ,cpuclock=Fixed,macaddr=ec:f4:bb:e9:bf:28,version=6.1.2,rectime=1611712972,jobs=307.tem-ce-el7.sdfarm.kr 308.tem-ce-el7.sdfarm.kr
     mom_service_port = 15002
     mom_manager_port = 15003

  tem-wn1012-el7.sdfarm.kr
     state = job-exclusive
     power_state = Running
     np = 28
     properties = cpuQ
     ntype = cluster
     jobs = 0-13/307.tem-ce-el7.sdfarm.kr,14-27/308.tem-ce-el7.sdfarm.kr
     status = opsys=linux,uname=Linux tem-wn1012-el7.sdfarm.kr 3.10.0-1160.11.1.el7.x86_64 #1 SMP Tue Dec 15 08:51:23 CST 2020 x86_64,sessions=10379 10475 21655,nsessions=3,nusers=2,idletime=127792,totmem=204113112kb,availmem=84717576kb,physmem=197821660kb,ncpus=28,loadave=28.27,gres=,netload=10075699597211,state=free,varattr= ,cpuclock=Fixed,macaddr=24:6e:96:02:de:d0,version=6.1.2,rectime=1611712971,jobs=307.tem-ce-el7.sdfarm.kr 308.tem-ce-el7.sdfarm.kr
     mom_service_port = 15002
     mom_manager_port = 15003

  tem-gpu01-el7.sdfarm.kr
    state = free
    power_state = Running
    np = 28
    properties = gpuQ
    ntype = cluster
    status = opsys=linux,uname=Linux tem-gpu01-el7.sdfarm.kr 3.10.0-1160.11.1.el7.x86_64 #1 SMP Tue Dec 15 08:51:23 CST 2020 x86_64,sessions=1823 4268,nsessions=2,nusers=2,idletime=36086,totmem=402281596kb,availmem=390304804kb,physmem=395990144kb,ncpus=28,loadave=0.05,gres=,netload=2091843090,state=free,varattr= ,cpuclock=Fixed,macaddr=24:6e:96:77:a0:80,version=6.1.2,rectime=1610587294,jobs=
    mom_service_port = 15002
    mom_manager_port = 15003
    gpus = 2
    gpu_status = gpu[1]=gpu_id=00000000:82:00.0;gpu_pci_device_id=368578782;gpu_pci_location_id=00000000:82:00.0;gpu_product_name=Tesla P100-PCIE-16GB;gpu_memory_total=16280 MB;gpu_memory_used=0 MB;gpu_mode=Default;gpu_state=Unallocated;gpu_utilization=0%;gpu_memory_utilization=0%;gpu_ecc_mode=Enabled;gpu_single_bit_ecc_errors=0;gpu_double_bit_ecc_errors=0;gpu_temperature=28 C,gpu[0]=gpu_id=00000000:03:00.0;gpu_pci_device_id=368578782;gpu_pci_location_id=00000000:03:00.0;gpu_product_name=Tesla P100-PCIE-16GB;gpu_memory_total=16280 MB;gpu_memory_used=0 MB;gpu_mode=Default;gpu_state=Unallocated;gpu_utilization=0%;gpu_memory_utilization=0%;gpu_ecc_mode=Enabled;gpu_single_bit_ecc_errors=0;gpu_double_bit_ecc_errors=0;gpu_temperature=29 C;gpu_display=Enabled,gpu_display=Enabled,driver_ver=460.27.04,timestamp=Thu Jan 14 10:21:33 2021

  tem-gpu02-el7.sdfarm.kr
    state = free
    power_state = Running
    np = 28
    properties = gpuQ
    ntype = cluster
    status = opsys=linux,uname=Linux tem-gpu02-el7.sdfarm.kr 3.10.0-1160.11.1.el7.x86_64 #1 SMP Tue Dec 15 08:51:23 CST 2020 x86_64,sessions=2142,nsessions=1,nusers=1,idletime=35378,totmem=402277340kb,availmem=390086436kb,physmem=395985888kb,ncpus=56,loadave=0.09,gres=,netload=2464164051,state=free,varattr= ,cpuclock=Fixed,macaddr=24:6e:96:77:9b:30,version=6.1.2,rectime=1610587314,jobs=
    mom_service_port = 15002
    mom_manager_port = 15003
    gpus = 2
    gpu_status = gpu[1]=gpu_id=00000000:82:00.0;gpu_pci_device_id=368578782;gpu_pci_location_id=00000000:82:00.0;gpu_product_name=Tesla P100-PCIE-16GB;gpu_memory_total=16280 MB;gpu_memory_used=0 MB;gpu_mode=Default;gpu_state=Unallocated;gpu_utilization=0%;gpu_memory_utilization=0%;gpu_ecc_mode=Enabled;gpu_single_bit_ecc_errors=0;gpu_double_bit_ecc_errors=0;gpu_temperature=27 C,gpu[0]=gpu_id=00000000:03:00.0;gpu_pci_device_id=368578782;gpu_pci_location_id=00000000:03:00.0;gpu_product_name=Tesla P100-PCIE-16GB;gpu_memory_total=16280 MB;gpu_memory_used=0 MB;gpu_mode=Default;gpu_state=Unallocated;gpu_utilization=0%;gpu_memory_utilization=0%;gpu_ecc_mode=Enabled;gpu_single_bit_ecc_errors=0;gpu_double_bit_ecc_errors=0;gpu_temperature=33 C;gpu_display=Enabled,gpu_display=Enabled,driver_ver=460.27.04,timestamp=Thu Jan 14 10:21:52 2021

  tem-gpu03-el7.sdfarm.kr
    state = free
    power_state = Running
    np = 28
    properties = gpuQ
    ntype = cluster
    status = opsys=linux,uname=Linux tem-gpu03-el7.sdfarm.kr 3.10.0-1160.11.1.el7.x86_64 #1 SMP Tue Dec 15 08:51:23 CST 2020 x86_64,sessions=1816,nsessions=1,nusers=1,idletime=34739,totmem=402281596kb,availmem=390290980kb,physmem=395990144kb,ncpus=28,loadave=0.10,gres=,netload=1338950655,state=free,varattr= ,cpuclock=Fixed,macaddr=24:6e:96:77:9b:10,version=6.1.2,rectime=1610587315,jobs=
    mom_service_port = 15002
    mom_manager_port = 15003
    gpus = 2
    gpu_status = gpu[1]=gpu_id=00000000:82:00.0;gpu_pci_device_id=368578782;gpu_pci_location_id=00000000:82:00.0;gpu_product_name=Tesla P100-PCIE-16GB;gpu_memory_total=16280 MB;gpu_memory_used=0 MB;gpu_mode=Default;gpu_state=Unallocated;gpu_utilization=0%;gpu_memory_utilization=0%;gpu_ecc_mode=Enabled;gpu_single_bit_ecc_errors=0;gpu_double_bit_ecc_errors=0;gpu_temperature=29 C,gpu[0]=gpu_id=00000000:03:00.0;gpu_pci_device_id=368578782;gpu_pci_location_id=00000000:03:00.0;gpu_product_name=Tesla P100-PCIE-16GB;gpu_memory_total=16280 MB;gpu_memory_used=0 MB;gpu_mode=Default;gpu_state=Unallocated;gpu_utilization=0%;gpu_memory_utilization=0%;gpu_ecc_mode=Enabled;gpu_single_bit_ecc_errors=0;gpu_double_bit_ecc_errors=0;gpu_temperature=28 C;gpu_display=Enabled,gpu_display=Enabled,driver_ver=460.27.04,timestamp=Thu Jan 14 10:21:53 2021
  
  tem-gpu04-el7.sdfarm.kr
     state = free
     power_state = Running
     np = 28
     properties = gpuQ
     ntype = cluster
     status = opsys=linux,uname=Linux tem-gpu04-el7.sdfarm.kr 3.10.0-1160.11.1.el7.x86_64 #1 SMP Tue Dec 15 08:51:23 CST 2020 x86_64,sessions=2041,nsessions=1,nusers=1,idletime=63469,totmem=137732192kb,availmem=132548340kb,physmem=131440740kb,ncpus=48,loadave=0.10,gres=,netload=790032261080,state=free,varattr= ,cpuclock=Fixed,macaddr=e4:43:4b:07:8c:f0,version=6.1.2,rectime=1611712958,jobs=
     mom_service_port = 15002
     mom_manager_port = 15003
     gpus = 2
     gpu_status = gpu[1]=gpu_id=00000000:AF:00.0;gpu_pci_device_id=456659166;gpu_pci_location_id=00000000:AF:00.0;gpu_product_name=Tesla P40;gpu_memory_total=22919 MB;gpu_memory_used=0 MB;gpu_mode=Default;gpu_state=Unallocated;gpu_utilization=0%;gpu_memory_utilization=0%;gpu_ecc_mode=Enabled;gpu_single_bit_ecc_errors=0;gpu_double_bit_ecc_errors=0;gpu_temperature=28 C,gpu[0]=gpu_id=00000000:3B:00.0;gpu_pci_device_id=456659166;gpu_pci_location_id=00000000:3B:00.0;gpu_product_name=Tesla P40;gpu_memory_total=22919 MB;gpu_memory_used=0 MB;gpu_mode=Default;gpu_state=Unallocated;gpu_utilization=0%;gpu_memory_utilization=0%;gpu_ecc_mode=Enabled;gpu_single_bit_ecc_errors=0;gpu_double_bit_ecc_errors=0;gpu_temperature=25 C;gpu_display=Enabled,gpu_display=Enabled,driver_ver=460.32.03,timestamp=Wed Jan 27 11:02:37 2021

  tem-gpu05-el7.sdfarm.kr
     state = free
     power_state = Running
     np = 28
     properties = gpuQ
     ntype = cluster
     status = opsys=linux,uname=Linux tem-gpu05-el7.sdfarm.kr 3.10.0-1160.11.1.el7.x86_64 #1 SMP Tue Dec 15 08:51:23 CST 2020 x86_64,sessions=2352,nsessions=1,nusers=1,idletime=63492,totmem=269906392kb,availmem=261305348kb,physmem=263614940kb,ncpus=72,loadave=0.13,gres=,netload=808539072,state=free,varattr= ,cpuclock=Fixed,macaddr=e4:43:4b:03:78:38,version=6.1.2,rectime=1611712989,jobs=
     mom_service_port = 15002
     mom_manager_port = 15003
     gpus = 2
     gpu_status = gpu[1]=gpu_id=00000000:AF:00.0;gpu_pci_device_id=456659166;gpu_pci_location_id=00000000:AF:00.0;gpu_product_name=Tesla P40;gpu_memory_total=22919 MB;gpu_memory_used=0 MB;gpu_mode=Default;gpu_state=Unallocated;gpu_utilization=0%;gpu_memory_utilization=0%;gpu_ecc_mode=Enabled;gpu_single_bit_ecc_errors=0;gpu_double_bit_ecc_errors=0;gpu_temperature=30 C,gpu[0]=gpu_id=00000000:3B:00.0;gpu_pci_device_id=456659166;gpu_pci_location_id=00000000:3B:00.0;gpu_product_name=Tesla P40;gpu_memory_total=22919 MB;gpu_memory_used=0 MB;gpu_mode=Default;gpu_state=Unallocated;gpu_utilization=0%;gpu_memory_utilization=0%;gpu_ecc_mode=Enabled;gpu_single_bit_ecc_errors=0;gpu_double_bit_ecc_errors=0;gpu_temperature=27 C;gpu_display=Enabled,gpu_display=Enabled,driver_ver=460.32.03,timestamp=Wed Jan 27 11:03:08 2021


7. 계산자원 활용 현황 및 모니터링 (CPU/GPU 노드) - fstat.bin
====================================================

.. code-block:: bash

  $> which fstat.bin
  /usr/bin/fstat.bin

  $> fstat.bin
  ------------------------------------------------------------------------------------------------------------------------
  NODE                          QUEUE   STATUS(F/S/E)    [GPU] T/U/F    [CPU] T/U/F  USAGE RATIO
  ------------------------------------------------------------------------------------------------------------------------
  tem-gpu01-el7.sdfarm.kr        gpuQ          Shared     2/1/1 [#.]        28/2/26  [##..........................]          
  tem-gpu02-el7.sdfarm.kr        gpuQ          Shared     2/2/0 [##]        28/4/24  [####........................]          
  tem-gpu03-el7.sdfarm.kr        gpuQ            Free     2/0/2 [..]        28/0/28  [............................]          
  tem-gpu04-el7.sdfarm.kr        gpuQ            Free     2/0/2 [..]        28/0/28  [............................]          
  tem-gpu05-el7.sdfarm.kr        gpuQ            Free     2/0/2 [..]        28/0/28  [............................]          
  tem-wn1001-el7.sdfarm.kr       cpuQ          Shared            n/a        36/28/8  [############################........]  
  tem-wn1002-el7.sdfarm.kr       cpuQ          Shared            n/a        36/28/8  [############################........]  
  tem-wn1003-el7.sdfarm.kr       cpuQ       Exclusive            n/a        28/28/0  [############################]          
  tem-wn1004-el7.sdfarm.kr       cpuQ       Exclusive            n/a        28/28/0  [############################]          
  tem-wn1005-el7.sdfarm.kr       cpuQ       Exclusive            n/a        28/28/0  [############################]          
  tem-wn1006-el7.sdfarm.kr       cpuQ       Exclusive            n/a        28/28/0  [############################]          
  tem-wn1007-el7.sdfarm.kr       cpuQ       Exclusive            n/a        28/28/0  [############################]          
  tem-wn1008-el7.sdfarm.kr       cpuQ       Exclusive            n/a        28/28/0  [############################]          
  tem-wn1009-el7.sdfarm.kr       cpuQ       Exclusive            n/a        28/28/0  [############################]          
  tem-wn1010-el7.sdfarm.kr       cpuQ       Exclusive            n/a        28/28/0  [############################]          
  tem-wn1011-el7.sdfarm.kr       cpuQ       Exclusive            n/a        28/28/0  [############################]          
  tem-wn1012-el7.sdfarm.kr       cpuQ       Exclusive            n/a        28/28/0  [############################]          
  ------------------------------------------------------------------------------------------------------------------------
          7 running jobs
          1 queued(waiting) jobs
          Total 492 cores / Used 342 cores (utilization 69.51 percent)
  ------------------------------------------------------------------------------------------------------------------------

  * NODE  : CPU 또는 GPU 장치를 가진 계산서버 이름 
  * QUEUE : 각 서버가 속한 큐 이름
  * STATUS(F/S/E)
    - F (Free) : 계산서버에 어떤 데이터 분석 작업도 할당되어 있지 않음
    - S (Shared) : 계산서버에 CPU 또는 GPU 작업이 할당되어 실행중이나, 해당 서버의 모든 자원을 할당받은 상태는 아님
    - E (Exclusive) : 계산서버에 작업들이 할당되어 실행중이고, 작업들이 모든 자원을 할당받아 busy 한 상태
  * [GPU] T/U/F : GPU 계산서버에 설치된 GPU 카드 총 개수, 사용중인 개수(#), 유휴 카드 개수(.)
  * [CPU] T/U/F : CPU 계산서버의 총 코어 개수, 사용중인 개수(#), 유휴 코어 개수(.)

8. 분석용 스토리지 쿼터 정보 확인 - dynmotd
====================================

.. code-block:: bash
  
  $tem-ui-el7> which dynmotd
  /usr/local/bin/dynmotd

  $tem-ui-el7> dynmotd
    ____ ____  ____   ____   _____ _____ __  __   _____
  / ___/ ___||  _ \ / ___| |_   _| ____|  \/  | |  ___|_ _ _ __ _ __ ___
  | |  _\___ \| | | | |       | | |  _| | |\/| | | |_ / _` | '__| '_ ` _ \
  | |_| |___) | |_| | |___    | | | |___| |  | | |  _| (_| | |  | | | | | |
  \____|____/|____/ \____|   |_| |_____|_|  |_| |_|  \__,_|_|  |_| |_| |_|

  * Official GSDC TEM users guide : https://tem-docs.readthedocs.io
  ==========================================================================
  * Hostname..............: tem-ui-el7.sdfarm.kr
  * OS Release............: Scientific Linux release 7.9 (Nitrogen)
  * System uptime.........: 137 days 1 hours 30 minutes 39 seconds
  * Users.................: Currently 6 user(s) logged on
  * Processes.............: 831 running
  * CPU usage.............: 0.00, 0.06, 0.07 (1, 5, 15 min)
  * Memory (used/total)...: 12800 MB / 385381 MB
  * Swap in use...........: 48 MB
  --------------------------------------------------------------------------
  * TEM disk (used/total).: 715 TB / 800 TB (90%)
  * Current user..........: tem
  * Home directory........: /tem/home/tem
  * Disk Quota limit......: 20480 GB
  * Disk usage............: 945 GB (4.6153 %)
  * # of Files............: 1719528
  ==========================================================================

