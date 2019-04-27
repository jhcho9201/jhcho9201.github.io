---
title: "SYS/BIOS study"
date: 2019-04-13 16:26:28 -0400
categories: RTOS
---

TI사의 SYS/BIOS는 pre-emptive 스케줄러를 사용해서 우선순위가 높은 쓰레드를 가장 먼저 실행한다.
1. high priority 쓰레드
2. mid priority 쓰레드
3. low priority 쓰레드

Q) 만약 high, mid가 CPU를 100% 사용하고 있다면, low 우선순위의 쓰레드는 실행될까?
A) No


