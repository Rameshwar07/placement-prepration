# Linux Interview Questions and Answers (3 Years Experience)

This document contains **50 Linux interview questions with sample answers and commands** for professionals with around 3 years of experience.

---

## 🟢 Basic Linux & OS Concepts

**1. What is the difference between Linux and Unix?**  
- Unix is proprietary, Linux is open-source.  
- Linux runs on a wide range of hardware, while Unix is vendor-specific.  

**2. Explain the Linux boot process step by step.**  
1. BIOS/UEFI initializes hardware  
2. Bootloader (GRUB) loads  
3. Kernel loads  
4. `init` or `systemd` starts  
5. System services and login prompt  

**3. What are runlevels in Linux?**  
- 0: Halt  
- 1: Single-user mode  
- 3: Multi-user (CLI)  
- 5: Multi-user (GUI)  
- 6: Reboot  
- In `systemd`: runlevels replaced with *targets* (`graphical.target`, `multi-user.target`)  

**4. How do you check the current kernel version?**  
```bash
uname -r
5. How do you find out the Linux distribution and version?

bash
Copy
Edit
cat /etc/os-release
lsb_release -a
6. Difference between su and sudo.

su: switch user, requires root password.

sudo: execute commands as root, requires user password.

7. How does Linux handle process management?

Kernel scheduler manages processes.

Use commands like ps, top, kill, nice.

8. Explain the difference between hard link and soft link.

Hard link → points to same inode, file exists even if original deleted.

Soft link → shortcut (like Windows), breaks if target deleted.

9. What is inode in Linux?

Metadata structure storing file permissions, size, ownership, location.

10. How do you check CPU, memory, and disk usage in Linux?

bash
Copy
Edit
top
htop
free -h
df -h
🟡 File System & Storage
11. Explain different Linux file system types.

ext3: older, journaling.

ext4: default, supports large files.

xfs: scalable, good for large files.

btrfs: supports snapshots, advanced features.

12. Difference between swap partition and swap file.

Swap partition: dedicated disk area.

Swap file: created inside filesystem, flexible.

13. How do you check available disk space?

bash
Copy
Edit
df -h
14. Explain df vs du.

df: disk free space by filesystem.

du: disk usage by files/folders.

15. How do you extend a filesystem in Linux?

bash
Copy
Edit
lvextend -L +5G /dev/vg0/lv0
resize2fs /dev/vg0/lv0
16. What happens when root (/) filesystem is full?

System may freeze, services fail, root login needed to clear space.

17. How do you mount and unmount a filesystem?

bash
Copy
Edit
mount /dev/sdb1 /mnt
umount /mnt
18. How to make mount permanent in Linux?

Add entry in /etc/fstab.

19. What is LVM? How do you extend/shrink an LVM volume?

LVM = Logical Volume Manager.

Extend:

bash
Copy
Edit
lvextend -L +5G /dev/vg0/lv0
resize2fs /dev/vg0/lv0
Shrink (careful!):

bash
Copy
Edit
resize2fs /dev/vg0/lv0 5G
lvreduce -L 5G /dev/vg0/lv0
20. How do you check open files in Linux?

bash
Copy
Edit
lsof
🔵 Process & Services
21. Difference between process and thread.

Process = independent program with own memory.

Thread = lightweight execution unit inside a process.

22. How do you find the PID of a process?

bash
Copy
Edit
ps -ef | grep processname
pidof processname
23. What does the ps command do?

Shows snapshot of current processes.

24. Difference between top and htop.

top: CLI, default monitoring tool.

htop: interactive, colorful, scrollable.

25. How do you kill a process?

bash
Copy
Edit
kill <PID>
kill -9 <PID>   # force kill
pkill processname
26. What is nice and renice?

nice: start a process with priority.

renice: change priority of running process.

27. Explain systemctl and service.

systemctl: manage services in systemd.

service: older SysVinit service manager.

28. How do you check if a service is running?

bash
Copy
Edit
systemctl status nginx
29. How do you schedule a job in Linux?

With cron (repeated jobs) and at (one-time jobs).

30. Difference between /etc/cron.d, /etc/cron.daily, and user crontabs.

/etc/cron.d: system-wide cron jobs.

/etc/cron.daily: scripts run daily.

User crontabs: crontab -e.

🟣 Networking
31. How do you check active network interfaces?

bash
Copy
Edit
ip a
ifconfig
32. Difference between netstat, ss, and lsof -i.

netstat: legacy, shows connections.

ss: faster, modern replacement.

lsof -i: shows processes using ports.

33. How do you check if a port is open in Linux?

bash
Copy
Edit
ss -tuln | grep 80
34. How to assign an IP address temporarily and permanently?

bash
Copy
Edit
ip addr add 192.168.1.10/24 dev eth0   # temporary
Permanent: edit /etc/network/interfaces or NetworkManager configs.

35. What is /etc/hosts and /etc/resolv.conf?

/etc/hosts: static hostname mapping.

/etc/resolv.conf: DNS servers.

36. Explain DNS resolution process.

Checks /etc/hosts → DNS cache → /etc/resolv.conf → external DNS servers.

37. How do you capture packets in Linux?

bash
Copy
Edit
tcpdump -i eth0
38. How do you test connectivity without ping?

bash
Copy
Edit
curl http://example.com
nc -zv google.com 80
39. What is the use of iptables or firewalld?

Firewall configuration to allow/deny traffic.

40. How to check routing table in Linux?

bash
Copy
Edit
route -n
ip route show
🔴 Security & User Management
41. How do you create a new user in Linux?

bash
Copy
Edit
useradd -m ramesh
passwd ramesh
42. Difference between /etc/passwd and /etc/shadow.

/etc/passwd: user info (username, UID, shell).

/etc/shadow: encrypted passwords.

43. How do you check user’s group membership?

bash
Copy
Edit
groups username
id username
44. How to change user password expiry settings?

bash
Copy
Edit
chage -l username
chage -M 30 username   # set max days
45. Explain Linux file permissions (rwx).

r = read, w = write, x = execute.

Example: chmod 755 file.

46. What are SUID, SGID, and sticky bit?

SUID: run file with owner's privileges.

SGID: run with group privileges.

Sticky bit: only owner can delete files in dir.

47. How to set ACLs on a file/directory?

bash
Copy
Edit
setfacl -m u:john:rwx file.txt
getfacl file.txt
48. How do you check last login details of a user?

bash
Copy
Edit
last username
49. How do you check failed login attempts?

bash
Copy
Edit
lastb
cat /var/log/secure
50. How do you secure SSH in Linux?

Disable root login in /etc/ssh/sshd_config

Use key-based authentication

Change default port (optional)

Use firewall rules

