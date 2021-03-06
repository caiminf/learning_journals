### New Things This Week

#### Linux
* [Here](http://www.howtogeek.com/177621/the-beginners-guide-to-iptables-the-linux-firewall/) is a good tutorial for **iptables**
    ```
    iptables -L -v
    ```
    Basic usage to check the existing policies.

    ```
    iptables --policy INPUT ACCEPT
    iptables --policy OUTPUT ACCEPT
    iptables --policy FORWARD ACCEPT
    ```
    Accept connections by default.

* screen ctrl-A :quit to terminate all sessions.
* Unix signals [Some comman singal numbers](https://en.wikipedia.org/wiki/Unix_signal)

    Signal|Portable number|Default Action|Description
    --- | --- | --- | ---
    SIGCHLD|n/a|Ignor|Child process terminated, stopped, or continued.
    SIGINT|2|Terminate|Terminal interrupt signal.
    SIGKILL|9|Terminate|Kill (cannot be caught or ignored).
    SIGPIPE|n/a|Terminate|Write on a pipe with no one to read it.
    SIGQUIT|3|Terminate (core dump)|Terminal quit signal.
    SIGSTOP|n/a|Stop|Stop executing (cannot be caught or ignored).
    SIGSYS|n/a|Terminate (core dump)|Bad system call.
    SIGTERM|15|Terminate|Termination signal.
    SIGUSR1|n/a|Terminate|User-defined signal 1.
    SIGUSR2|n/a|Terminate|User-defined signal 2.

    
### Unsolved Problems

