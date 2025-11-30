# 리눅스 명령어
## top
CPU 사용량, 메모리 사용량, 실행 중인 프로세스 목록 등을 주기적으로 업데이트하여 보여주는 실시간 프로세스 모니터링 도구

![top명령어_edit](https://github.com/user-attachments/assets/847df02e-02e1-4bfd-bda7-b12f3cae1eca)

- top - 05:51:18 up 1:29, 0 users, load average: 0.00, 0.00, 0.07
  - **05:51:18** : 현재 시간
  - **up 1:29** : 시스템(컨테이너)이 부팅된 후 경과 시간
  - **0 users** : 현재 로그인한 사용자 수
  - **load average : 0.00, 0.00, 0.07** : 최근 1분, 5분, 15분 평균 부하량 (load average)

- Tasks: 2 totals, 1 running, 1 sleeping, 0 stopped, 0 zombie
  - **totals** : 전체 프로세스 개수
  - **running** : CPU에서 실행 중인 프로세스
  - **sleeping** : I/O 기다리며 잠들어 있는 프로세스
  - **stopped** : Ctrl+Z 같은 신호로 멈춘 상태
  - **zombie** : 종료되었지만 종료 처리가 안 된 프로세스

- %Cpu(s): 0.3 us, 0.5 sy, 0.0 ni, 98.9 id, 0.1 wa, 0.0 hi, 0.2 si, 0.0 st ***(CPU 사용량)***
  - **us (user)** : 사용자 영역 프로그램 CPU 사용
  - **sy (system)** : 커널/시스템 CPU 사용
  - **ni (nice)** : nice 값 변경된 프로세스의 CPU 사용
  - **id (idle)** : CPU가 아무 일도 안 하며 쉬는 시간
  - **wa (iowait)** : I/O 대기 시간
  - **hi** : 하드웨어 인터럽트 처리
  - **si** : 소프트웨어 인터럽트 처리
  - **st (steal)** : 다른 VM에 빼앗긴 CPU 시간
 
- MiB Mem : 15744.2 total,  14773.5 free,  597.7 used,  373.0 buff/cache
  - **total** : 총 물리 메모리
  - **free** : 현재 완전히 비어 있는 메모리
  - **used** : 프로그램들이 직접 사용하는 메모리
  - **buff/cache** : 캐싱/버퍼에 사용되는 메모리

- MiB Swap: 4096.0 total,  4096.0 free,  0.0 used,    14945.6 avail Mem
  - **total** : 총 Swap 공간
  - **free** : 아직 사용되지 않은 Swap 공간
  - **used** : 사용 중인 Swap 공간
  - **avail Mem** : 프로그램이 실제로 사용 가능한 메모리

- 프로세스 리스트

|컬럼|의미|
|-----|-----|
|PID|프로세스 ID|
|USER|프로세스를 실행한 사용자|
|PR|프로세스 우선순위|
|NI|nice 값(프로세스 우선순위 조절 값)|
|VIRT|가상 메모리 사용량|
|RES|실제 메모리 사용량|
|SHR|공유 메모리 사용량|
|S|상태(State)|
|%CPU|CPU 사용률|
|%MEM|메모리 사용률|
|TIME+|CPU 사용 시간|
|COMMAND|실행 명령어|

## ps
Process Status의 약자로, 프로세스 정보(PID, 실행 사용자, CPU/메모리 사용량, 실행 경로 등)를 출력하는 명령어

![ps명령어__edit](https://github.com/user-attachments/assets/0b262c47-438f-4e8b-8255-a403e31a6271)

|컬럼|의미|
|-----|-----|
|PID|프로세스 ID|
|TTY|프로세스를 실행한 터미널|
|TIME|사용한 CPU 시간|
|CMD|실행된 명령어|

## jobs
현재 쉘에서 실행 중인 작업(job) 목록을 확인하는 명령어

![jobs명령어__edit](https://github.com/user-attachments/assets/728d8c08-78af-4077-909d-44ee812c9ff4)


- 작업 목록

|작업|의미|
|-----|-----|
|Running|실행 중|
|Stopped|정지 상태|
|Done|정상 종료|
|Killed|시그널에 의해 강제로 종료된 상태|
|Terminated|시그널로 종료됨|

## kill
프로세스 ID(PID) 또는 작업 번호(Job ID)를 지정해 해당 프로세스에 시그널(Signal)을 보내는 명령어

- 대표적으로 사용하는 시그널

|번호|시그널|의미|
|-----|-----|-----|
|15|SIGTERM|정상 종료(기본값)|
|9|SIGKILL|강제 종료|
|2|SIGINT|인터럽트(Ctrl+C와 동일)|
|18|SIGCONT|정지된 작업 계속 실행|
|19|SIGSTOP|작업 정지(Ctrl+Z와 유사)|

- kill 명령어 예제
  
    kill 명령어 실행을 위해 다음 명령어를 입력

    $ sleep 100 &
  
    $ sleep 200 &
  
    $ sleep 300 &
  
    $ sleep 400 &
  
    $ sleep 500 &

    ---

    sleep : 지정한 시간(초) 동안 아무 동작도 하지 않고 기다림
  
    100 : sleep할 시간(초)
  
    & : 백그라운드 실행

    ---
  

  - kill -15 PID
 
    ![kill_SIGTERM](https://github.com/user-attachments/assets/02bd097f-2b58-44d8-aaa7-5924fd4d3c99)

  - kill -9 PID
 
    ![kill_SIGKILL](https://github.com/user-attachments/assets/333e3e12-ddcf-4e41-ace0-99399516736f)

  - kill -2 PID
 
    ![kill_SIGINT](https://github.com/user-attachments/assets/0a02eb19-373a-4fd3-8150-966a7c4d45cb)

  - kill -19 PID
    
    ![kill_SIGSTOP](https://github.com/user-attachments/assets/3cab9a73-dc3b-45a7-8ec5-c03247a246c3)

  - kill -18 PID
    
    ![kill_SIGCONT](https://github.com/user-attachments/assets/31516395-c5da-481e-b44d-a0a710f0e0f3)

