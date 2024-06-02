# top, ps, jobs, kill 명령어
_20243133 지창현 과제2_
---


# TOP

top 명령어를 통해 실행되고 있는 프로세스, 메모리 사용량, 서비스 실행 시간 등 시스템에 대한 다양한 정보를 확인할 수 있습니다.

아무 옵션을 주지 않은 top을 입력하면 상단과 하단의 두 개의 영역으로 구분되어 내용이 표시됩니다. 상단에는 시스템에 대한 전반적인 요약 정보가, 하단에는 프로세스별 구체적인 정보가 표기됩니다. 정보는 3초마다 업데이트됩니다.

### TOP - 상단 정보
---
![TOP 명령어](https://github.com/JChangH/OSS_2/assets/171461998/2269bc3a-2ec8-450e-b12b-bc98c2cd665b)

상단의 첫번째 줄(top -)은 왼쪽부터 순서대로 현재 시간, 컴퓨터가 연속으로 실행되고 있는 시간, 로그인 한 사용자 수, 로드 에버리지(load average)를 보여줍니다. 로드 에버리지는 숫자가 3개인데, 차례로 1분, 5분, 15분 간의 로드의 평균을 나타냅니다. 로드란 리소스 사용량을 비율로 표시한 지표를 의미하는데요. 싱글 코어일 때 1.0이면 100%를 모두 사용하고 있다는 의미입니다. 2코어에 1.0이면 50%를 사용하고 있다는 것입니다.

두번째 줄(task)은 프로세스의 상태를 표시합니다. 순서대로 총 프로세스 수, 실행되고 있는 프로세스 수, 대기 중인 프로세스 수, 멈춘 프로세스 수, 좀비 상태인 프로세스 수를 의미합니다.

세번째 줄(Cpu)은 CPU 사용 정보를 나타냅니다. 아래 정보에 따라 각각 비율이 표기됩니다.

- us : 사용자 영역 프로세스에서의 CPU 사용률입니다.
- sy : 커널 영역 프로세스에서의 CPU 사용률입니다.
- ni : 우선순위로 할당된 사용자 영역 프로세스를 실행하는데 소요되는 CPU 사용률입니다.
- id : CPU를 사용하고 있지 않은 비율입니다.
- wa : I/O가 완료될 때까지 기다리는 CPU 사용률입니다.
- hi : 하드웨어 인터럽트에 사용되는 CPU 사용률
- si : 소프트웨어 인터럽트에 사용되는 CPU 사용률
- st : CPU를 가상 머신에서 사용함으로써 생기는 손실된 CPU의 비율

네번째 줄(Mem)은 물리 메모리 사용 정보를 나타냅니다. 그 뒤로는 순서대로 총 메모리(total), 여유 메모리(free), 사용 중인 메모리(used), 버퍼 또는 캐시 메모리(buff/cache)를 의미합니다.

다섯번째 줄(Swap)은 스왑 메모리 정보를 나타냅니다. 표기 방식은 물리 메모리와 동일합니다. 스왑 메모리는 가상 메모리로 불리며, 메모리가 부족할 때 디스크 공간을 이용해서 부족한 메모리 공간을 대체할 수 있는 메모리입니다. 때문에 물리 메모리가 가득 차도 스왑 메모리에 여유가 있으면 프로세스를 구동할 수 있습니다.

Mem과 Swap 앞에 KiB, MiB, GiB 등이 붙어있는데, 이는 표기되는 데이터의 단위를 나타냅니다.

### TOP - 하단 정보
---
하단에는 프로세스 목록과 각 프로세스별 정보가 표기됩니다.

- PID : 프로세스 ID입니다.
- USER : 프로세스의 소유 계정입니다.
- PR : 프로세스 우선순위입니다.
- NI : PR에 영향을 주는 나이스 값입니다.
- VIRT : 프로세스가 사용하고 있는 가상 메모리의 총량입니다.
- RES : 프로세스가 사용하고 있는 물리 메모리의 양입니다.
- SHR : 다른 프로세스와의 공유 메모리입니다.
- S : 프로세스의 상태를 의미합니다. D는 네트워크 I/O를 대기하고 있는 상태, R은 실행 중인 상태, S는 대기 상태, Z는 좀비 상태입니다. 좀비 상태란 부모 프로세스가 죽은 자식 프로세스를 의미합니다.
- %CPU : 프로세스의 CPU 사용률입니다.
- %MEM : 프로세스의 물리 메모리 사용률입니다.
- TIME+ : 100초 안에 사용하는 CPU 사용량입니다.
- COMMAND : 명령줄입니다.

하단 정보는 키보드 방향키 위, 아래 키와 페이지 업, 다운 키로 목록을 이동할 수 있습니다.

### TOP - 메모리 단위 변경
---
- E를 누르면 상단에 표기되는 데이터 단위가 변경됩니다.

- e를 누르면 하단에 표기되는 데이터 단위가 변경됩니다.

### TOP - 원하는 정보 순으로 정렬하기
---
컬럼별 사용량 순으로 순차 정렬을 위해선 top으로 정보가 표기되고 있는 상태에서 아래의 단축키를 입력하면 됩니다.

- P : %CPU순으로 정렬
- M : %MEM순으로 정렬
- N : PID순으로 정렬
- T : TIME+순으로 정렬

[출처](https://change-words.tistory.com/entry/%EB%A6%AC%EB%88%85%EC%8A%A4-top)

# PS

실행 중인 프로세스를 확인할 때 ps 명령어를 사용할 수 있습니다. 

ps -ef 형태로 자주 사용되며 grep 명령어를 파이프라인으로 연결해 특정 프로세스에 대한 추가 정보를 확인하는 방식으로도 활용할 수 있습니다.

### ps
---
ps는 현재 실행되고 있는 프로세스를 보여주는 명령어입니다. 옵션 없이 ps를 실행하면 아주 간단한 정보를 출력합니다.
```bash
[root@localhost ~]# ps
   PID TTY          TIME CMD
  3161 pts/1    00:00:00 bash
  3409 pts/1    00:00:05 java
  3425 pts/1    00:00:35 java
  4020 pts/1    00:00:00 su
  4069 pts/1    00:00:00 su
  4073 pts/1    00:00:00 bash
  4211 pts/1    00:00:00 ps
```
### ps -ef
---
ps -ef 명령어는 시스템의 모든 프로세스를 출력합니다.

- -e : 모든 프로세스를 출력합니다. 사용자가 실행한 프로세스를 포함해서 부팅하며 자동으로 실행되는 systemd 같은 프로세스도 모두 출력합니다.
- -f : 모든 포맷을 출력합니다. 더 자세한 출력 결과를 보여줍니다.
ps 명령어는 grep과 함께 쓰는 경우도 많습니다. 예를 들어, 실행 중인 postgresql 프로세스를 찾아보겠습니다.
```bash
[root@localhost bin]# ps -e | grep "post*"
  1154 ?        00:00:00 postmaster
  1218 ?        00:00:00 postmaster
  1231 ?        00:00:00 postmaster
  1232 ?        00:00:00 postmaster
  1233 ?        00:00:00 postmaster
  1234 ?        00:00:00 postmaster
  1235 ?        00:00:00 postmaster
  1242 ?        00:00:00 postmaster
```
출력된 결과로 알게된 PID로 netstat을 통해 소켓 리스닝 상태를 확인하는 식으로 추가 정보를 확인할 수 있습니다.

```bash
[root@localhost bin]# netstat -ntlp | grep "1154"
tcp        0      0 0.0.0.0:5432            0.0.0.0:*               LISTEN      1154/postmaster
tcp6       0      0 :::5432                 :::*                    LISTEN      1154/postmaster
```

### ps -aux
---
ps -aux 명령어는 ps -ef 명령어와 출력 결과가 비슷합니다. 단 ps -aux는 프로세스의 CPU와 메모리 사용량을 출력한다는 차이가 있습니다.

- a : 시스템의 모든 사용자가 실행 중인 프로세스를 출력합니다.
- u : 메모리, CPU 사용률, 프로세스 상태코드, 프로세스 소유자 등의 정보를 출력합니다.
- x : 시스템이 부팅될 때 백그라운드에서 실행되는 시스템 관련 프로세스도 출력합니다. 예를 들어 PID 1번인 systemd도 출력됩니다.
![ps -aux](https://github.com/JChangH/OSS_2/assets/171461998/fad407f6-8193-4d43-9e90-5904a3ad897b)

[출처](https://change-words.tistory.com/entry/linux-ps)

# jobs

현재 세션의 작업 상태를 출력합니다.

### jobs 사용법
---
```bash
jobs [옵션][jobID]
jobs -x command [args]
```
- -l : 프로세스 그룹 ID를 state 필드 앞에 출력합니다.
- -n : 프로세스 그룹 중에 대표 프로세스 ID를 출력합니다.
- -p : 각 프로세스 ID에 대해 한 행씩 출력합니다.
- command : 지정한 명령어를 실행합니다.

### jobs 설명 및 예
---
jobs는 작업이 중지된 상태, 백그라운드로 진행 중인 작업 상태, 변경되었지만 보고되지 않은 상태 등을 표시합니다.

현재 환경의 작업 상태를 아래와 같이 확인할 수 있습니다.
```bash
$ jobs
[1]- 정지됨                          vi
[2]- 정지됨                          tail -f /var/log/messages
```
-l 옵션은 state 필드 앞에 프로세스 ID를 출력합니다.
```bash
$ jobs -l
[1]- 4908 Stopped (tty out put)      vi
[2]- 4987 Stopped                    tail -f /var/log/messages
```
- jobs 명령어로 확인할 수 있는 세션의 상태값은 다음과 같습니다.
- Running - 작업이 일시 중단되지 않았고 종료하지 않고 계속 진행 중임을 뜻합니다.
- Done - 작업이 완료되어 0을 반환하고 종료했음을 뜻합니다.
- Done (code) - 작업이 정상적으로 완료했으며, 0이 아닌 코드를 반환했음을 뜻합니다.
- Stopped - 작업이 일시 중단됨을 뜻합니다.
- Stopped (SIGTSTP) - SIGTSTP 신호가 작업을 일시 중단했음을 뜻합니다.
- Stopped (SIGSTOP) - SIGSTOP 신호가 일시 중단했음을 뜻합니다.
- Stopped (SIGTTIN) - SIGTTIN 신호가 작업을 일시 중단했음을 뜻합니다.
- Stopped (SIGTTOU) - SIGTTOU 신호가 작업을 일시 중단했음을 뜻합니다.

다음과 같이 하면 v로 시작하는 모든 프로세스 ID를 확인할 수 있습니다.
```bash
$ jobs -p %v
4908
```
[출처](https://terms.naver.com/entry.naver?docId=4125682&cid=59321&categoryId=59321 "유닉스 리눅스 명령어 사전, 2010. 11. 30., 우종경, 박종오")

# kill

리눅스 kill 명령어는 프로세스를 종료할 때 사용됩니다. 이때 터미널은 프로세스에 시그널을 보냅니다. 프로세스가 받는 시그널에 따라 프로세스의 종료 행위에 차이가 있습니다.

### 리눅스 kill
---
```bash
kill [signal] [process ID(s)]
```
kill을 통해 프로세스에 보낼 시그널 넘버와 종료할 PID를 입력합니다. 예를 들어, 1234라는 PID를 가진 프로세스를 종료할 때 아래와 같이 사용할 수 있습니다.
```bash
kill 1234
```
그런데 kill은 -9 옵션과 함께 사용하는 경우가 더 많습니다.
```bash
kill -9 1234
```
### 시그널이란?
---
kill 뒤에 붙이는 숫자 옵션을 이해하기 위해서는 시그널(signal) 개념을 알아야 합니다. 리눅스에서 시그널이란 프로세스에 전달되는 일종의 명령 신호입니다. 고유한 이름과 숫자가 있으며 특정 신호를 받은 프로세스는 신호에 맞는 기능이 수행됩니다.

예를 들어, 리눅스에서 정말 자주 사용되는 CTRL + C 명령 역시 프로세스에 시그널을 보내는 행위입니다. 이때 터미널은 SIGINT라는 2번 시그널을 포그라운드 프로세스로 보내는데, 이 시그널을 받은 프로세스는 종료됩니다. 그래서 포그라운드 프로세스가 오래 동안 끝나지 않고 프롬프트를 작성할 수가 없는 상태일 때 CTRL + C로 종료할 수 있습니다.

### 시그널 옵션 숫자
---
시그널 목록은 kill과 l 옵션을 조합해서 확인할 수 있습니다. 물론 모든 시그널의 의미를 알고 있어야하는 건 아닙니다. 자주 사용하는 시그널이 있다면 그게 뭘 의미하는 것인지 정도만 이해하고 있으면 충분합니다.
```bash
kill -l
```
![시그널 옵션 숫자](https://github.com/JChangH/OSS_2/assets/171461998/33f45797-8eb6-4a18-b6d7-c3ea4c6216e0)

### kill -9 옵션이 가장 많이 사용되는 이유
---
프로세스 종료에 사용되는 시그널은 15, 19, 9 등이 있습니다.

- SIGTERM(15) : 프로세스를 정상적으로 종료합니다. 종료 전 필요한 정리 작업을 수행합니다.
- SIGSTOP(19) : 프로세스를 중지합니다.
- SIGKILL(9) : 프로세스를 강제 종료합니다. 프로세스가 이 신호를 받으면 정리 작업 없이 즉시 종료됩니다.

가장 많이 사용되는 옵션은 -9입니다. 사실 시그널 개념을 모르고 쓰는 경우도 흔하기 때문에 그냥 "프로세스 종료 명령은 kill -9"라고 이해하고 쓰는 분들도 많을 겁니다.

kill -9가 가장 많이 쓰이는 이유는 상황에 관계없이 즉각 종료가 보장된다는 점 때문인 거 같습니다. SIGTERM(15)이나 SIGSTOP(9) 같은 다른 시그널의 경우 정리 작업을 수행하기 때문에 프로세스가 신호를 무시하거나 차단하거나 무한 루프에 빠질 수도 있습니다.

그리고 kill 명령어를 사용하는 것 자체가 프로세스를 강제종료 해야하는 순간일 확률이 높습니다. 예를 들어, 일반적으로 서비스는 startup.sh, stop.sh 같은 실행 스크립트를 만들어서 시작, 종료하는데 이런 스크립트가 먹히지 않을 때 강제 종료를 위해 kill을 사용하기 때문입니다.

[출처](https://change-words.tistory.com/entry/linux-kill-9)
