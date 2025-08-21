# Linux Interview Questions and Answers (3 Years Experience)

This document contains **50 Linux interview questions with sample answers and commands** for professionals with around 3 years of experience.

---

## 🟢 Basic Linux & OS Concepts

**1. What is the difference between Linux and Unix?**  
- Unix is the original proprietary OS, Linux is an open-source clone inspired by Unix.  
- Linux is widely used in servers, cloud, and DevOps.  

**2. Explain the Linux boot process step by step.**  
1. BIOS/UEFI  
2. Bootloader (GRUB)  
3. Kernel loads  
4. `init` or `systemd` starts  
5. Runlevel/targets initialize  

**3. What are runlevels in Linux?**  
- Runlevels define the state of the machine.  
- 0: Halt, 1: Single-user, 3: Multi-user (CLI), 5: GUI, 6: Reboot.  
- Modern systems use `systemd targets`.  

**4. How do you check the current kernel version?**  
```bash
uname -r
```

**5. How do you find out the Linux distribution and version?**  
```bash
cat /etc/os-release
lsb_release -a
```

**6. Difference between `su` and `sudo`.**  
- `su` switches user (needs root password).  
- `sudo` executes command as root (needs user password).  

**7. How does Linux handle process management?**  
- Scheduler manages processes.  
- Commands: `ps`, `top`, `kill`, `nice`.  

**8. Explain the difference between hard link and soft link.**  
- Hard link → direct reference to inode.  
- Soft link (symlink) → pointer to another file.  

**9. What is inode in Linux?**  
- Metadata structure storing file details (permissions, size, blocks).  

**10. How do you check CPU, memory, and disk usage in Linux?**  
```bash
top
htop
free -h
df -h
```

---

## 🟡 File System & Storage

**11. Explain different Linux file system types.**  
- ext3 (old, journaling), ext4 (default, large files), xfs (scalable), btrfs (snapshots).  

**12. Difference between swap partition and swap file.**  
- Swap partition → dedicated disk space.  
- Swap file → file inside filesystem.  

**13. How do you check available disk space?**  
```bash
df -h
```

**14. Explain `df` vs `du`.**  
- `df`: free space per filesystem.  
- `du`: disk usage per file/folder.  

**15. How do you extend a filesystem in Linux?**  
```bash
lvextend -L +5G /dev/vg0/lv0
resize2fs /dev/vg0/lv0
```

**16. What happens when root (/) filesystem is full?**  
- System becomes unstable, services may fail, root login required to clear space.  

**17. How do you mount and unmount a filesystem?**  
```bash
mount /dev/sdb1 /mnt
umount /mnt
```

**18. How to make mount permanent in Linux?**  
- Add entry in `/etc/fstab`.  

**19. What is LVM? How do you extend/shrink an LVM volume?**  
- Logical Volume Manager for flexible storage.  
- Extend: `lvextend`, `resize2fs`.  
- Shrink: `resize2fs`, `lvreduce`.  

**20. How do you check open files in Linux?**  
```bash
lsof
```

---

## 🔵 Process & Services

**21. Difference between process and thread.**  
- Process: independent program.  
- Thread: lightweight, shares process resources.  

**22. How do you find the PID of a process?**  
```bash
ps -ef | grep processname
pidof processname
```

**23. What does the `ps` command do?**  
- Displays currently running processes.  

**24. Difference between `top` and `htop`.**  
- `top`: default process viewer.  
- `htop`: interactive and more user-friendly.  

**25. How do you kill a process?**  
```bash
kill <pid>
kill -9 <pid>   # force kill
pkill processname
```

**26. What is `nice` and `renice` in Linux?**  
- `nice`: start a process with priority.  
- `renice`: change priority of running process.  

**27. Explain `systemctl` and `service` command.**  
- `systemctl`: manage services in systemd.  
- `service`: manage services in SysV init.  

**28. How do you check if a service is running on Linux?**  
```bash
systemctl status sshd
```

**29. How do you schedule a job in Linux? (cron & at)**  
- `cron`: repeated jobs.  
- `at`: one-time jobs.  
```bash
crontab -e
at 10:00 AM tomorrow
```

**30. Difference between `/etc/cron.d`, `/etc/cron.daily`, and user crontabs.**  
- `/etc/cron.d`: system-wide cron jobs.  
- `/etc/cron.daily`: runs daily.  
- User crontabs: specific to users.  

---

## 🟣 Networking

**31. How do you check active network interfaces?**  
```bash
ip a
ifconfig
```

**32. Difference between `netstat`, `ss`, and `lsof -i`.**  
- `netstat`: old, shows connections.  
- `ss`: faster alternative.  
- `lsof -i`: shows open network files.  

**33. How do you check if a port is open in Linux?**  
```bash
ss -tulnp | grep 80
```

**34. How to assign an IP address to an interface temporarily and permanently?**  
```bash
ip addr add 192.168.1.10/24 dev eth0   # temporary
/etc/sysconfig/network-scripts/ifcfg-eth0   # permanent (RHEL)
```

**35. What is `/etc/hosts` and `/etc/resolv.conf`?**  
- `/etc/hosts`: local hostname resolution.  
- `/etc/resolv.conf`: DNS configuration.  

**36. Explain DNS resolution process in Linux.**  
- Order: `/etc/hosts` → DNS resolver (`resolv.conf`) → DNS server.  

**37. How do you capture packets in Linux?**  
```bash
tcpdump -i eth0
```

**38. How do you test connectivity without `ping`?**  
```bash
curl -I http://example.com
nc -zv example.com 80
```

**39. What is the use of `iptables` or `firewalld` in Linux?**  
- Manage firewall rules and network traffic.  

**40. How to check routing table in Linux?**  
```bash
ip route
netstat -rn
```

---

## 🔴 Security & User Management

**41. How do you create a new user in Linux?**  
```bash
useradd username
passwd username
```

**42. Difference between `/etc/passwd` and `/etc/shadow`.**  
- `/etc/passwd`: user details.  
- `/etc/shadow`: encrypted passwords.  

**43. How do you check user’s group membership?**  
```bash
groups username
id username
```

**44. How to change user password expiry settings?**  
```bash
chage -l username
chage -M 30 username
```

**45. Explain Linux file permissions (rwx).**  
- r = read, w = write, x = execute.  

**46. What are SUID, SGID, and sticky bit?**  
- SUID: execute with file owner’s privilege.  
- SGID: execute with group privilege.  
- Sticky bit: restrict deletion to owner.  

**47. How to set ACLs on a file/directory?**  
```bash
setfacl -m u:username:rwx file
getfacl file
```

**48. How do you check last login details of a user?**  
```bash
last username
```

**49. How do you check failed login attempts?**  
```bash
lastb
cat /var/log/secure
```

**50. How do you secure SSH in Linux?**  
- Disable root login.  
- Use SSH keys instead of passwords.  
- Change default port.  
- Configure `sshd_config`.  

---
