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
