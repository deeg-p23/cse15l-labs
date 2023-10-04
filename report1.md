### cd no args
'''
**[user@sahara ~]$ cd**
[user@sahara ~]$ []
'''
The working directory was /root.
I got this output because the cd command requires some directory or file to _change directory_. Otherwise, it will remain in the same directory.
This output is not necessarily an error, just a response to no arguments.

### cd directory arg
'''
**[user@sahara ~]$ cd lecture1**
[user@sahara ~/lecture1]$ []
'''
The working directory was /root.
This output is due to giving a directory that is accessible from /root. _Change directory_ command's goal is to do so anyway.
This output is not an error.


### cd file arg
'''
**[user@sahara ~/lecture1]$ cd README**
bash: cd: README: Not a directory
'''
The working directory was /root/lecture1.
This output is because cd can only take Directories as valid arguments. This is why it returns a bash error.
This output is an error because you give it a non-directory item as an argument.

### ls no args
'''
**[user@sahara ~/lecture1]$ ls**
Hello.class  Hello.java  messages  README
'''
The working directory was /root/lecture1.
This output acts as the default output when no args are given. It then _lists files_ in the present directory.
This output is not an error.

### ls directory arg
'''
**[user@sahara ~/lecture1]$ ls messages**
en-us.txt  es-mx.txt  tl.txt  zh-cn.txt
'''
The working directory was /root/lecture1.
This output is the _listed files_ of all files inside of the directory messages, which is inside the directory lecture1.
This output is not an error.

### ls file arg
'''
**[user@sahara ~/lecture1]$ ls README**
README
'''
The working directory was /root/lecture1.
This output will read to the user the file title itself, simply because it is the only file listable amongst itself; as it is not a directory.
This output is not necessarily an error, it's reading its own contents as a non-directory item.

### cat no args
'''
**[user@sahara ~/lecture1]$ cat**
[]
'''
The working directory was /root/lecture1.
This output will break the console entirely, requiring a new console. This is because the cat command requires any sort of input in order to continue and not crash.
This output is an error, as it breaks console input entirely.

### cat directory arg
'''
**[user@sahara ~/lecture1]$ cat messages**
cat: messages: Is a directory
'''
The working directory was /root/lecture1.
This reads to you info about messages telling you what kind of item it is, since there are no strings to read or concatenate, it is only a directory.
This output isn't necessarily an error, it's only informing the user what type of item they attempted to concatenate is.

### cat file arg
'''
**[user@sahara ~/lecture1]$ cat README**
To use this program:

javac Hello.java
java Hello messages/en-us.txt
'''
The working directory was /root/lecture1.
This will read to you the entire string contained within the README text file. If there was a second readable file given as an arg, it would concatenate both string contained within both files and print.
This output is not an error, just a single-argument use of the cat command.
