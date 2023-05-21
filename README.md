

# top, ps, jobs, kill에 대한 이해





``` bash
1. top
2. ps
3. jobs
4. kill
```
***

# 1. top
### top 명령어는 table of processes 의 약자로 CPU 와 메모리 이용에 관한 정보를 표시하는 일을 수행합니다.
``` bash
(base) /home/chosun/20203154/gitdir/readme.md ~ % top
Processes: 448 total, 2 running, 446 sleeping, 2159 threads            23:44:33
Load Avg: 1.26, 1.56, 1.62  CPU usage: 4.28% user, 3.56% sys, 92.15% idle
SharedLibs: 397M resident, 79M data, 23M linkedit.
MemRegions: 276565 total, 2423M resident, 238M private, 890M shared.
PhysMem: 7328M used (1176M wired), 215M unused.
VM: 191T vsize, 3268M framework vsize, 199287(0) swapins, 465072(0) swapouts.
Networks: packets: 6769184/4186M in, 2333067/346M out.
Disks: 1659506/39G read, 1139452/21G written.
ID   COMMAND      %CPU TIME     #TH    #WQ  #PORT MEM    PURG   CMPRS  PGRP
8260  top          4.8  00:03.92 1/1    0    44    4946K  0B     160K   8260

```

만약 명령 프롬프트에 top을 입력한다면 화면에는 다음과 같은 형식의 이미지가 보여지게 됩니다.
>보여지는 정보들은 초당 한번씩 갱신되어 화면에 출력되게 됩니다.
---
# 1. top
### ID
프로세스 ID
>프로세스에 활당된 ID의 값을 표시합니다.
### %CPU
CPU 사용량 
>전체 CPU 중 프로세스가 사용하고 있는 양 입니다.
### TIME
작업이 시작된 이후 사용한 총 CPU 시간
### MEM
메모리 사용량
>프로세스가 사용하고 있는 메모리의 양 입니다.
---

# 2. ps 
### ps 명령어는 현재 실행중인 프로세스 목록과 상태를 보여줍니다.
+ top은 실시간으로 갱신되는 반면 ps는 명령을 실행한 순간의 프로세스를 보여줍니다.
+ cat 명령어의 형식으로 화면에 출력해줍니다.
``` bash
(base) /home/chosun/20203154/gitdir/readme.md ~ % ps
  PID TTY           TIME CMD
 8230 ttys000    0:00.05 -zsh
```
---

# 2. ps 
### ps는 여러가지 옵션을 가지고 있습니다.
|옵션|내용|
|:--:|:--:|
|-A|모든 프로세스를 출력한다.|
|-a|터미널에 종속되지 않은 모든 프로세스를 출력한다.|
|-e|커널 프로세스를 제외한 모든 프로세스를 출력해 준다.|
|-f|풀 포맷으로 보여준다.|
|-M|64비트 프로세스를 보여준다.|
|-m|프로세스들 뿐만 아니라 커널 스레드들도 보여준다.|

>이 외에도 '-o, -p ,-r -u' 등등 여러 옵션이 있지만 분량상 제가 사용할 옵션을 정리해보았습니다.
---
# 3. jobs
### jobs는 작업의 상태를 표시하는 명령어 입니다.
>jobs 명령어는 현재 쉘 프로세스의 자식 백그라운드 프로세스들을 보여줍니다.

``` bash
(base) /home/chosun/20203154/gitdir/readme.md ~ % sleep 100 &
[1] 8405
(base) /home/chosun/20203154/gitdir/readme.md ~ % jobs
[1]  + running    sleep 100
```
+ 다음과 같이 sleep 명령어를 백그라운드 실행모드로 실행하고 이를 jobs로 확인할 수 있습니다.
---
# 3. jobs
>jobs 명령어가 보여주는 상태에는 이러한 것들이 있습니다.


|상태|설명|
|:--:|:--:|
|Running|작업이 계속 진행중|
|Done|작업이 완료되어 0을 반환|
|Done(code)|작업이 완료되어 코드를 반환|
|Stopped|작업이 일시 중단|
---
# 4. kill
### kill 은 프로세스를 종료할 때 사용하는 명령어입니다.
``` bash
(base) naujin@naujin-ui-MacBookPro ~ % sleep 100 &
[1] 8461
(base) naujin@naujin-ui-MacBookPro ~ % ps
  PID TTY           TIME CMD
 8230 ttys000    0:00.09 -zsh
 8461 ttys000    0:00.00 sleep 100
(base) naujin@naujin-ui-MacBookPro ~ % kill -9 8461
[1]  + killed     sleep 100
(base) naujin@naujin-ui-MacBookPro ~ % ps
  PID TTY           TIME CMD
 8230 ttys000    0:00.10 -zsh
```
> sleep 명령어를 사용해 백그라운드 프로세스를 만들고 ps로 현재 진행중인 프로세스를 확인한 다음 kill 명령어의 옵션 -9를 사용해 프로세스를 직접 지정 종료해 보았습니다.
---
# 4. kill
### -9
+ 프로세스 아이디를 직접 지정하여 종료할 수 있습니다.
### -l
+ 신호로 사용할 수 있는 신호 이름들을 보여줍니다.
---
20203154 컴퓨터공학과 나우진



