# ssh 使用笔记

## 在远程主机重装或密匙变更后ssh无法登陆的处理方法

```shell
#登陆远程主机
ssh hcy@192.168.31.91
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the ECDSA key sent by the remote host is
SHA256:bw/xTvE023iScVjww3QWD87zV+2b6k/0TguO2ZyEgd8.
Please contact your system administrator.
Add correct host key in /Users/leo/.ssh/known_hosts to get rid of this message.
Offending ECDSA key in /Users/leo/.ssh/known_hosts:1
ECDSA host key for 192.168.31.91 has changed and you have requested strict checking.
Host key verification failed.

#更新远程主机密匙
ssh-keygen -R 192.168.31.91(远程主机IP)
# Host 192.168.31.91 found: line 1
/Users/leo/.ssh/known_hosts updated.
Original contents retained as /Users/leo/.ssh/known_hosts.old
```

