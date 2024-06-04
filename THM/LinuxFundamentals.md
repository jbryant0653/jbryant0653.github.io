- <font color="#ff0000">Unix</font> was created  by <font color="#ffc000">Ken Thompson</font> and <font color="#ffc000">Dennis Ritchie</font> in <font color="#ffc000">1970</font> at AT&T Bell Lab.
	- Then <font color="#ff0000">GNU Project</font> was made to make a bunch of <font color="#ffc000">open source software</font> and tools for a UNIX like operating system. So <font color="#ffc000">Richard Stallman</font> made a OS called <font color="#ffc000">GNU (Gnu Not Unix)</font> in <font color="#ffc000">1983</font>.
		- A GNU license was released so that people could create these open source content.
	- <font color="#ff0000">Linux</font> began in <font color="#ffc000">1991</font> by <font color="#ffc000">Linus Torvalds</font> and was combined with the GNU software to add onto the Linux kernel and this created the name <font color="#ffc000">GNU/Linux</font>.
	- Linux is based on Unix and is used as an umbrella term to mean all OS's that are based on Unix.
- Linux is used in things like: Websites, car control panels, checkout tills and registers, traffic light controllers.
# Commands
- Commands use <font color="#ff0000">-char</font> syntax called <font color="#ffc000">flags</font> or <font color="#ffc000">switches</font> to do more detailed tasks.
	- Use <font color="#ff0000">--help</font> flag to learn how to use the command tool.
	- Or use the <font color="#ff0000">MAN</font> aka manual page to see the full documentation.
		- Syntax: man command
- <font color="#ff0000">cd</font>: Change Directory
	- cd . (current directory)
	- cd .. (Previous directory)
- <font color="#ff0000">ls</font>: List
	- ls -a (all)
	- ls -l (long format which lists <font color="#ffc000">permissions</font>.)
		- ls -l fileName (will only do that file)
	- ls Directory (list the files in that directory)
- <font color="#ff0000">cat</font>: Concatenate
	- cat Directory/Path/File.txt (prints out that file)
- <font color="#ff0000">pwd</font>: Print Working Directory
- <font color="#ff0000">echo</font>: Print text
	- echo wowowo (prints the text)
- <font color="#ff0000">whoami</font>: 
- <font color="#ff0000">find</font>: searches for a <font color="#ffc000">file or folder</font>
	- find -name file (or *.txt)
- <font color="#ff0000">grep</font>: Comes from the <font color="#ffc000">ed</font> editor which had a command called <font color="#ffc000">g/re/p </font>which means <font color="#ffc000">Global/Regular Expression/Print</font> which finally became its own utility. This searches within files for a specific pattern.
	- grep "regex pattern" File/Files 
- <font color="#ff0000">wc</font>: Word Count
	- wc -l  File/Files (lines)
	- wc -w File/Files (words)
	- wc -c File/Files (Bytes)
	- wc -m File/Files (characters)
	- wc -L File/Files (longest line)
- <font color="#ff0000">touch</font>: create empty file
	- touch filename
- <font color="#ff0000">mkdir</font>: MaKe DIRectory
	- mkdir DirectoryName
- <font color="#ff0000">cp</font>: CoPy files or folder
	- cp oldFile newFile
- <font color="#ff0000">mv</font>: <font color="#ffc000">MoVe</font> or <font color="#ffc000">merge</font> file or folder
	- mv oldFile NewFile (This is the same as cp)
	- mv oldFile ExistingFile (This will Merge the oldFile to the ExistingFile)
	- mv oldFile Directory/ (The / indicates it as directory and not a new file.)
- <font color="#ff0000">rm</font>: ReMove file or folder
	- rm fileName
	- rm <font color="#ffc000">-R</font> DirectoryName
- <font color="#ff0000">file</font>: Determine file type
	- file fileName
- <font color="#ffc000">wget</font>: Download content from a webstie
	- wget website/file
