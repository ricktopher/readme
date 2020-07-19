Documentation and tutorial for readme program

* * *

*Program to help maintain large project directories by
automating the creation and deletion of README.txt files. 
<br><br>
Skip below for instruction on how to use*

Use the "Project" folder provided to test the program
out for yourelf.

* * *

# Program functions


## 1. Overview

Sometimes, you come back to a complex directory structure
and you have no heckin idea where you put what and what's
in what directory. 

> *insert "I have no memory of this place" meme*

Here is where readme becomes, hopefully, really powerful.
Use 'readme -d directoryName' and it will show a tree
structure of directoryName along with annotations taken
from the first line of the file. Thus, when you look
at the tree, you will be able to see an overview of the
purpose of each of your directories. 

Ofcourse, at the end of the day, it's up to you to
give a concise yet descriptive one-liner.



## 2. README.txt creation 
   
Empty README.txt files are created inside each directory.
To be annotated by the user later on. 



## 3. README.txt deletion

If you have empty README.txt file that you didn't need to
annotate, then leave it empty. readme will find the 
empty file and delete it. README.txt files with text in
them is left untouched. 

Following a "Creation -> Annotation -> Deletion" 
cycle will hopefully allow even the messiest of file 
directories to be left labelled without having
superfluous README.txt files.


## 4. README.md content collation

When you have a large directory structure with lots of
readme files, you might want to collate all of them
and have a giant file dump to work off of. The program
can help you create such a file, so yous don't have
to hunt all over your directory structure, opening and
closing who knows how many text files along the way.


* * *


#	Tutorial


## 0. (Optional) Make the script executable from anywhere in the system

Create script folder in your home directory (or wherever you want).
Place the readme inside that directory.
Make sure the shebang (first line) of the readme looks like this:
   
   	#!/usr/bin/env python
   
Get the directory path using while inside the directory.

   	username@pop-os:~/script$ pwd

It's gotta point to python in your system, essentially.
Make script executable with the command 
   
   	username@pop-os:~/script$ chmod +x readme 
   
Open up the bashrc file with 
   
   	username@pop-os:~/script$ sudo nano ~/.bashrc
   
Add this line to the end of .bashrc.
   
   	PATH="directory path:$PATH"
   
In the terminal run the command 

   	username@pop-os:~/script$s ource ~/.bashrc

Congratulations, you now can use the readme script from anywhere ni your system! 



## 1. Getting an overview of your directory

Suppose you have directory named 'Project' with the following stucture, 

	username@pop-os:~/Desktop/readme$ ./readme -d Project
	   . Project
	      . text1.txt
	      . text2.txt
	      . subProject1
	         . text1.txt
	      . subProject2

Right now, the directories are not annotated because they have no
README.txt files. Lets create some some README.txt files



## 2. Creating README.txt files

	rick@pop-os:~/Desktop/readme$ ./readme -d Project -c
	Created 3 README files!

Now, if we run readme again:
	
	rick@pop-os:~/Desktop/readme$ ./readme -d Project 
	   . Project  # No info	
	      . text1.txt
	      . text2.txt
	      . subProject1  # No info	
	         . text1.txt
	      . subProject2  # No info	

We have annotations! Empty README.txt files have been created!
However, the README.txt are invisible unless you use the verbose command

Suppose we go change the README.txt file inside 'Project' and write
the text 'Hello World!'
 
Then, if we run the program again we get the following:

	rick@pop-os:~/Desktop/readme$ ./readme -d Project
	   . Project   # Hello World!
	      . text1.txt
	      . text2.txt
	      . subProject1  # No info	
	         . text1.txt
	      . subProject2  # No info	



## 3. Deleting unused README.txt files

Notice the directories with the annotations '# No info'. 
Ideally, all the directories have annotations. Sometimes, 
there is legitimately no need to have an annotation. In such 
cases, the README.txt file will only serve to clutter up our 
directory structur. 

So, we can just use readme to remove empty README.txt if we
wont add anything to them.

	rick@pop-os:~/Desktop/readme$ ./readme -d Project -e
	Deleted 2 empty README files!


Now, if we do an overview of our directory, we shall see
that the empty README.txt files have been removed, leaving
only our annotated README.txt intact.

	rick@pop-os:~/Desktop/readme$ ./readme -d Project -e
	Deleted 2 empty README files!
	
	rick@pop-os:~/Desktop/readme$ ./readme -d Project 
	   . Project   # Hello World!
	      . text1.txt
	      . text2.txt
	      . subProject1
	         . text1.txt
	      . subProject2
	


## 4. README.md content collation

All you have to do is point to the directory where all your
readmes are and the location of the dump file (file can be
any name of your choice), and all the contents of the 
directory and the README.md files will be there.


	rick@pop-os:~/Desktop/readme$ readme -d Project -o ./DUMP.md


----------------------------------------------------------------
# End
----------------------------------------------------------------