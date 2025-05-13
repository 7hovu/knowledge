### **一、文件与目录操作**

1. **浏览与切换**
    
    - `ls`：列出目录内容  
        `-l` 详细信息，`-a` 显示隐藏文件，`-h` 易读格式。
        
    - `cd`：切换目录  
        `cd ~` 返回家目录，`cd ..` 返回上级。
        
    - `pwd`：显示当前目录路径。
        
2. **创建与删除**
    
    - `mkdir`：创建目录  
        `-p` 递归创建（如 `mkdir -p dir1/dir2`）。
        
    - `rmdir`：删除空目录。
        
    - `rm`：删除文件/目录  
        `-r` 递归删除，`-f` 强制删除（谨慎使用 `rm -rf`）。
        
3. **复制、移动与重命名**
    
    - `cp`：复制文件/目录  
        `-r` 复制目录，`-i` 覆盖前提示。
        
    - `mv`：移动或重命名文件/目录。
        
4. **查看与编辑文件**
    
    - `cat`：显示文件内容。
        
    - `more`/`less`：分页查看文件。
        
    - `head`/`tail`：查看文件头部/尾部（`tail -f` 实时追踪日志）。
        
    - `touch`：创建空文件或更新文件时间戳。
        
5. **搜索与权限**
    
    - `find`：实时搜索文件（如 `find /home -name "*.txt"`）。
        
    - `locate`：快速搜索（需先运行 `updatedb` 更新数据库）。
        
    - `chmod`：修改权限  
        数字模式（`chmod 755 file`）或符号模式（`chmod u+x file`）。
        
    - `chown`：修改所有者（如 `chown user:group file`）。
        

---

### **二、系统信息与管理**

1. **系统状态**
    
    - `uname -a`：查看系统内核信息。
        
    - `df -h`：显示磁盘空间。
        
    - `free -h`：查看内存使用情况。
        
    - `top`/`htop`：实时监控进程和资源。
        
2. **进程管理**
    
    - `ps`：查看进程  
        `ps aux` 显示所有进程。
        
    - `kill [PID]`：终止进程，`kill -9` 强制终止。
        
    - `killall [进程名]`：按名称终止进程。
        
3. **开关机与用户**
    
    - `shutdown`：关机/重启（`shutdown now` 立即关机）。
        
    - `reboot`/`poweroff`：重启/关机。
        
    - `useradd`/`userdel`：添加/删除用户。
        
    - `passwd`：修改密码。
        
    - `su`/`sudo`：切换用户或以管理员权限运行命令。
        
4. **服务管理**
    
    - `systemctl start/stop/restart [服务名]`：管理系统服务（Systemd系统）。
        

---

### **三、网络相关**

1. **连接与配置**
    
    - `ping [域名/IP]`：测试网络连通性（`-c 4` 指定次数）。
        
    - `ifconfig`/`ip addr`：查看网络接口信息。
        
    - `netstat -tulnp`：查看端口监听状态。
        
    - `ss`：替代 `netstat`，显示更详细网络信息。
        
2. **文件传输与测试**
    
    - `wget [URL]`：下载文件。
        
    - `curl [URL]`：发送HTTP请求并显示结果。
        
    - `scp`：安全复制文件（如 `scp file user@host:/path`）。
        
3. **路由与防火墙**
    
    - `route`/`ip route`：查看路由表。
        
    - `ufw`：简化防火墙配置（Ubuntu）。
        

---

### **四、软件包管理**

- **Debian/Ubuntu (APT)**  
    `apt update` 更新源，`apt install [包名]` 安装，`apt remove [包名]` 卸载。
    
- **RedHat/CentOS (YUM/DNF)**  
    `yum install [包名]` 或 `dnf install [包名]`。
    
- **Arch (Pacman)**  
    `pacman -S [包名]` 安装，`pacman -Syu` 更新系统。
    
- **openSUSE (Zypper)**  
    `zypper install [包名]`。
    

---

### **五、压缩与解压**

- `tar -czvf file.tar.gz dir`：压缩为.tar.gz。
    
- `tar -xzvf file.tar.gz`：解压.tar.gz。
    
- `zip -r file.zip dir`：压缩为.zip。
    
- `unzip file.zip`：解压.zip。
    

---

### **六、文本处理**

- `grep "text" file`：搜索文本（`-i` 忽略大小写，`-r` 递归目录）。
    
- `sed 's/old/new/g' file`：替换文本。
    
- `awk '{print $1}' file`：提取第一列。
    
- `sort file`：排序，`uniq` 去重，`diff file1 file2` 比较差异。
    

---

### **七、其他实用命令**

- `history`：查看命令历史。
    
- `alias`：创建别名（如 `alias ll='ls -l'`）。
    
- `crontab -e`：编辑定时任务。
    
- `man [命令]`：查看命令手册。
    
- `ln -s [源文件] [链接名]`：创建软链接。