# Shell Operators \[<font color="#7030a0">NOT DONE</font>\]
- <font color="#ff0000">&</font>
	- Run Command in the <font color="#ffc000">background</font> of your terminal.
> [!example] Copying a large file
> - Use it to copy a large file that might take awhile to continue using the terminal.

- <font color="#ff0000">&&</font> 
	- Combine multiple commands into one line. Order is from left to right.
	- The second command will only run when the first command finishes.
- <font color="#ff0000">\></font> 
	- Takes the output of a command and <font color="#ffc000">redirects</font> it somewhere else.
> [!example] Creating a new file using echo
> echo heyyyyyy > welcome
> - If the file already exists it will <font color="#ffc000">overwrite</font> the content.

- <font color="#ff0000">>></font>
	- Will <font color="#ffc000">append</font> the content to the <font color="#ffc000">bottom</font> of the file instead of overwriting it.
# SSH and Remote Connection
- <font color="#ff0000">SSH</font> means Secure Shell and is a protocol to execute commands on a <font color="#ffc000">remote device</font> that is properly <font color="#ffc000">encrypted</font>.
- A password is usually needed to connect to a remote device.
> [!example] Command structure
> ssh username@ipAddress
- <font color="#ff0000">SCP</font>: Secure Copy Files using <font color="#ffc000">SSH protocol</font> to and from remote computer
	- Makes its own SSH session and so you don't have to be SSH'd into the system already.
	- scp localFile userName@ipAddress:newFile (<font color="#ffc000">Local to Remote</font>)
	- scp userName@ipAddress:remoteFile localFile (<font color="#ffc000">Remote to Local</font>)
		- Use -r for recursively copy a full directory
		- Use -P port to specify port (defualt 22)
		- Use -p to preserve file attributes.
	- <font color="#ffc000">Alternative format</font>: scp localfile site.name.com:newfile
- <font color="#ff0000">Python3 Webserver</font>: start up a <font color="#ffc000">webserver</font> to wget files from a remote machine.
	- python3 -m http.server
		- Default port is <font color="#ffc000">8000</font>
	> [!attention] 
	> - Without configuration this can be <font color="#ffc000">dangerous</font>! There is no authentication.
	- <font color="#ff0000">Secure Alternatives</font>: <font color="#ffc000">Caddy</font>, nginx, apache server.
		- You want to use <font color="#ffc000">HTTPS, SSL/TLS certs, and password protected</font>.
	

# File & Folder Permissions 
- Characteristics of a Item are: What <font color="#ffc000">actions</font> are allowed and <font color="#ffc000">Who</font> can perform the action.
	- File <font color="#ffc000">Ownership</font>
	- File <font color="#ffc000">Permission</font>
- Every file has 3 kinds of owners: User, Group, Other
	- <font color="#ff0000">User</font>: <font color="#ffc000">owner</font> of the file.
	- <font color="#ff0000">Group</font>: Every user is apart of a group and sometimes the group is called the same as your username.
		- Use the command <font color="#ffc000">groups</font> to see what groups you belong to.
	- <font color="#ff0000">Other</font>: A large group of <font color="#ffc000">every single user</font> on the system.
- Every file and directory has 3 permissions for each owner:
	- <font color="#ff0000">Files</font>:
		- Read: <font color="#ffc000">view</font> or <font color="#ffc000">copy</font> file <font color="#ffc000">contents</font>
		- Write: <font color="#ffc000">Modify</font> file content
		- Execute: <font color="#ffc000">run</font> the file <font color="#ffc000">if executable</font>
	- <font color="#ff0000">Directories</font>:
		- Read: <font color="#ffc000">list</font> and <font color="#ffc000">copy names</font> of all files from a directory
		- Write: <font color="#ffc000">Add</font> or <font color="#ffc000">Delete</font> files in a directory
		- Execute: Can <font color="#ffc000">enter</font> the directory

    > [!Attention] Directory RWE Precedence
    > - <font color="#ff0000">Directory Execute</font> must be <font color="#ffc000">On</font> for <font color="#ffc000">Dir Write</font> and all File permissions to work!
    > - If  <font color="#ffc000">Dir Read</font> and <font color="#ffc000">Write</font> are <font color="#ffc000">Off</font>, you can still <font color="#ffc000">Read and Write to file contents</font> if you know the File names!
    > 	- Unless you have the <font color="#ffc000">sticky bit on "t"</font> for the <font color="#ffc000">directory</font>.
