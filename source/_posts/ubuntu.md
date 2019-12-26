---
title: ubuntu
date: 2019-07-17 17:34:01
tags:
---


**how to create more users in ubuntu**

reference: https://blog.csdn.net/timothy93bp/article/details/77679000

---

**how to copy the entire dict to another user**

reference: https://www.cnblogs.com/zdz8207/p/linux-cp-dir.html

example:
cp -r dir1 dir2
cp -r dir1 /home/jack

---

**pay attention to the path**

conda install spyder
conda install tensorflow-gpu

---

**supervise the status of CPU and GPU**

- for GPU:	watch -n 10 nvidia-smi
- for CPU:	sudo apt-get install htop	htop

---

**how to run python without hangup in terminal**
1. nohup python -u main.py > nohup.out 2>&1 &   -> run
2. tail -fn 50 nohup.out 			-> check the progress
3. jobs, jobs -l, kill -9 PID                 	-> kill the progress