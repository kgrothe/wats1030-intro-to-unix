# *nix Scavenger Hunt

Complete the following challenges using the command-line interface on your favorite
Unix or Linux operating system. You are welcome and encouraged to consult any
additional documentation online or in books.

Please add your answers/responses/text pastes to the document after each prompt.

Note: For some of the challenges you will need to reference files included with
this repository, so you will need to fork the repo into your own Github account
and then clone it to your development environment.

## The Challenges

### Navigating the Filesystem

* Get an idea of where you are in the operating system. Use the `pwd` command to find your "path to working directory"--your current location in the filesystem of your devbox. *Paste the output of the `pwd` command here:*

>/projects

* Discover more about this filesystem. Use `ls` (the "list" command)to see what is in this directory. *What directories and files do you see when you run `ls`?*

>wats1030-intro-to-unix

* You can use *options* to modify how a command runs. Try using `ls -alh` to see the contents of your current directory. *How are the results different when you use the `-alh` options?*

>total 0

>drwxr-xr-x  3 user root  36 Jul  5 13:19 .

>drwxr-xr-x 22 root root 295 Jul  8 21:08 ..

>drwxr-xr-x  5 user root 178 Jul  5 13:19 wats1030-intro-to-unix



* The `man` ("manual") command tells you more about how any given command works. (*WARNING:* CodeAnywhere does not support the man command. You can click the following link to complete this task: http://man.he.net/). Run `man` to see instructions about how to use `man`. Then use `man` to learn what the `a`, `l`, and `h` options mean when used with the `ls` command. *Write down what those options do?*

>  a: means "all". Will display all the manual pages that match the search criteria rather than exiting after finding the     most suitable one

>  l: activate "local" mode. Format and display local manual files rather than searching through the system's manual files

>  h: means "help". Print a help message and exit.


* Commands can also take *arguments*, which are usually the names of files or locations that you want the command to work with. Try running `ls /` to see what files are in the *root* directory of the filesystem. *What files and directories do you see listed?*

>bin  boot  dev  etc  home  lib  lib64  media  mnt  open-jdk-source-file-location  opt  proc  projects  root  run  sbin  srv  sys  tmp  usr  var
     

* A Unix filesystem has a few special shortcuts to refer to specific locations. `/` indicates the *root* of the filesystem, meaning the top-most directory in the filesystem hierarchy. Use the `cd` ("change directory") command to move to the root directory. (Hint: Use `man` to look up the `cd` command if you have any issues) *Then run `pwd` and paste the output here:*

>/

* Another special shortcut in Unix is the `~` location. This indicates the *user root* directory, meaning the top-most directory in the hierarchy that comes below your user account. Use `cd` to move to `~`. *Run `pwd` and paste the response here:*

>/home/user

* Change directory into the `challenge_files` directory. Use `ls` to find only the files with a `.demo` pattern. *How many files do you find?*

>3 (2015_special_stuff.demo,  cloaked-wookie.demo,  scooter-double-mamba.demo)

* Use the `cd` command to move "up" one directory. *Where are you in the filesystem now?*

 >/projects/wats1030-intro-to-unix

* Press the up arrow on your keyboard. *What just happened?*

 >last command I entered (pwd) appeared

* Press the up arrow a few more times. *What do you see?*

>last commands entered appear, starting with latest command used

* Run the `history` command. *What do you see?*

>A list of all commands entered appear


### Observing the System

* Discover what account you are logged into using the `whoami` command. *What username are you currently using?*

> "user"

* Discover who else is on your system with the `who` command. *Are any other users using your system? If so, list them here:*


 >no one else is on my system

* How long has your system been running? Use `uptime` to see, and *paste the result here:*

>17:19:57 up 6 days,  9:13

* Run `ps aux` and review the results. (Hint: Use `man` to learn more about the `ps` command and options.) *How do you interpret what you see here?*

>PS = "process status". This is a report of current processes running. The "a" displays all users, 
"u" displays user  column in output, 
"x" displays processes not executed from any terminal. <br>

>I'm seeing "user" (me) and "root" in the USER column. 

* Run `top` and review the results. (Hint: You may need to use `ctrl-c` to get out of this app.) *How do you interpret what you see here?*

>"Top" displays the same information as ps aux, but information is being updated continuosly. In referring to resources, I see that >"top" displays processes as they are running in real time.

### Finding and Viewing Files

* Make sure you are in the `challenge_files` directory. Use the `*` wildcard to find all the files that have the word "credit" in the filename. *How many files did you find?*

>2

* credit_cards2.txt
* credit_cards.txt

* Use the `more` command to view one of the `credit_cards` files you just discovered. (Hint: Type `q` to quit viewing the file. Press the `spacebar` to page down. Use your keyboard arrows to move up/down.) *What is the date in the file you have viewed?*

>01-15-2015

* Use the `find` command to search for files more effectively. Search the sub-directories under `challenge_files` to find the location of the file named `modi_laboriosam.txt`. *Where is that file located?*

 >/tmp

* Use the `grep` command to search for text within a file. Use `grep` on all the `.user` files in `challenge_files` to find which files contain "WA" (the abbreviation for Washington state). *How many files did you find?*

>2 -
>Britt-Erdman.user                                                                                                                >Lissie-Strosin.user


* Use the `-r` option of `grep` to *recursively* find the text "Waldo" hidden in a file somewhere under the `challenge_files` directory. *Paste the result showing the file and line where the word "Waldo" shows up.*

>serial-numbers/eaque_molestiae.txt:Ut est maiores quia autem. Nisi modi Waldo sed corporis sit explicabo ut est. Et est placeat ea sunt sunt consectetur sunt incidunt. Explicabo vel esse blanditiis dolorem culpa non quia.


### Pipes and Connecting Commands

* Sometimes it's useful to output the results of a command to a text file for further analysis, reference, or processing. Try running `ls > files.txt`. Notice that the file `files.txt` was created. View that file using `more`. *What do you see in the `files.txt` file?*

>It looks like all files in the challenge-files folders are now in this file.

* Notice that if you run `ls -alh` in the `challenge_files` directory, the files scroll by very quickly. Sometimes it would be better to get the results in a paginated format. Try running `ls -alh | more`. *Describe what you see when you run `ls -alh | more`.*

>There is no automatic scrolling. One page is displayed at a time. I can use the space bar and scroll to view the results.

* Earlier, when you viewed the list of active processes on your devbox using `ps aux`, the list was probably really long. You can make this list more manageable by using the pipe (`|`) to filter the results of `ps` using `grep`. Run `ps aux | grep <your_username>` to see what processes are running for your specific user. *Paste the list of processes that reference your username here:*


user         1  0.0  0.0   4500   640 ?        Ss   20:10   0:00 /bin/sh -c tail -f /dev/null                                                                                      user        26  0.0  0.0   6036   624 ?        S    20:10   0:00 tail -f /dev/null                                                                                                 user        31  0.0  0.0   4508   748 ?        Ss   20:10   0:00 /bin/sh -c trap
 
