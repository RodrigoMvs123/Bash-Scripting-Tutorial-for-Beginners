# Bash-Scripting-Tutorial-for-Beginners

https://www.youtube.com/watch?v=tK9Oc6AEnR4

https://raw.githubusercontent.com/RodrigoMvs123/Bash-Scripting-Tutorial-for-Beginners/master/README.md

https://github.com/RodrigoMvs123/Bash-Scripting-Tutorial-for-Beginners/blame/master/README.md

What will you need?
01 WSL - We will use WSL on windows (Ubuntu)
02 Real Linux Distro - True linux distro encouraged ! Ex: Ubuntu LTS 
03 Mac OK ! - Mac can use the mac terminal if Bash is shell 
04 Disclaimer - Disclaimer: Basic Linux knowledge required !

Basic Commands

herbert@DESKTOP-UFIA6QU:~/tutorial-bash$ echo Hello
Hello  
herbert@DESKTOP-UFIA6QU:~/tutorial-bash$ vim textfile.txt

- - INSERT - -

Hello World ! 

: w

“textfile.txt” [NEW] 1L, 13C written
 
:q ( To exit the file ) 

herbert@DESKTOP-UFIA6QU:~/tutorial-bash$ vim textfile.txt
herbert@DESKTOP-UFIA6QU:~/tutorial-bash$ 

Hello World ! 

“textfile.txt” 1L, 13C

:wq

herbert@DESKTOP-UFIA6QU:~/tutorial-bash$ textfile.txt

Hello World !

:q! 

herbert@DESKTOP-UFIA6QU:~/tutorial-bash$ cat textfile.txt 
Hello World ! 

herbert@DESKTOP-UFIA6QU:~/tutorial-bash$ 

Writing your first bash script 


herbert@DESKTOP-UFIA6QU:~/tutorial-bash$ vim shelltest.sh 

“sheltest.sh” [NEW FILE]

- - INSET - -          0,1

echo Hello World !            1,18 
 
:wq 

herbert@DESKTOP-UFIA6QU:~/tutorial-bash$ ls
shelltest.sh textfile.txt 
herbert@DESKTOP-UFIA6QU:~/tutorial-bash$ pwd
/home/hebert/tutorial-bash
herbert@DESKTOP-UFIA6QU:~/tutorial-bash$ bash shelltest.sh 
Hello World !
herbert@DESKTOP-UFIA6QU:~/tutorial-bash$ echo $SHELL
/bin/bash
herbert@DESKTOP-UFIA6QU:~/tutorial-bash$ vim shelltest.sh

#!/bin/bash
echo Hello World !

- - INSERT - -
:wq

herbert@DESKTOP-UFIA6QU:~/tutorial-bash$ ./shelltest.sh
-bash: ./shelltest.sh: Permission denied

herbert@DESKTOP-UFIA6QU:~/tutorial-bash$ ls -l

-rw-r- - r- - 1 hebert hebert 30 DEC 26 11:34 shelltest.sh
-rw-r- -r - - 1 hebert hebert 13 DEC 26 11:20 textfile.txt 

herbert@DESKTOP-UFIA6QU:~/tutorial-bash$ chmod u+x shelltest.sh
herbert@DESKTOP-UFIA6QU:~/tutorial-bash$ ./shelltest.sh 
Hello World ! 
herbert@DESKTOP-UFIA6QU:~/tutorial-bash$ 

Variables 


#!bin/bash

## NOT GOOD >>
cp /my/location/from/my/location/to
cp /my/location/from/here/my/location/to/there

## BETTER

MY_LOCATION_FROM=/my/location/from
MY_LOCATION_TO=/my/location/to 

cp $MY_LOCATION_FROM $MY_LOCATION_TO

cp “$MY_LOCATION_FROM/here” “$MY_LOCATION_TO/there”
                
                                                                                                              15,51

