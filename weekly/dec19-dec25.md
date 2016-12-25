### New Things This Week

#### Linux
* CentOS check ssh login log
 ```
 $ tail -n 10 /var/log/secure
 ```
* Time Zone
 ```
 $ dpkg-reconfigure
 ```
 will enter a graphical interface to configure timezone.

* Adding a new user with sudo privilege.[link1](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-14-04) [link2](https://www.digitalocean.com/community/tutorials/how-to-create-a-sudo-user-on-centos-quickstart)
 
 Generally speaking is a bad habbit to use root user as a daily use user.  
 Instead, we should use a normal user with sudo privilege.
 ```
 $ gpasswd -a username sudo          # Ubuntu
 $ usermod -aG wheel username        # CentOS
 ```
* Give write access to group users.
 ```
 $ chmod -R g+w directory
 ```
* How do multiple clients connect simultaneously to one port on a server? [link](http://stackoverflow.com/questions/3329641/how-do-multiple-clients-connect-simultaneously-to-one-port-say-80-on-a-server)
 
 A socket is identified by {SRC-IP, SRC-PORT, DEST-IP, DEST-PORT, PROTOCOL};  
 * Two clients connecting to same server port means: socket1 {SRC-A, 100, DEST-X,80, TCP} and socket2{SRC-B, 100, DEST-X,80, TCP};
 * Two clients can connect to same server port because for each client we can assign a different socket (as client IP will definitely differ). Same client can also have two sockets connecting to same server port - since such sockets differ by SRC-PORT;
 * Now as long as a server knows which request is associated with which socket, it can always respond to appropriate client using the same socket. Thus a server never needs to open another port in its own node than the original one on which client initially tried to bind.

* [link](http://stackoverflow.com/questions/33508997/waitpid-wnohang-wuntraced-how-do-i-use-these) *waitpid()* function. When *WNOHAN* option is specified, *waitpid()* will take a look at the processes specified by the first parameter of the function, and then:
 * If any zombie state process exist, one of them will be reaped, and its pid will be returned;
 * If all processes specified are still running(not terminated, or zombie), the function will do nothing and 0 will be returned;
 * If there are no processed specified by the first parameter, -1 will be return and errno will be set to ECHILD.

* tcpdump options:
 * -i specify interface to listen on.
 * -n display addresses rather than names.
 * -w write to file.
 * -Z specify user.
 * -r read from a -w output file.

#### Makefile
* Here is a very good tutorial for makefile beginners. [link](http://www.cs.colby.edu/maxwell/courses/tutorials/maketutor/)

* Example (for recall)

  ```
  IDIR =../include
  CC=gcc
  CFLAGS=-I$(IDIR)
  
  ODIR=obj
  LDIR =../lib
  
  LIBS=-lm
  
  _DEPS = hellomake.h
  DEPS = $(patsubst %,$(IDIR)/%,$(_DEPS))
  
  _OBJ = hellomake.o hellofunc.o 
  OBJ = $(patsubst %,$(ODIR)/%,$(_OBJ))
  
  
  $(ODIR)/%.o: %.c $(DEPS)
    $(CC) -c -o $@ $< $(CFLAGS)
  
  hellomake: $(OBJ)
    gcc -o $@ $^ $(CFLAGS) $(LIBS)
  
  .PHONY: clean
  
  clean:
    rm -f $(ODIR)/*.o *~ core $(INCDIR)/*~ 
  ```

* [**string substitution**](https://www.gnu.org/software/make/manual/html_node/Text-Functions.html)

  ```
  $(subst from,to,text)
  ```
 Performs a textual replacement on the text text: each occurrence of from is replaced by to. The result is substituted for the function call. For example:
  ```
  $(subst ee,EE,feet on the street)
  ```
  substitutes the string ‘fEEt on the strEEt’.

  ```
  $(patsubst pattern,replacement,text)
  ```
  Find whitespace-separated words in text that match pattern and replaces them with replacement. For example:
  ```
  $(patsubst %.c,%.o,x.c.c bar.c)
  ```
  produces the value ‘x.c.o bar.o’
  
  And there are many short-cuts listed in the link.

* [**Automatic Variables**](https://www.gnu.org/software/make/manual/html_node/Automatic-Variables.html#Automatic-Variables)

 * $@ The file name of the target of the rule.
 * $< The name of the first prerequisite.
 * $^ The names of all the prerequisites, with spaces between them.
 * $? The names of all the prerequisites that are newer than the target, with spaces between them.

#### Word Press Apache
* [Here](https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-on-ubuntu-14-04) is a very good tutorial for install wordpress with apache.  
Note: *www-data* user on Ubuntu is equivalent to *apache* user on CentOS.
Data should be owned by *apache* if you want them to be modified by your web scripts.
* Wordpress apache ownership setup.[link](http://stackoverflow.com/questions/28918996/proper-owner-of-var-www-html) google searche *who should be the owner of /var/www*
 CMSs like wordpress have bad support with the ownership of the files on Linux. The most convenient way to configure is to set all file under /var/www/html to be owned (and group owned) by www-data on Ubuntu(apache on CentOS), and give write access to www-data group.

#### Raspberry Pi
* [Here](https://frillip.com/using-your-raspberry-pi-3-as-a-wifi-access-point-with-hostapd/) is a good tutorial to set up a wifi hotspot using raspberry pi 3.

### Unsolved Problems