- Use the <font color="#ff0000">stat</font> command to get information about a files permissions or filesystem information.
	- stat fileName (about file)
	- stat -f fileName (about filesystem)
- Or use the <font color="#ff0000">ls -l</font> command for information about the files and folders.
	- ![ls -l command format](attachments/ls%20-l%20command%20format.png)
	- <font color="#ff0000">Filetype</font>: 
		- <font color="#ffc000">"-":</font> Regular File
		- <font color="#ffc000">"d":</font> Directory
		- <font color="#ffc000"> "l":</font> Symbolic Link
			- File that points to another File, Directory, non-existent files.
			- Create using: <font color="#ffc000">ln -s targetFile linkName</font>
		- <font color="#ffc000">"c":</font> Character Device File
			- Files that provide <font color="#ffc000">access to char oriented devices</font> such as <font color="#ffc000">keyboards </font>and <font color="#ffc000">mice</font> or <font color="#ffc000">serial ports</font> which sequentially handle information. The files provide programs access to these hardware device.
			- stored in <font color="#ffc000">/dev</font> and are associated with device drivers which are shown as numbers when doing ls -l.
		- <font color="#ffc000">"b":</font> Block Device File
			- Files that provide <font color="#ffc000">access to block oriented devices</font> such as <font color="#ffc000">storage devices</font> and are stored in <font color="#ffc000">/dev</font>.
		- <font color="#ffc000">"p":</font> Named Pipe (FIFO)
			- (First In First Out), This file acts a intermediate area for processes to <font color="#ffc000">inter-communicate</font> between each other. The files are <font color="#ffc000">bidirectional</font> and are read and written to.
			- <font color="#ffc000">unnamed</font> or anonymous pipes are use by the <font color="#ffc000">| symbol</font> and only exist when the processes are alive.
				- The named version has persistent storage in the <font color="#ffc000">/dev</font> folder.
		- <font color="#ffc000">"s":</font> Unix Domain Socket
			- Same as named pipe accept it is typically used for communicated between processes across a network or local but similar processes.
	- <font color="#ff0000">Permissions</font>: The read,write, and execute permission for the user, group, and other.
		- ![Permissions section format](attachments/Permissions%20section%20format.png)
			- <font color="#ffc000">"r"</font>: Read
			- <font color="#ffc000">"w"</font>: Write
			- <font color="#ffc000">"x"</font>: eXecute
				- <font color="#ffc000">"X"</font>: Changes only Directories which can be used for large scale chmoding to not change any files!
			- <font color="#ffc000">"-"</font>: no Permission
			- <font color="#ffc000">"s"</font>: SUID or SGID (Set User or Group ID).
				- This will make it where when others <font color="#ffc000">execute</font> the file it executes it will the <font color="#ffc000">User or Group owners permissions</font>.
				- <font color="#ffc000">"S"</font>: If the <font color="#ffc000">x is not on</font> for <font color="#ffc000">user or group</font> to show you that there is an <font color="#ffc000">error</font>.
			- <font color="#ffc000">"t"</font>: Set sticky bit which makes it so that all files in a given <font color="#ffc000">directory</font> can only be <font color="#ffc000">deleted</font> or <font color="#ffc000">renamed</font> by the file owners or root.
				- <font color="#ffc000">"T"</font>: If the <font color="#ffc000">x is not on</font> for <font color="#ffc000">other</font> to show that there is an <font color="#ffc000">error</font>.
		- <font color="#ff0000">Changing Permissions</font> using <font color="#ffc000">chmod</font> command:
			- Two modes: <font color="#ffc000">Absolute</font> and <font color="#ffc000">Symbolic</font>
			- <font color="#ff0000">Absolute</font>:
				- Each section(user,group,other) is represented using <font color="#ffc000">octal</font> format which is a <font color="#ffc000">7 digit system</font> or <font color="#ffc000">3 bit system</font>.
					- The MSB or <font color="#ffc000">3rd bit</font> is the "<font color="#ffc000">Read</font>" value, <font color="#ffc000">2nd bit</font> is the "<font color="#ffc000">Write</font>", and LSB or <font color="#ffc000">1st bit</font> is "<font color="#ffc000">eXecute</font>". 
					- This means from binary the <font color="#ffc000">"r" value is 4</font> in decimal, <font color="#ffc000">"w" is 2</font>, and <font color="#ffc000">"x" is 1</font>, and <font color="#ffc000">"-" is 0</font>.
				- So in total each section will be a number <font color="#ffc000">0 to 7</font> and make 3 digit number to give to chmod.

        > [!example] chmod absolute mode
        > - chmod <font color="#00b050">3</font><font color="#0070c0">5</font><font color="#7030a0">6</font> fileName
        > 	- <font color="#00b050">User</font>: <font color="#00b050">3</font> = 2+1 so Write and eXecute. Or <font color="#00b050">3 => 011</font> which is <font color="#00b050">-wx</font>
        > 	- <font color="#0070c0">Group</font>: <font color="#0070c0">5</font> = 4+1 so Read and eXecute. Or <font color="#0070c0">5 => 101</font> which is <font color="#0070c0">r-x</font>
        > 	- <font color="#7030a0">Other</font>: <font color="#7030a0">6</font> = 4+2 so Read and Write. Or <font color="#7030a0">6 => 110</font> which is <font color="#7030a0">rw-</font>
        
        > [!important] Special Permissions!
        > - <font color="#ffc000">"s" SUID is 4</font>, <font color="#ffc000">"s" SGID is 2</font>, and <font color="#ffc000">"t" is 1</font>
        > - Use the <font color="#ffc000">optional 4th digit</font> to set these values.
        > - chmod <font color="#ffc000">7</font>356 fileName
        > - <font color="#ffc000">0</font>777 => drw<font color="#ffc000">x</font>rw<font color="#ffc000">x</font>rw<font color="#ffc000">x</font>
        > - <font color="#ffc000">7</font>777 => drw<font color="#ffc000">s</font>rw<font color="#ffc000">s</font>rw<font color="#ffc000">t</font>
        > - <font color="#ffc000">7666</font> => drw<font color="#ffc000">S</font>rw<font color="#ffc000">S</font>rw<font color="#ffc000">T</font>
			- <font color="#ff0000">Symbolic</font>:
				- Pro of symbolic mode is that you can just change one section of permissions at a time instead of being forced to change them all with absolute mode!
				- Section Symbols:
					- <font color="#ffc000">"u"</font>: user owner
					- <font color="#ffc000">"g"</font>: group owner
					- <font color="#ffc000">"o"</font>: Other/everyone
					- <font color="#ffc000">"a"</font>: all of the above
						- If no section symbol is used, <font color="#ffc000">a is the default!</font>
				- Operation Symbols:
					- <font color="#ffc000">"+"</font>: adding permissions
					- <font color="#ffc000">"-"</font>: subtracting permissions
					- <font color="#ffc000">"="</font>: Instead of subtracting or adding, you absolutely set it equal to that permission. (u=r {user=read})
				- Use the <font color="#ffc000">section symbols</font> to pick the owner section, then use <font color="#ffc000">operation symbols</font> to give <font color="#ffc000">permissions</font>.
					- This works for Special Permission too, but they <font color="#ffc000">require the section symbols</font> to work.
				> [!example] chmod symbolic mode
				> - chmod u+rwx,g-rx,o=xt fileName

	- <font color="#ff0000">Hard Link Count</font>: number of hard links with a <font color="#ffc000">default of 1</font>.
	- <font color="#ff0000">User</font>: <font color="#ffc000">Owner</font> of file
	- <font color="#ff0000">Group</font>: Group with <font color="#ffc000">access</font> to file, <font color="#ffc000">Only one group at a time</font>!
		- Use <font color="#ffc000">id -gn userName</font> command to find the <font color="#ffc000">Primary group</font> of a user which will be the group on there by default when a user creates a file.
	- <font color="#ff0000">File Size</font>: size in <font color="#ffc000">bytes</font>
	- <font color="#ff0000">Modification Time</font>: date time of l<font color="#ffc000">ast modified</font>.
	- <font color="#ff0000">Filename</font>: name of file or folder.