herbert@DESKTOP-UFIA6QU:~/tutorial-bash$ FIRST_NAME=Herbert 
hebert@DESKTOP-UFIA6QU:~/tutorial-bash$ echo Hello $FIRST_NAME
Hello Herbert 
hebert@DESKTOP-UFIA6QU:~/tutorial-bash$ vim hellothere.sh

- - INSERT - -  

#!/bin/bash

FIRST_NAME=Herbert
LAST_NAME=Lindemans
echo Hello $FIRST_NAME $LAST_NAME 

:wq

hebert@DESKTOP-UFIA6QU:~/tutorial-bash$ chmod u+x hellotherer.sh
hebert@DESKTOP-UFIA6QU:~/tutorial-bash$ ./hellotherer.sh
Hello Herbert Lindemans 
hebert@DESKTOP-UFIA6QU:~/tutorial-bash$ vim interactiveshell.sh 

- - INSERT - - 

#!/bin/bash 

echo What is your first name? 
read FIRST_NAME
echo What is your last name? 
read LAST_NAME 

echo Hello $FIRST_NAME $LAST_NAME 

:wq

hebert@DESKTOP-UFIA6QU:~/tutorial-bash$ chmod u+x interactiveshell.sh 
hebert@DESKTOP-UFIA6QU:~/tutorial-bash$ ./interactiveshell.sh 
What is your first name?
Herbert 
What is your last name?
Lindemans
Hello Herbert Lindemans 
hebert@DESKTOP-UFIA6QU:~/tutorial-bash$ 

Positional Arguments


Arguments are a specific positions 
Commands can take in arguments at a specific position counting from one (0 reserved for the shell)
$ echo Hello There !
$ echo o Hello o There !   
      0          1           2

hebert@DESKTOP-UFIA6QU:~/tutorial-bash$ vim posargu.sh

- - INSERT - -

#!/bin/bash

echo Hello $1 $2 

:wq

hebert@DESKTOP-UFIA6QU:~/tutorial-bash$ chmod u+x posargu.sh
hebert@DESKTOP-UFIA6QU:~/tutorial-bash$ ./posargu.sh Herbert Lindemans
Hello Herbert Lindemans 
hebert@DESKTOP-UFIA6QU:~/tutorial-bash$ 

Output/Input redirection 


PIPING 

Command one :~$ echo Hello there 
Pipe symbol :~$ echo Hello there | 
Command Two :~$ echo Hello there | grep there

Send command output to other commands

hebert@DESKTOP-UFIA6QU:~tutorial-bash$ ls -l /usr/bin | grep bash 
-rw-r- - r- - 1 root root 1183448 Apr 18 2022 bash
-rw-r- - r- - 1 root root 6794 Apr 18 2022 bashbug
-rw-r- - r- - 1 root root 2446 Jan 26 2022 dh_bash-completion
-rw-r- - r- - 1 root root 4 Apr 18 2022 rbash -> bash
hebert@DESKTOP-UFIA6QU:~tutorial-bash$

Output redirection 
> Symbol to write to a file
>> To append to a file 

$ echo Hello World! > hello.txt
$ echo Hello World! >> hello.txt

Example use case
Logging to a logfile (for ex. using timestamp)
Dynamically creating (config) files 

hebert@DESKTOP-UFIA6QU:~tutorial-bash$ echo Hello World! > hello.txt
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ cat hello.txt
Hello World! 
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ echo Good day to you! > hello.txt
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ cat hello.txt
Good day to you! 
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ rm hello.txt
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ echo Hello World >> hello.txt 
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ cat hello.txt
Hello World
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ echo Good day to you >> hello.txt
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ cat hello.txt
Hello World 
Good day to you 


hebert@DESKTOP-UFIA6QU:~tutorial-bash$  wc -w hello.txt
6 hello.txt
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ wc - w < hello.txt
6 
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ cat << EOF 
> I will
> write some
> text here
> EOF 
I will
write some
text here
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ wc -w <<< “Hello there wordcounty!” 
3
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ 


