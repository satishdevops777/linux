# linux
Linux
20/07/2025
Finding Files (find & Locate)
	⁃	find location -name "word"
	⁃	locate filename

Wildcards
	⁃	Wildcard is a character that can be used as a substitute for any of a class of characters in a search
	⁃	* zero or more charcs
	⁃	? Single charc
	⁃	[] Range of charc
	⁃	{1..5}

21/07/2025
Linux File types 
	⁃	- regular, 
	⁃	d directory is a folder
	⁃	l linked file that points to other files
	⁃	c speacial or device file is representa hardware devices meaning anything connected to our system lets say keyboard, hw device
	⁃	b block file thses files represents hw devices that handle data in blocks 
	⁃	Hard drives 
	⁃	USB drives
	⁃	s socket file is used for nw comm btw process, allowing daya exchange between them
	⁃	p named pipe file is also know as FIFO, Used for interprocess comm inside pur computer allowed data to process between process (FIFO)

Soft and hard links
	⁃	Inode is pointer or number of a file on the hard disk
	⁃	Soft link link will be removed if file is removed or renamed (ln -s) and different inode number 
	⁃	Hard link - Deleting renaming or moving the original file will not affect the hard link (ln) and same inode number (ls -ltri)
Note: we cannot create soft and hard link within the same directory with the same name.  That is why we will create links in /tmp dir.
	⁃	Hard links works within the same partition

Command Syntax
	⁃	Cmd options arguments

File Permissions
	⁃	Read -r (4)
	⁃	Write -w (2)
	⁃	Execute - x (1)
	⁃	Each permission can be controlled by 3 levels
	⁃	u ; User
	⁃	g ; group
	⁃	o ; others
	⁃	
	⁃	Command : chmod
	⁃	chmod ugo+permissions FILE
	⁃	chmod 777 FILE

Cut command

cut the lines from a soecified file or piped data and print the result to a standard output.

cut filename - does not work we need pass option

cut --version
cut --help/man
cut -c1 filename - list of all the first charcs in that file
cut -c1, 2,4 - pic the charcs
cut -c3-7 filename - range
cut -c1-3, 5-8 filename - display the 1-3 and 5-8 chracs 
cut -b1-3 filename -- list by byte size
cut -d: -f 5 /etc/passwd -- 6th colum it will grab in the file, we can use any deliminater
cut -d: -f 4-6 filename 

Awk command
Utility or language designed for data extraction, most of the time it is used to extract field from a file lr from an output

awk -version -- check version
awk '(print $1)' filename - list first field from a file
ls -l | awk '(print $1, $3)' -- first and third field of the ls -l output

ls -l | awk '(print $NF)' -- Last colum
awk '/ram/  (print)' filename
awk -F: '(print $1)' filename
echo "Hello tom" | awk '($2="Adam"; print $0)' --replace words in file
awk 'length($0) >15' filename -- get the lines that have more than 15 byte size
ls -l | awk '(if($9 =="ram" print $0;)'
ls -l | awk '(print NF) -- Print number of fields in a file

grep/egrep
global regular expression print, print the specified matched pattern lines
