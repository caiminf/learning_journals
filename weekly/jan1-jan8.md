### New Things This Week

#### Markdown
------
* In order to configure image size in markdown, you should use html directory.
  ```
  <img src="drawing.jpg" alt="Drawing" style="width: 200px;"/>
  ```
  [ref](http://stackoverflow.com/questions/14675913/how-to-change-image-size-markdown)

#### Linux
------
* delay a command to be execute, you can run
    ```
    $ sleep 5; command;
    ```

* *history* is a very useful command. It keeps track of the command you typed in, and can reuse it.
    * !n       # Refer to command line n.
    * !-n      # Refer to the current command line minus n.
    * !!       # Refer to the previous command. This is a synonym for '!-1'.
    * !string  # Refer to the most recent command starting with string.

* Static ARP table. [link](http://xmodulo.com/how-to-add-or-remove-static-arp-entry-on-linux.html)
    Sometimes it's useful to setup static ARP table for some scenario.
    ```
    $ arp -s xxx.xxx.xxx.xxx xx:xx:xx:xx:xx:xx # set a map between ip address and mac address
    $ arp -d xxx.xxx.xxx.xxx                   # remove the map

### Unsolved Problems