Test operators 


hebert@DESKTOP-UFIA6QU:~tutorial-bash$ [ hello = hello ] 
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ echo $? 
0
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ [ 1 = 0 ] 
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ echo $?
1
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ [ 1 -eq 1 ]
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ echo $?
0

If/Elif/Else


hebert@DESKTOP-UFIA6QU:~tutorial-bash$ vim ifelifelse.sh

- - INSERT - -

#!bin/bash 

if [ ${1,,} = herbert ]; then
      echo “Oh, you are the boss here. Welcome!”
elif [ ${1,,} = help ]; then 
      echo “Just enter your username , duh!”
else 
      echo “I do not know who you are. But you are not the boss of me”
fi 

:wq

hebert@DESKTOP-UFIA6QU:~tutorial-bash$ ./ifelifelse.sh herbert
Oh, you are not the boss here. Welcome! 
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ ./ifelifelse.sh help
Just enter your user name, duh! 
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ ./ifelifelse.sh someone
I do not know who you are. But you are not the boss of me!
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ 

Case Statements


hebert@DESKTOP-UFIA6QU:~tutorial-bash$ vim login.sh 

- - INSERT - -

#!/bin/bash
case ${1,,} in 
             herbert | administrator) 
                         echo “Hello, you are the boss here!”
                         ;;
             help)
                         echo “Just enter your username!” 
                         ;;
             *) 
                         echo “Hello there, you are not the boss of me. Enter a valid username!” 
esac 

:wq

hebert@DESKTOP-UFIA6QU:~tutorial-bash$ chmod u+x login.sh 
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ ./login.sh herbert
Hello you are the boss here!
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ ./login.sh help
Just enter your username!
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ ./login.sh test
Hello there. You are not the boss of me. Enter a valid username! 
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ ./login.sh administrator
Hello you are the boss herer!
hebert@DESKTOP-UFIA6QU:~tutorial-bash$ 

Arrays 


hebert@DESKTOP-UFIA6QU:~$ MY_FIRST_LIST= (one two three four five) 
hebert@DESKTOP-UFIA6QU:~$ echo $MY_FIRST_LIST
one 
hebert@DESKTOP-UFIA6QU:~$ echo ${MY_FIRST_LIST[@]} 
one two three four five
hebert@DESKTOP-UFIA6QU:~$ echo ${MY_FIRST_LIST[0]}
one 
hebert@DESKTOP-UFIA6QU:~$ 

For Loop 