# Switching Users and Into Root
- Use the <font color="#ff0000">su</font> command which stands for <font color="#ffc000">switch user</font> and NOT superuser.
- This command is how you can switch to <font color="#ffc000">root</font>.
	- su username (keeps the same shell)
	- su -l username (logs in as the user and uses there shell and env varibles)
	- su (will login you into root by default but without its shell)
	- <font color="#ffc000">su -</font> (will login you into root but with its shell and is the same as using -l or --login)
# Common Directories \[<font color="#7030a0">NOT DONE</font>\]
- <font color="#ff0000">\/etc</font>: etcetera
	- Stores <font color="#ffc000">system files</font> for the operating system.
		- Such as the <font color="#ffc000">shadow file, passwd file, and sudoers file</font>.
- <font color="#ff0000">\/var</font>: variable data
	- Stores <font color="#ffc000">ramdom data</font> for prorams and services.
		- Such as <font color="#ffc000">Logs, temp data, backups</font>, and more.
- <font color="#ff0000">\/home</font>
	- The directory that holds all the <font color="#ffc000">users home folders</font> except for root.
- <font color="#ff0000">\/root</font>
	- This is the <font color="#ffc000">home folder for the root user.</font>
- <font color="#ff0000">\/tmp</font>: Temporary
	- <font color="#ffc000">Volatile</font> storage which means it erases when the computer restarts just like RAM.
