###New Things This Week

####Git Usages
------
* Shows information about current repository.
 ```
 $ git config --list
 ```
 
* Print all your remotes' fetch/push URLs.[link](http://stackoverflow.com/questions/4089430/how-can-i-determine-the-url-that-a-local-git-repository-was-originally-cloned-fr)
 ```
 $ git remote -v
 ```

* Create a git repository in the remote server.[link](http://stackoverflow.com/questions/6648995/how-to-create-a-remote-git-repository-from-a-local-one)
 ```
 $ git clone --bare my_project my_project.git
 $ scp -r my_project.git user@git.example.com:/opt/git
 ```
 Now other user who have ssh access to the same server which has read-access to */opt/git* directory can clone your repository by running
 ```
 $ git clone user@git.example.com:/opt/git/my_project.git
 ```

* Three ways to untrack changes of files.[link](https://help.github.com/articles/ignoring-files/)
  1. Creating a local .gitignore file
    1. In Terminal, navigate to the location of your Git repository.
    2. Enter _touch .gitignore_ to create a .gitignore file.
       If you already have a file checked in, and you want to ignore it, Git will not ignore the file if you add a rule later. In those cases, you must untrack the file first, by running the following command in your terminal:
       ```shell
       $ git rm --cached FILENAME
       ```
  2. Creating a global .gitignore
    ```
    $ git config --global core.excludesfile ~/.gitignore_global
    ```
  3. Explicit repository excludes
    Edit the file .git/info/exclude.

* Compare the current file with the most recent commit.
 
 ```shell
 $ git diff myfile.txt            # Not added yet
 $ git diff --cached myfile.txt   # Already added
 ```

* Git global configuration
 *~/.gitconfig* is the global configuration file for git. Global variables like email and name will be stored in it. You can also add alias for git commands in it.

 ```
 [alias]
	co = checkout
	br = branch
	st = status
 ```
 and so on.

####Mark Usages
------
```
*italic*
_italic_

**bold**
__bold__

[link text](link address)
[link text][ref tag]
[ref tag]: link adress

![alt text](image link address)
![alt text][ref tag]
[ref tag]: image link address

>block quote
>
>another block quote

1. item1
 some paragraph
2. item2
 * sub item1
 * sub item2
3. item3

hard break
\n\n
soft break
  \n
```
*italic*

**bold**

[link text](link address)  
[link text][ref tag]  
[ref tag]: link adress

![alt text](image link address)  
![alt text][ref tag]  
[ref tag]: image link address

>block quote
>
>another block quote

1. item1
 some paragraph
2. item2
 * sub item1
 * sub item2
3. item3

####Vim Usages
------
* Short cuts
 ```
 ^E # scroll the window down
 ^Y # scroll the window up
 ^F # scroll down one page
 ^B # scroll up one page
 H  # move cursor to the top of the window
 M  # move cursor to the middle of the window
 L  # move cursor to the bottom of the window
 I  # move to the beginning of the line and switch to insert mode
 ```

* redo Ctrl R

* Vundle.[link](https://github.com/VundleVim/Vundle.vim)
 Vundle is short for Vim bundle and is a Vim plugin manager.
 Just clone the repository into specify location using git
 ```
 $ git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
 ```
 and paste the configure file on top of .vimrc file.  
 Then you can launch vim and run *:PluginInstall* to install plugins.

* My .vimrc settings
 ```
 Plugin 'jiangmiao/auto-pairs'

 set number  
 set tabstop=4  
 set shiftwidth=4  
 set softtabstop=4  
 ```

####Linux
------
* All ports are listed in /etc/services
* Program indication
  ```shell
  #!/bin/bash
  ```
  This is a special clue given to the shell indicating what program is used to interpret the script. In this case, it is /bin/bash. Other scripting languages such as perl, awk, tcl, Tk, and python can also use this mechanism.

* Cron job.[link](http://www.computerhope.com/unix/ucrontab.htm)
 ```
 $crontab -e
 ```
 Open and edit crontable file to make cron jobs.

 To define the time you can provide concrete values for minute (m), hour (h), day of month (dom), month (mon), and day of week (dow) or use '*' in these fields (for 'any')

 For example:  
 ```
 * 10 * * * cd /home/mitchell/Desktop/weibo_weather_robot/;./send_weather_weibo.py >> ./log 2>&1
 ```
 creates a cron job to be execute every day at 10a.m.

 **crontab options:**

 -l Display the current crontab.  
 -r Remove the current crontab.  
 -e Edit the current crontab.

* Tail options.[link](https://www.linode.com/docs/tools-reference/tools/view-and-follow-the-end-of-text-files-with-tail)
 *-n number* specify how many lines to be printed.
 *-f* follow mode. When new lines are added they are printed to the terminal.

* Check out the route table
 ```
 $ route -n
 $ netstat -rn
 ```

* Static IP address.[link1](https://www.howtoforge.com/linux-basics-set-a-static-ip-on-ubuntu)[link2](https://help.ubuntu.com/lts/serverguide/network-configuration.html)
 open file */etc/network/interfaces*
 ```
 auto eth0
 iface eth0 inet static
        address xxx.xxx.xxx.xxx(enter your ip here)
        netmask xxx.xxx.xxx.xxx
        gateway xxx.xxx.xxx.xxx(enter gateway ip here,usually the address of the router)
        dns-nameservers xxx.xxx.xxx.xxx
 ```
 and then restart network
 ```
 $ sudo ifdown eth0;sudo ifup eth0
 ```

* Disable ssh user password login
 In file */etc/ssh/sshd_config*, change
 ```
 #PasswordAuthentication yes
 ```
 to
 ```
 PasswordAuthentication no
 ```
 and then restart ssh service
 ```
 $ service ssh restart
 ```

* Count lines in a file
 ```
 $ wc -l FILENAME
 ```

* cron job
 Notice that first parameter * means every minute.

####Raspberry Pi
------
* Raspberry pi has a semi-graphical configure interface
 ```
 $ sudo raspi-config
 ```
 which can allow you to change login method(disabling gui login) and start ssh service.

* Root user
 root user in Raspberry Pi is not set by default.

 *sudo* will let you run commands with super user privileges.

 To set the root password you could write:
 ```
 sudo passwd root
 ```
 But for general running this is not needed, as you can run commands using sudo.

####Python
------
* Print Chinese characters.[link](http://stackoverflow.com/questions/2688020/how-to-print-chinese-word-in-my-code-using-python)
 First need to declare an encoding
 ```python
 # -*- coding: utf-8 -*-
 ```
 then
 ```python
 print u'哈哈'.encode('utf-8')
 ```

* Time string format
 strftime() function series is for formatting time string.
 ```python
 >>> from datetime import datetime
 >>> datetime.now().strftime('%Y-%m-%d %H:%M:%S')
 '2011-05-03 17:45:35.177000'

 >>> from time import gmtime, strftime
 >>> strftime("%Y-%m-%d %H:%M:%S", gmtime())
 '2009-01-05 22:14:39'
 ```

####Others
------
* 443 is the port for https
* Install apache php wordpress on Tencent Cloud Service
  [云服务器 云数据库 搭建wordpress博客](http://bbs.qcloud.com/thread-849-1-1.html)
  Be careful about the security setting. Make sure port 80 is open to public access.
* [thinkpage](http://www.thinkpage.cn/)is a website to fetch weather information easily.

 Just register and send http request as asked, json format message including all kinds of information will be returned.

###Unsolved Problems

* gcc x86 calling conventions[link](https://pdos.csail.mit.edu/6.828/2016/lec/l-x86.html)

assembly code
