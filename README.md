# 리눅스 top, ps, jobs, kill 명령어

## top 명령어

시스템의 상태를 실시간으로 모니터링할 수 있는 명령어이다.
CPU 및 메모리 사용량, 시스템 업타임 등 전반적인 시스템 상태와 함께 자원을 많이 사용하는 프로세스 목록을 실시간으로 보여준다.

<img width="363" height="209" alt="top command" src="https://github.com/user-attachments/assets/f9b97209-ab95-4e21-ae5d-bd0a0bfbda0c" />

<출처: https://code-lab1.tistory.com/332 >


### 사용 예시

```bash
top
top -u user1
top -d 5
```


## 화면 상단 정보
### 1. 시스템 상태 
* 현재 시간
* 시스템 가동 시간
* 로그인한 사용자 수
* 시스템 평균 부하(Load Average)


### 2. 작업 정보
* 전체 프로세스 수
* 실행 중(Running)
* 대기 중(Sleeping)
* 중지됨(Stopped)
* 좀비 프로세스(Zombie)


### 3. CPU 사용률
* us : 사용자 프로세스 사용률
* sy : 시스템(커널) 사용률
* ni : 우선순위가 변경된 프로세스 사용률
* id : 유휴 상태 비율
* wa : I/O 대기 시간


### 4. 메모리 정보
* total : 전체 메모리
* free : 사용 가능한 메모리
* used : 사용 중인 메모리
* buff/cache : 버퍼 및 캐시 메모리


### 주요 열

| 항목 | 의미 |
|:---|:---|
|PID|프로세스 ID|
|USER|사용자 이름|
|PR|우선순위|
|NI|Nice 값|
|VIRT|가상 메모리 사용량|
|RES|실제 메모리 사용량|
|SHR|공유 메모리 사용량|
|S|프로세스 상태|
|%CPU|CPU 사용률|
|%MEM|메모리 사용률|
|TIME+|CPU 사용 시간|
|COMMAND|실행된 명령어|



### 주요 옵션:

**top -u 사용자명**

특정 사용자의 프로세스만 표시한다.

**top -p PID**

특정 프로세스만 모니터링한다.

**top -d 초**

화면 갱신 주기를 설정한다.

**top -n 횟수**

지정한 횟수만큼 화면을 갱신한 후 종료한다.




### 주요 인터랙티브 키:
* q - top 종료
* m - 메모리 사용량 순으로 프로세스 정렬
* p - CPU 사용량 순으로 프로세스 정렬
* k - 프로세스 종료
* N - PID 순으로 정렬
* T - 실행 시간 기준으로 정렬
* R - 오름차순과 내림차순 전환





## ps 명령어 
(ps - Process Status)

현재 실행 중인 프로세스의 상태 정보를 확인할 때 사용하는 명령어이다. 프로세스 ID, CPU 및 메모리 사용량, 실행 상태 등을 확인할 수 있다. 


<img width="713" height="95" alt="ps" src="https://github.com/user-attachments/assets/120e0a6f-38fb-4eba-a955-0adbc1616993" />


### 사용 예시

```bash
ps
ps -ef
ps aux
ps -ef | grep ssh
```

### 출력 정보
* PID : 프로세스 ID
* TTY : 터미널 종류
* TIME : CPU 사용 시간
* CMD : 실행된 명령어



### 주요 옵션:

**ps -A**

시스템의 모든 프로세스를 표시한다.

**ps -f**

프로세스의 상세 정보를 표시한다.


추가 정보: UID, PPID, STIME

**ps -ef**

모든 프로세스를 상세 정보와 함께 출력한다.


grep 명령어와 함께 사용하여 특정 프로세스를 검색할 수 있다.
  
**ps -u 사용자**

특정 사용자가 실행 중인 프로세스를 확인한다.

**ps aux**
   
BSD 형식으로 모든 프로세스를 출력한다.



### 프로세스 상태

|상태|의미|
|:---|:---|
|R|실행 중(Running)|
|S|대기 상태(Sleeping)|
|D|인터럽트 불가능한 대기|
|T|중지됨(Stopped)|
|Z|종료되었으나 제거되지 않은 좀비 프로세스|





## jobs 명령어

현재 셸(shell)에서 실행 중이거나 일시 중지된 작업의 상태를 확인할 때 사용하는 명령어이다. 백그라운드 작업을 관리하는 데 사용된다.


<img width="286" height="187" alt="jobs" src="https://github.com/user-attachments/assets/7dd6a002-525a-43e6-b57f-612e796726b4" />


<출처: https://www.geeksforgeeks.org/linux-unix/bg-command-in-linux-with-examples/ >


### 사용 예시

```bash
jobs
jobs -l
jobs -r
```


### 출력 정보
* 작업 번호(Job ID)
* 상태(Running, Stopped 등)
* 실행 명령어




### 주요 옵션:

**jobs -l**

작업 번호와 함께 프로세스 ID(PID)를 표시한다.

**jobs -r**

실행 중(Running)인 작업만 표시한다.

**jobs -s**

중지된(Stopped) 작업만 표시한다.




## kill 명령어

프로세스에 신호를 보내어 종료하거나 제어할 때 사용하는 명령어이다. 기본적으로 SIGTERM(15) 신호를 보내 프로세스의 정상 종료를 요청한다.

<img width="556" height="214" alt="kill" src="https://github.com/user-attachments/assets/a0049928-4013-4964-987a-1173d01e0753" />

<출처: https://media.geeksforgeeks.org/wp-content/uploads/20230508114424/74-(1).webp >

### 사용 예시

```bash
kill 1234
kill -9 1234
kill -l
```


### 주요 옵션:

**kill -9 PID**

강제로 프로세스를 종료한다.

**kill -15 PID**

정상 종료를 요청한다.

**kill -l**

사용 가능한 신호(signal) 목록을 출력한다.




### 자주 사용하는 신호

|신호|번호|의미|
|:---|:---|:---|
|SIGTERM|15|정상 종료 요청|
|SIGKILL|9|강제 종료|
|SIGSTOP|19|프로세스 일시 중지|
|SIGCONT|18|중지된 프로세스 재개|