> [!Note] Feature
> Any User can <font color="#ffc000">write</font> to the tmp directory by default.
# Processes 
- <font color="#ff0000">Processes</font> are <font color="#ffc000">units of work</font> on linux and <font color="#ffc000">programs</font> have many processes which are managed by the <font color="#ffc000">kernel</font>.
	- They have an ID associated with it called <font color="#ffc000">PID</font> (Process ID) which <font color="#ffc000">increments</font> in the order at which processes start when the PC turns on.
	- You can see processes in the <font color="#ffc000">/proc</font> directory
	> [!note] 
	> -  Processes are different than <font color="#ffc000">Jobs</font>!
	> 	- <font color="#ffc000">Jobs</font> are <font color="#ffc000">not apart of the OS</font> and use many programs executed as a shell command.
	- Linux uses <font color="#ffc000">namespaces</font> to split up processes into sections which have certain access to resources.
	- The first process ran when a computer boots up is normally the <font color="#ffc000">init system</font> such as (<font color="#ffc000">systemd</font>).
		- Other processes ran afterwards are normally <font color="#ffc000">subprocesses</font> of systemd.
- <font color="#ff0000">ps</font>: (Process Status) Display running processes and other Information
	- ps aux (all processes included those outside of the terminal and not owned by you)
	- ps -ux (processes you own and outside your terminal)
	- ps -U username (processes owned by that user)
	- ps -C programName (all processes for a given program)
	- ps -ux | grep regex (use regex to search processes)
		- Or use: <font color="#ff0000">pgrep</font> regex 