hebert@DESKTOP-UFIA6QU:~$ for item in ${[MY_FIRST_LIST[@]}; do echo -n $item | wc -c; done
3
3
5
4
4
hebert@DESKTOP-UFIA6QU:~$ 

Functions 



hebert@DESKTOP-UFIA6QU:~$ vim firstfunction.sh

- - INSERT - -

#!/bin/bash 

showuptime(){
                    up=$(up time -p | cut -c4-)
                    since=$(uptime -s )
                    cat << EOF
—--- 
This machine has been up for ${up}
It has running since ${since} 
—---
EOF
}
showuptime 

:wq


hebert@DESKTOP-UFIA6QU:~$ chmod u+x firstfunction.sh 
hebert@DESKTOP-UFIA6QU:~$ ./firstfunction.sh
—---
This machine has been up for 21 minutes 
It has been running since 2022-12-29 08:37:09
—---
hebert@DESKTOP-UFIA6QU:~$ vim function.sh 
- - INSERT - -

#!/bin/bash 

showuptime(){
                    up=$(up time -p | cut -c4-)
                    since=$(uptime -s )
                    cat << EOF
—--- 
This machine has been up for ${up}
It has running since ${since} 
—---
EOF
}
showuptime 
“firstfunction.sh” 13L 186C 
- - INSERT - -

#!/bin/bash 
up=”before”
since=”function”
echo $up
echo $since
showuptime(){
                    up=$(up time -p | cut -c4-)
                    since=$(uptime -s )
                    cat << EOF
—--- 
This machine has been up for ${up}
It has running since ${since} 
—---
EOF
}
showuptime 
echo $up 
echo $since 

:wq

hebert@DESKTOP-UFIA6QU:~$ ./firsfunction.sh
before
function
—---
This machine has been up for 21 minutes 
It has been running since 2022-12-29 08:37:08
—---
28 minutes
2022-12-29 08:37:08 
hebert@DESKTOP-UFIA6QU:~$ vim firstfunction.sh

- - INSERT - -

#!/bin/bash 

showuptime(){
                    local up=$(up time -p | cut -c4-)
                    local since=$(uptime -s )
                    cat << EOF
—--- 
This machine has been up for ${up}
It has running since ${since} 
—---
EOF
}
showuptime 
“firstfunction.sh” 13L 256C 

:wq

hebert@DESKTOP-UFIA6QU:~$ ./firstfunction.sh 

before
function
—---
This machine has been up for 21 minutes 
It has been running since 2022-12-29 08:37:08
—---
before
function 

hebert@DESKTOP-UFIA6QU:~$ vim functionposargu.sh

- - INSERT - -

#!/bin/bash
showname(){
                  echo hello $1
}
showname Herbert

hebert@DESKTOP-UFIA6QU:~$ chmod u+x functionposargu.sh
hebert@DESKTOP-UFIA6QU:~$ ./functionposargu.sh
hello Herbert
hebert@DESKTOP-UFIA6QU:~$ 

Exit Codes


hebert@DESKTOP-UFIA6QU:~$ functionposargu.sh 

- - INSERT - -

#!/bin/bash
showname(){
                  echo hello $1
                  if [ {$1,,} = herbert ]; then
                            return 0 
                  else 
                            return 1 
                  fi
}
showname $1 
if [ $? = 1 ]; then 
           echo “Someone unknown called the function!”
fi 

:wq

hebert@DESKTOP-UFIA6QU:~$ ./functionposargu.sh test
hello test 
Someone unknown called the function!
hebert@DESKTOP-UFIA6QU:~$ ./functionposargu.sh herbert 
hello herbert
hebert@DESKTOP-UFIA6QU:~$ 

AWK


hebert@DESKTOP-UFIA6QU:~$ echo one two three > testfile.txt
hebert@DESKTOP-UFIA6QU:~$ vim testfile.txt
hebert@DESKTOP-UFIA6QU:~$ awk ‘{ print $1}’ testefile.txt 
one 
hebert@DESKTOP-UFIA6QU:~$ awk ‘{ print $2}’ testefile.txt 
two
hebert@DESKTOP-UFIA6QU:~$ vim csvtest.csv 

- - INSERT - -

one, two, three

: wq

hebert@DESKTOP-UFIA6QU:~$ awk -F, ‘{print $1}’ csvtest.csv 
one 
hebert@DESKTOP-UFIA6QU:~$ echo “Just get this word: Hello” | awk ‘{print $5}’
Hello
hebert@DESKTOP-UFIA6QU:~$ echo “Just get this word: Hello” | awk -F:  ‘{print $2}’ | cut -c2- 
Hello
hebert@DESKTOP-UFIA6QU:~$ 

SED


hebert@DESKTOP-UFIA6QU:~$ vim sedtest.txt
hebert@DESKTOP-UFIA6QU:~$ sed ‘s/fly/grasshopper/g’ sedtest.txt
The grasshopper flies like no grasshopper flies.
hebert@DESKTOP-UFIA6QU:~$ sed -i.ORIGINAL ‘s/fly/grasshopper/g’ sedtest.txt
hebert@DESKTOP-UFIA6QU:~$ vim test.txt ORIGINAL 
The grasshopper flies like no grasshopper flies.
hebert@DESKTOP-UFIA6QU:~$ vim test.txt 
hebert@DESKTOP-UFIA6QU:~$ 
      