- <font color="#ff0000">top</font>: (Table Of Processes) 
	- Use <font color="#ffc000">h</font> key to show key binds.
	- <font color="#ff0000">Alternatives</font>: <font color="#ffc000">btop</font>, <font color="#ffc000">htop</font>
- <font color="#ff0000">uptime</font>: Tells you how long the computer has been on.
- <font color="#ff0000">kill</font>: (Uses <font color="#ffc000">SIGTERM</font> which terminates the program <font color="#ffc000">with cleanup</font> by default)
	- kill PID (find PID uses pgrep and ps)
	- kill -\[SIG\] PID (give a different siginal with the SIG prefix)
		- Signals: <font color="#ffc000">TERM</font>, <font color="#ffc000">KILL</font>(Force w/o cleanup), <font color="#ffc000">STOP</font>
	- kill $(pgrep programName) 
- <font color="#ff0000">pkill</font>: (<font color="#ffc000">kill all</font> processes for a given program)
	- pkill programName
- <font color="#ff0000">xkill</font>: (<font color="#ffc000">Interactive</font> kill to choose which foreground process to kill)
# Services
- <font color="#ff0000">systemctl</font>: (List all services and their statuses)
- Format: sudo systemctl \[option\] serviceName
	- <font color="#ffc000">Options</font>: enable, disable, start, stop,  restart, reload, status
# Cron Jobs
- These are processes that are used to do specific tasks and actions such as running commands, backing up files, running programs, etc at a <font color="#ffc000">specific time</font> that repeat over and over again.
	- <font color="#ff0000">Cron</font> is the <font color="#ffc000">main process</font> that gets called <font color="#ffc000">once a minute</font>.
		- <font color="#ffc000">Cron</font> checks all <font color="#ff0000">crontabs</font> which are files in the <font color="#ffc000">/var/spool/cron</font> directory
			- These files have <font color="#ff0000">cron jobs</font> in them, <font color="#ffc000">one per line</font>.
			- Blank lines and Commented (#) lines don't get read.
- <font color="#ff0000">crontab</font>: (command to edit your crontab file)
	- crontab -e (edit crontab file)
	- crontab -l (print out crontab file)
	- crontab -r (delete crontab file)
	- crontab fileName (make file your crontab file)
	- sudo crontab -u userName (superuser edits other users crontab files)
- <font color="#ff0000">Job Syntax</font>: Min Hour DayOfMonth Month DayOfWeek Command
	- <font color="#ffc000">\*</font> means the we dont care about that option. Aka it could be any of them.
	- <font color="#ffc000">MIN</font>: {0-59} => (#) or (#-#) Range  or (#,#) or (#-#,#-#) or \[(\*/n) or (#-#/n)\] every nth min.
	- <font color="#ffc000">Hour</font>: {0-23} => Same as MIN
	- <font color="#ffc000">DOM</font>: {1-31} => Same as MIN
	- <font color="#ffc000">MONTH</font>: {1-12} => Same as MIN and (jan, feb, mar, ... etc)
	- <font color="#ffc000">DOW</font>: {0(Sun)-6(Sat)} => Same as MIN and (mon, tue, wed, ... etc)
	- <font color="#ffc000">COMMAND</font>: any shell command
		- Use <font color="#ffc000">absolute paths</font> for programs (/usr/bin/cmd) to ensure it works properly
		- You can use <font color="#ffc000">environment variables</font> too!
    > [!Important] Predefined options
    > - Instead of using the complicated syntax, there are a few <font color="#ff0000">predefined options</font>:
    > 	- @option:
    > 		- <font color="#ffc000">yearly, annually, weekly, daily, midnight, hourly, minutely, secondly</font>

# Package Managers

# Installing Software from Source Code




