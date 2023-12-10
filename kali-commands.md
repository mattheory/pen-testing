

# 7z

7z is a file compression format known for its high compression ratio,
using LZMA and LZMA2 compression, while ZIP is a more commonly used
format with wider compatibility but generally offers lower compression
efficiency.

-   **a** compression: stands for 'add' and is used to create an archive

    ``` bash
    7z a <archive-name> <file-name>
    ```

-   **x** decompression: stands for 'extract with full paths'

    ``` bash
    7z x <archive-name>
    ```

# alias

Create temporary alias (session only) for often used complex command. To
make this alias permanent, add it to **.bashrc**.

# apt

The **apt** command is a powerful command-line tool, which works with
Kali's **Advanced Packaging Tool (APT)** performing such functions as
installation of new software packages, upgrade of existing software
packages, updating of the package list index, and even upgrading the
entire Debian system. This command Debian-based systems. An older
version was **apt-get** but now **apt** is preferred.

Best practice:

1.  Update local package database from the software repositories
    specified in **/etc/apt/sources.list**.

    ``` bash
    sudo apt update
    ```

2.  Upgrade installed packages - does not remove or install new
    packages, only updates the existing ones.

    ``` bash
    sudo apt upgrade -y         #adding '-y' pre-approves any prompts
    ```

3.  Upgrade installed packages (BETTER) - not only upgrades the
    installed packages but also intelligently resolves and handles
    dependencies and can remove or install additional packages as needed
    to ensure a smooth upgrade.

    ``` bash
    sudo apt full-upgrade -y        #adding '-y' pre-approves any prompts
    ```

4.  Optional - Remove packages that were installed as dependencies for
    other packages, but are no longer needed because the original
    package has been removed

    ``` bash
    sudo apt autoremove
    ```

5.  Optional - Remove any package files that have been downloaded for
    installation but are no longer needed, freeing up disk space

    ``` bash
    sudo apt clean
    ```

Some examples of popular uses for the apt utility:

-   Install a Package: Installation of packages using the apt tool is
    quite simple. For example, to install the nmap network scanner, type
    the following:

    ``` bash
    sudo apt install nmap
    ```

-   Remove a Package: Removal of a package (or packages) is also
    straightforward. To remove the package installed in the previous
    example, type the following:

    ``` bash
    sudo apt remove nmap
    sudo apt remove nmap --purge #remove pkg config files as well (use with caution)
    ```

# base64

The **base64** command in Linux is used to encode and decode binary data
into text format using Base64 encoding. Base64 encoding is commonly used
to represent binary data, such as files or binary streams, in a text
format that can be easily transmitted or stored in a way that is safe
for use in various contexts, including email, data transfer, and
configuration files.

## Encoding

To encode binary data into Base64 format, use the **base64** command
followed by the name of the file you want to encode.

``` bash
base64 myfile.bin > encoded.txt
```

This command takes the binary data from myfile.bin and outputs the
Base64-encoded version to encoded.txt.

## Decoding

To decode Base64-encoded data back into its original binary form, you
can use the -d option with the base64 command, followed by the name of
the file containing the Base64-encoded data.

``` bash
base64 -d encoded.txt > decoded.bin
```

This command takes the Base64-encoded data from encoded.txt and decodes
it, then saves the original binary data to decoded.bin.

To just get the decoded value, for example decoding a base64 Windows
password, create password.txt with **nano** and paste the base64 encoded
password in it.

``` bash
base64 -d password.txt  
Admin@123 
```

## Additional Options

The base64 command may have additional options depending on your Linux
distribution and version. Common options include -i to specify an input
file and -o to specify an output file.

# bash

Switch from current version of *shell* to *bash*. If running zsh, type
**bash** to switch to *bash*. To find out which *shell* is currently
running:

``` bash
which $SHELL
/bin/bash
```

# cal

Display calendar of the month

# cat

**cat** (short for concatenate) is one of the most frequently used
commands in Linux. It is used to list the contents of a file on the
standard output (sdout). To run this command, type **cat** followed by
the file's name and its extension. For instance: **cat file.txt**.
Prefer \[[41](#less){reference-type="ref" reference="less"}\] to
**cat**.

-   **cat $>$ filename** creates a new file

-   **cat filename1 filename2$>$filename3** joins two files (1 and 2)
    and stores the output of them in a new file (3)

-   **cat filename $|$ tr a-z A-Z $>$output.txt** to convert a file to
    upper or lower case use

After using **whoami**, to find further information of a Linux machine:

``` bash
cat /etc/*issue
Kali GNU/Linux Rolling \n \l

cat /etc/*release
PRETTY_NAME="Kali GNU/Linux Rolling"
NAME="Kali GNU/Linux"
ID=kali
VERSION="2020.1"
VERSION_ID="2020.1"
VERSION_CODENAME="kali-rolling"
ID_LIKE=debian
ANSI_COLOR="1;31"
HOME_URL="https://www.kali.org/"
SUPPORT_URL="https://forums.kali.org/"
BUG_REPORT_URL="https://bugs.kali.org/"
```

# cd

To navigate through the Linux files and directories, use the **cd**
command. It requires either the full path or the name of the directory,
depending on the current working directory that you're in. This command
takes both absolute and relative paths and is case sensitive.

-   **cd ..** to move one directory up

-   **cd** or **cd$\sim$** (tilde) to go straight to the home folder

-   **cd -** (hyphen) to move to your previous directory

-   **cd /** to move to the root of the current OS

# chmod

**chmod** is used to change the read, write, and execute permissions of
files and directories. Example:

``` bash
matt@kali:/usr/bin$ ls m* -al
lrwxrwxrwx 1 root root        22 Dec 20  2021 mail -> /etc/alternatives/mail
-rwxr-xr-x 1 root root     26760 May  9  2019 mapscrn
-rw-r--r-- 1 root root       298 Nov 17 20:47 matt-rename
drwxr-xr-x 2 root root      4096 Aug  5  2020 media
```

For \"**mapscrn**\" file above, \"**-rwxr-xr-x 1 root root**\":

-   **-** 1st character \"-\" for file, \"d\" for \"directory\", \"l\"
    for link

-   **r** user read

-   **w** user write

-   **x** user execute

-   **r** group read

-   **-** group write

-   **x** group execute

-   **r** others read

-   **-** others write

-   **x** others execute

-   **root** user

-   **root** group

To change directory permissions in Linux, use the following:

-   **chmod +rwx** filename to add permissions

-   **chmod -rwx** directory name to remove permissions

-   **chmod +x** filename to allow executable permissions

``` bash
chmod -wx filename #to take out write and executable permissions
```

Note 1: "r" is for read, "w" is for write, and "x" is for execute\
Note 2: "u" for users, "g" for group, "o" for others, and "ugo" or "a"
(for all)

# cmatrix

Transform your terminal into a matrix visual with **cmatrix**. 'q' to
quit.

``` bash
sudo apt install cmatrix
cmatrix
```

# chage

The **chage** command is used to modify and display user password expiry
information in Linux systems. When used with the -l option followed by a
username, it displays the current password expiry details for that user.
Let's take a look at an example:

``` bash
chage -l matt 
Last password change                                    : Jun 30, 2023
Password expires                                        : never
Password inactive                                       : never
Account expires                                         : never
Minimum number of days between password change          : 0
Maximum number of days between password change          : 99999
Number of days of warning before password expires       : 7
```

# chown

In Linux, all files are owned by a specific user. The **chown** command
enables you to change or transfer the ownership of a file to the
specified username. For instance, **chown linuxuser2 file.ext** will
make **linuxuser2** as the owner of the **file.ext**.

# cp

Use the **cp** command to copy files from the current directory to a
different directory. For instance, the command **cp scenery.jpg
/home/username/Pictures** would create a copy of **scenery.jpg** (from
your current directory) into the **Pictures** directory.

# curl

Note: add **-O** to save file when downloading.

::: {#tab:curl}
  **Method**   **Command**
  ------------ -------------------------------------------------------------------------
  GET          curl http://example.com/resource
  POST         curl -X POST -d \"key1=value1&key2=value2\" http://example.com/resource
  PUT          curl -X PUT -d \"data to put\" http://example.com/resource
  DELETE       curl -X DELETE http://example.com/resource/id
  HEAD         curl -I http://example.com/resource
  OPTIONS      curl -X OPTIONS http://example.com/resource
  PATCH        curl -X PATCH -d \"data to update\" http://example.com/resource/id

  : curl commands
:::

Note: The -X option is used to specify a custom method, but in many
cases, curl will automatically adjust the method based on other options
provided (e.g., -d implies POST unless -X is used to override it).
However, it's a good habit to explicitly set the method using -X when
you intend to use anything other than GET, as it makes your intentions
clear and your command self-explanatory.

Remember to use the -H option if you need to set custom headers. For
instance, when sending JSON data with a POST request:

``` bash
curl -X POST -H "Content-Type: application/json" -d '{"key1":"value1", "key2":"value2"}' http://example.com/resource
```

Check your IP address:

``` bash
curl ipinfo.io
{
  "ip": "52.76.221.243",
  "hostname": "ec2-52-76-221-243.ap-southeast-1.compute.amazonaws.com",
  "city": "Singapore",
  "region": "Singapore",
  "country": "SG",
  "loc": "1.2903,103.8591",
  "org": "AS16509 Amazon.com, Inc.",
  "postal": "039801",
  "timezone": "Asia/Singapore",
  "readme": "https://ipinfo.io/missingauth"
```

# df

Use **df** command to get a report on the system's disk space usage,
shown in percentage and KBs. If you want to see the report in megabytes,
type **df -m**.

``` bash
df -k           *** common one used by Faye @ ACG ***
```

# diff

Short for difference, the **diff** is used to compare the contents of
two files line by line. It outputs the differences between them. This
command is particularly useful for determining changes between versions
of the same file or checking the differences between two similar files.

The simplest form of this command is **diff file1.ext file2.ext**

For side-by-side comparison: **diff -y file1.txt file2.txt**

# dig

**dig** command stands for Domain Information Groper. It is used for
retrieving information about DNS name servers. It is basically used by
network administrators. It is used for verifying and troubleshooting DNS
problems and to perform DNS lookups. Dig command replaces older tools
such as nslookup and the host.

``` bash
dig google.com
```

``` bash
dig google.com ANY
```

  **DNS record**   **Definition**
  ---------------- ------------------------------------
  SOA              Start of Authority
  NS               Authoritative name servers
  A                IPv4 address of the domain
  AAAA             IPv6 address of the domain
  CNAME            Canonical name of an alias
  MX               Mail exchange servers
  TXT              Text records, including SPF record

-   Check if SPF value is set in line with available MX:

    ``` bash
    dig cybernode.au txt
    ...
    ;; ANSWER SECTION:
    cybernode.au.           0       IN      TXT     "v=spf1 include:spf.protection.outlook.com -all"
    ```

-   Check if DKIM values are set correctly:

    ``` bash
    dig selector1._domainkey.cybernode.au cname
    ;; ANSWER SECTION:
    selector1._domainkey.cybernode.au. 0 IN CNAME   selector1-cybernode-au._domainkey.cybernodes.onmicrosoft.com.
    ```

-   ``` bash
    dig selector2._domainkey.cybernode.au cname
    ;; ANSWER SECTION:
    selector2._domainkey.cybernode.au. 0 IN CNAME   selector2-cybernode-au._domainkey.cybernodes.onmicrosoft.com.
    ```

-   Check if DMARC config is set correctly:

    ``` bash
    dig _dmarc.cybernode.au txt
    ...
    ;; ANSWER SECTION:
    _dmarc.cybernode.au.    0       IN      TXT     "v=DMARC1; p=quarantine; rua=mailto:report@cybernode.au; ruf=mailto:report@cybernode.au; fo=1; pct=100"
    ```

# du

If you want to check how much space a file or a directory takes, the
**du** (Disk Usage) command is the answer. However, the disk usage
summary will show disk block numbers instead of the usual size format.
If you want to see it in bytes, kilobytes, and megabytes, add the -h
argument to the command line.

# echo

This command is used to move some data into a file. For example, if you
want to add the text, **"Hello, my name is John"** into a file called
**name.txt**, you would type **echo Hello, my name is John
\>\>name.txt**

Important use for **echo**:

``` bash
echo $SHELL
/bin/bash
echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/usr/lib/wsl/lib:/snap/bin
```

Redirection operator

-   $>$ overwrite redirection operator

-   $>>$ append redirection operator

``` bash
echo public > community
echo private >> community
echo manager >> community
cat community     
public
private
manager
```

# exiftool

Show all EXIF information associated with [compatible
files](https://exiftool.org/#supported). Example with [AWS
Well-Architected
Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html):

``` bash
exiftool -a -u wellarchitected-reliability-pillar.pdf        
ExifTool Version Number         : 12.67
File Name                       : wellarchitected-reliability-pillar.pdf
Directory                       : .
File Size                       : 6.8 MB
...
File Permissions                : -rw-r--r--
File Type                       : PDF
File Type Extension             : pdf
MIME Type                       : application/pdf
PDF Version                     : 1.4
Linearized                      : No
Page Count                      : 188
...
Primary Platform                : Apple Computer Inc.
CMM Flags                       : Not Embedded, Independent
Device Manufacturer             : Little CMS
...
Creator Tool                    : ZonBook XSL Stylesheets with Apache FOP
Metadata Date                   : 2023:10:23 04:20:55Z
Create Date                     : 2023:10:23 04:20:55Z
PDF Version                     : 1.5
Page Mode                       : UseOutlines
Title                           : Reliability Pillar - AWS Well-Architected Framework
Author                          : Amazon Web Services
Creator                         : ZonBook XSL Stylesheets with Apache FOP
Producer                        : Apache FOP Version 2.6
Create Date                     : 2023:10:23 04:20:55Z
```

Arguments:

-   **-a** OR **--duplicates** - allows ExifTool to display all
    duplicate metadata tags. Some tags may be stored in multiple
    locations within a file, and by default, ExifTool will only show the
    first instance of a tag.

-   **-u** OR **--unknown** - extract information from unknown or
    unrecognized tags. By default, ExifTool will only display known
    tags. When -u is used, it will also try to extract and display data
    from tags it doesn't recognize.

-   -gpslatitude AND -gpslongitude - extract the GPS latitude and
    longitude.

# fallocate

Create big files ($>$ 100 MB) on a Linux system. Use K for kilobytes and
M for megabytes

-c removes a byte range from a file, without leaving a hole -d detect
and dig holes -i insert a hole of length bytes from offset, shifting
existing data -l specifies the length of the range, in bytes. -n do not
modify the apparent length of the file. This may effectively allocate
blocks past EOF, which can be removed with a truncate -o specifies the
beginning offset of the range, in bytes -p de-allocates space (i.e.,
creates a hole) in the byte range starting at offset and continuing for
length bytes -v verbose mode.

``` bash
fallocate -l 5M test.txt
ls -al
total 5120
drwxrwxr-x 2 ec2-user ec2-user      22 Nov 15 12:30 .
drwx------ 4 ec2-user ec2-user     111 Nov 15 12:15 ..
-rw-rw-r-- 1 ec2-user ec2-user 5242880 Nov 15 12:30 test.txt
du -sh test.txt
5.0M    test.txt
```

# fg

If you typed CTRL+Z inadvertently, **fg** + \[job number\] for
\"foreground\" will bring your job back on top.

``` bash
nano xattr.conf
Use "fg" to return to nano.
[1]+  Stopped                 nano xattr.conf
jobs
[1]+  Stopped                 nano xattr.conf
fg 1
nano xattr.conf
```

# file

Describes the file type and language / encoding:

``` bash
file Yubikey.txt
Yubikey.txt: ASCII text
```

# find

Similar to the locate command, using find also searches for files and
directories. The difference is, you use the find command to locate files
within a given directory.

As an example, **find /home/ -name notes.txt** command will search for a
file called **notes.txt** within the home directory and its
sub-directories.

-   To find files in the current directory use, **find . -name
    notes.txt**

-   To look for directories use, **/ -type d -name notes. txt**

# for

Execute loops using **for** command:

``` bash
for file in *.txt; do mv "$file" "${file%.txt}.text"; done
```

Alternatively, use a **for** loop with string command **sed**
\[[73](#sed){reference-type="ref" reference="sed"}\]. Note that
**rename** \[[\[remane\]](#remane){reference-type="ref"
reference="remane"}\] is preferred for renaming series.

``` bash
for f in *.jpg; do mv "$f" "$(echo "$f" | sed s/IMG/VACATION/)"; done
```

In example above, all jpg files are assumed to contain 'IMG' which will
be replaced by 'VACATION':

``` bash
IMG\_02.jpg; IMG\_0032.jpg; IMG\_0009.jpg
```

Replaced by:

``` bash
VACATION\_02.jpg; VACATION\_0032.jpg; VACATION\_0009.jpg
```

# geoiplookup

Find IP geolocation based on preloaded free 2016 database from
[Maxmind](#https://www.maxmind.com/en/geoip2-country-database).

``` bash
geoiplookup 58.135.76.101
GeoIP Country Edition: CN, China
```

To find IP address associated with domain, use command **nslookup**
\[[\[nslookup\]](#nslookup){reference-type="ref"
reference="nslookup"}\].

Install in Kali / Debian using the following:

``` bash
apt install geoip-bin geoip-database
```

# grep

**grep** lets you search through all the text in a given file. To
illustrate, **grep blue notepad.txt** will search for the word **blue**
in the notepad **file**. Lines that contain the searched word will be
displayed fully.

# gzip

Gunzip or gzip is one the many compression packages part of Linux.
Replace \"file.gz\" below with file to decompress.

``` bash
gzip -d file.gz
```

# head

The **head** command is used to view the first lines of any text file.
By default, it will show the first ten lines, but you can change this
number to your liking. For example, if you only want to show the first
five lines, type **head -n 5 filename.ext**.

# history

**history** command to review the commands you've entered before.

1.  Clear the current session's command history, but won't affect your
    overall history file (usually stored in  /.bash_history)

    ``` bash
    history -c
    ```

2.  Clear the entire history file

    ``` bash
    rm ~/.bash_history
    ```

3.  Delete specific entries from your command history (e.g., line 42)

    ``` bash
    history -d 42
    ```

# hosts

``` bash
host yopaz.com   
yopaz.com has address 18.179.237.153
yopaz.com mail is handled by 10 alt3.aspmx.l.google.com.
yopaz.com mail is handled by 10 alt4.aspmx.l.google.com.
yopaz.com mail is handled by 1 aspmx.l.google.com.
yopaz.com mail is handled by 5 alt1.aspmx.l.google.com.
yopaz.com mail is handled by 5 alt2.aspmx.l.google.com.
```

# htop

Nicer version of **top** command. Not available on all distros.

# hostname

If you want to know the name of your host/network simply type
**hostname**. Adding a -i to the end will display the IP address of your
network.

# id

Print real and effective user and group IDs.

``` bash
id
uid=1000(kali) gid=1001(kali) groups=1001(kali),4(adm),20(dialout),24(cdrom),25(floppy),27(sudo),29(audio),30(dip),44(video),46(plugdev),106(netdev),119(kismet),1000(lxd)
```

# ifconfig

Check network interfaces.

``` bash
ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
    inet 10.1.1.39  netmask 255.255.255.0  broadcast 10.82.1.255
    inet6 fe80::4a21:bff:fe3c:14a2  prefixlen 64  scopeid 0x20<link>
    inet6 fd93:be50:b526:4234:4a21:bff:fe3c:14a2  prefixlen 64  scopeid 0x0<global>
    inet6 fd93:be50:b526:4234:828c:3a67:94da:8386  prefixlen 64  scopeid 0x0<global>
    ether 48:21:0b:3c:14:a2  txqueuelen 1000  (Ethernet)
    RX packets 654618  bytes 704582079 (671.9 MiB)
    RX errors 0  dropped 192  overruns 2  frame 0
    TX packets 215772  bytes 44608367 (42.5 MiB)
    TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
    device memory 0x84200000-842fffff  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
    inet 127.0.0.1  netmask 255.0.0.0
    inet6 ::1  prefixlen 128  scopeid 0x10<host>
    loop  txqueuelen 1000  (Local Loopback)
    RX packets 64  bytes 3640 (3.5 KiB)
    RX errors 0  dropped 0  overruns 0  frame 0
    TX packets 64  bytes 3640 (3.5 KiB)
    TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlan0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
    ether 72:33:89:0b:45:f6  txqueuelen 1000  (Ethernet)
    RX packets 0  bytes 0 (0.0 B)
    RX errors 0  dropped 0  overruns 0  frame 0
    TX packets 0  bytes 0 (0.0 B)
    TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

# jobs

**jobs** command will display all current jobs along with their
statuses. A job is basically a process that is started by the shell.

If you typed $CTRL+Z$ inadvertently, **fg** + \[job number\] for
\"foreground\" will bring your job back on top.

``` bash
ping -c 1000 google.com &
[2] 361
PING google.com (3.24.70.179) 56(84) bytes of data.
sleep 60 &
[3] 362
jobs
[1]+  Stopped                 sleep 60
[2]   Running                 ping -c 1000 google.com &
[3]-  Running                 sleep 60 &
ps
  PID TTY          TIME CMD
   11 pts/0    00:00:00 bash
  355 pts/0    00:00:00 sleep
  361 pts/0    00:00:00 ping
  364 pts/0    00:00:00 ps
kill -9 355
ps
  PID TTY          TIME CMD
   11 pts/0    00:00:00 bash
  361 pts/0    00:00:00 ping
  365 pts/0    00:00:00 ps
[1]+  Killed                  sleep 60
kill -9 361
ps
  PID TTY          TIME CMD
   11 pts/0    00:00:00 bash
  367 pts/0    00:00:00 ps
[2]+  Killed                  ping -c 1000 google.com
ps -ef
*** common one used by Faye @ ACG ***
```

Note: to put a job in the background straight away upon start, add an
**&** at the end of the command. Otherwise that process will stay in the
foreground. Also use **bg** + PID to send to background, or **fg** + PID
to bring back to foreground.

``` bash
ping -c 1000 google.com &
```

# kill

Terminate unresponsive programs manually by using the kill command.
There is a total of sixty-four different signals, which may be sent to
the misbehaving app and instruct the app to terminate itself. List all
**kill** signals with **kill -l**. Most common is **kill -9 processnb**.

``` bash
kill -l
 1) SIGHUP       2) SIGINT       3) SIGQUIT      4) SIGILL       5) SIGTRAP
 6) SIGABRT      7) SIGBUS       8) SIGFPE       9) SIGKILL     10) SIGUSR1
11) SIGSEGV     12) SIGUSR2     13) SIGPIPE     14) SIGALRM     15) SIGTERM
16) SIGSTKFLT   17) SIGCHLD     18) SIGCONT     19) SIGSTOP     20) SIGTSTP
21) SIGTTIN     22) SIGTTOU     23) SIGURG      24) SIGXCPU     25) SIGXFSZ
26) SIGVTALRM   27) SIGPROF     28) SIGWINCH    29) SIGIO       30) SIGPWR
31) SIGSYS      34) SIGRTMIN    35) SIGRTMIN+1  36) SIGRTMIN+2  37) SIGRTMIN+3
38) SIGRTMIN+4  39) SIGRTMIN+5  40) SIGRTMIN+6  41) SIGRTMIN+7  42) SIGRTMIN+8
43) SIGRTMIN+9  44) SIGRTMIN+10 45) SIGRTMIN+11 46) SIGRTMIN+12 47) SIGRTMIN+13
48) SIGRTMIN+14 49) SIGRTMIN+15 50) SIGRTMAX-14 51) SIGRTMAX-13 52) SIGRTMAX-12
53) SIGRTMAX-11 54) SIGRTMAX-10 55) SIGRTMAX-9  56) SIGRTMAX-8  57) SIGRTMAX-7
58) SIGRTMAX-6  59) SIGRTMAX-5  60) SIGRTMAX-4  61) SIGRTMAX-3  62) SIGRTMAX-2
63) SIGRTMAX-1  64) SIGRTMAX
```

-   **SIGINT (2)** - Equivalent to typing $CTRL+C$ while a process is
    running, which interrupts it. []{#SIGINT (2) label="SIGINT (2)"}

-   **SIGKILL (9)** --- Forces programs to stop immediately. Unsaved
    progress will be lost.

-   **SIGTERM (15)** --- (default if no kill signal specified) requests
    a program to stop running and gives it some time to save all of its
    progress. If you don't specify the signal when entering the kill
    command, this signal will be used.

-   **SIGSTOP (19)** - Equivalent to typing $CTRL+Z$ while a process is
    running, which pauses it. Typing $CTRL+Z$ again lets the process
    carry on again using **SIGCONT (18)**. []{#SIGSTOP (19)
    label="SIGSTOP (19)"}

Besides knowing the signals, you also need to know the process
identification number (PID) of the program you want to kill. If you
don't know the PID, simply run the command **ps ux** or use the **top**
command.

After knowing what signal you want to use and the PID of the program,
enter the following syntax: **kill \[signal option\] PID**.

To kill groups of processes, such as a group of ping commands running in
the background, use command **pkill**:

``` bash
ping -c 1000 google.com &
ping -c 1000 google.com.au &
jobs
[1]-  Running                 ping -c 1000 google.com &
[2]+  Running                 ping -c 1000 google.com.au &
pkill ping
[1]-  Terminated              ping -c 1000 google.com
[2]+  Terminated              ping -c 1000 google.com.au
```

Most common use case:

``` bash
jobs
[1]  - suspended  ping 192.168.1.1
[2]  + suspended  ping 10.82.1.1

kill -9 202115                                                                                                 
[1]  - killed     ping 192.168.1.1

kill -9 202280                                                                                                        
[2]  + killed     ping 10.82.1.1
```

# la

Alias for **ls -al**.

# last

Show a listing of last logged in users.

``` bash
Last
kali     pts/0        120.149.86.230   Sun Sep 17 10:50   still logged in
kali     pts/0        120.149.86.230   Sat Sep 16 13:08 - 13:28  (00:20)
kali     pts/0        120.149.86.230   Sat Sep 16 13:03 - 13:07  (00:04)
kali     pts/0        120.149.86.230   Sat Sep 16 12:49 - 13:03  (00:13)
kali     pts/0        120.149.86.230   Sat Sep 16 09:01 - 12:49  (03:47)
kali     pts/0        120.149.86.230   Fri Sep 15 11:59 - 13:59  (02:00)
root     tty1                          Thu Sep 14 14:12   still logged in
root     ttyS0                         Thu Sep 14 14:12   still logged in
reboot   system boot  6.4.0-kali3-clou Thu Sep 14 14:12   still running
kali     pts/3        120.149.86.230   Thu Sep 14 13:37 - 14:11  (00:33)
kali     pts/0        120.149.86.230   Thu Sep 14 13:17 - 14:07  (00:50)
root     ttyS0                         Thu Sep 14 13:15 - down   (00:55)
root     tty1                          Thu Sep 14 13:15 - down   (00:55)
reboot   system boot  6.3.0-kali1-clou Thu Sep 14 13:15 - 14:11  (00:56)

wtmp begins Thu Sep 14 13:15:11 2023
```

# lastlog

Reports the most recent login of all users or of a given user.

``` bash
lastlog
Username         Port     From                                       Latest
root             tty1                                               Thu Sep 14 14:12:46 +0000 2023
daemon                                                              **Never logged in**
bin                                                                 **Never logged in**
sys                                                                 **Never logged in**
sync                                                                **Never logged in**
games                                                               **Never logged in**
man                                                                 **Never logged in**
lp                                                                  **Never logged in**
mail                                                                **Never logged in**
news                                                                **Never logged in**
uucp                                                                **Never logged in**
proxy                                                               **Never logged in**
www-data                                                            **Never logged in**
backup                                                              **Never logged in**
list                                                                **Never logged in**
irc                                                                 **Never logged in**
_apt                                                                **Never logged in**
nobody                                                              **Never logged in**
systemd-network                                                     **Never logged in**
messagebus                                                          **Never logged in**
tcpdump                                                             **Never logged in**
sshd                                                                **Never logged in**
polkitd                                                             **Never logged in**
_chrony                                                             **Never logged in**
kali             pts/0    120.149.86.230                            Sun Sep 17 10:50:13 +0000 2023
mysql                                                               **Never logged in**
stunnel4                                                            **Never logged in**
_rpc                                                                **Never logged in**
sslh                                                                **Never logged in**
ntpsec                                                              **Never logged in**
redsocks                                                            **Never logged in**
iodine                                                              **Never logged in**
miredo                                                              **Never logged in**
statd                                                               **Never logged in**
postgres                                                            **Never logged in**
Debian-snmp                                                         **Never logged in**
inetsim                                                             **Never logged in**
```

# less

Prefer **less** to **cat** \[[7](#cat){reference-type="ref"
reference="cat"}\] as **less** will let you scroll through content as
oppose to list the whole file and may affect your system performance if
the file is large.

The **less** command is a Linux utility that allows you to view and
navigate through the contents of a file. It is similar to the \"more\"
command, but with more advanced features.

When you run the **less** command, it displays the contents of the
specified file on the screen. You can then navigate through the file
using various commands. Some of the most commonly used commands include:

-   spacebar: scrolls down one screen

-   enter: scrolls down one line

-   b: scrolls up one screen

-   j: scrolls down one line

-   k: scrolls up one line

-   /pattern: search for a specific pattern in the file

-   q: quits the **less** command

The **less** command is particularly useful for viewing large files, as
it allows you to quickly navigate through the file without having to
load the entire file into memory. It is also commonly used in
conjunction with other Linux commands, such as **grep**
\[[27](#grep){reference-type="ref" reference="grep"}\] and **find**
\[[24](#find){reference-type="ref" reference="find"}\], to search for
specific information within a file or directory.

``` bash
less /etc/passwd
```

# locate

To locate a file, just like the search command in Windows. Use the -i
argument for case-insensitive search, and asterisk (\*) for unknowns.
For example, **locate -i school\*note** command will search for any file
that contains the word "school" and "note", whether it is uppercase or
lowercase. Refresh the database using **updatedb** command.

``` bash
locate cybernode
/home/kali/cybernode-au-scan-txt
```

In contrast, **which** specifically helps you identify the full path of
executable commands within your PATH environment.

# ll

Alias for **ls -l**.

# ls

The **ls** command is used to view the contents of a directory. By
default, this command will display the contents of your current working
directory.

If you want to see the content of other directories, type ls and then
the directory's path. For example, enter **ls /home/username/Documents**
to view the content of Documents.

-   **ls -R** will list all the files in the sub-directories as well

-   **ls -a** will show the hidden files

-   **ls -al** will list the files and directories with detailed
    information like the permissions, size, owner, etc.

``` bash
ls -al
total 44
drwxr-xr-x 7 matt matt 4096 Sep 13 12:34 .
drwxr-xr-x 3 root   root   4096 Sep 13 11:23 ..
lrwxrwxrwx 1 matt matt   32 Sep 13 11:53 .aws -> /mnt/c/Users/matt/.aws
lrwxrwxrwx 1 matt matt   34 Sep 13 11:53 .azure -> /mnt/c/Users/matt/.azure
-rw------- 1 matt matt  119 Sep 13 11:51 .bash_history
-rw-r--r-- 1 matt matt  220 Sep 13 11:23 .bash_logout
-rw-r--r-- 1 matt matt 3771 Sep 13 11:23 .bashrc
drwx------ 3 matt matt 4096 Sep 13 11:23 .config
drwxr-xr-x 4 matt matt 4096 Sep 13 11:53 .docker
drwxr-xr-x 2 matt matt 4096 Sep 13 11:23 .landscape
-rw-r--r-- 1 matt matt    0 Sep 13 11:23 .motd_shown
-rw-r--r-- 1 matt matt  807 Sep 13 11:23 .profile
drwxr-xr-x 2 matt matt 4096 Sep 13 12:34 daniel
drwxr-xr-x 2 matt matt 4096 Sep 13 11:24 matt
```

Count number of files in folder:

``` bash
ls -1 | wc -l
4610
```

# lsattr

Lists the file attributes on a second extended file system. It's used to
display the attributes set on files or directories, such as whether they
are immutable or append-only.

# lsblk

Lists information about all available or the specified block devices. It
includes details such as device name, size, partition type, mount point,
etc.

# lsb_release

Provides certain LSB (Linux Standard Base) and distribution-specific
information. This command is useful for finding out the version of the
Linux distribution you are running.

# lscpu

Information about the CPU architecture, including the number of CPUs,
threads, cores, sockets, and more. It's useful for getting a detailed
view of the CPU layout of the system.

# lshw

Detailed information about all the hardware on the system, including
memory, disk drives, network adapters, etc. It can also output the
information in various formats, such as HTML or XML.

# lsinitrd

Lists the contents of an initrd image. The initrd (initial ramdisk) is a
scheme for loading a temporary root file system into memory to aid in
the booting process of the Linux kernel.

# lsipc

Shows information on the System V inter-process communication facilities
for which the calling process has read access.

# lslogins

Information about users on the system, such as login names, user IDs,
group IDs, home directories, and the number of logged-in sessions. It's
helpful for system administrators to manage user accounts.

# lsmod

Reads **/proc/modules** and displays the contents in a nicely formatted
list to show all the kernel modules currently loaded into the system.
Kernel modules are pieces of code that can be added to or removed from
the kernel dynamically, providing additional functionality to the system
when needed.

# lsns

Lists information about the currently existing namespaces. Namespaces
are a feature of the Linux kernel that partitions kernel resources so
that one set of processes sees one set of resources while another set of
processes sees a different set of resources, providing a form of
lightweight virtualization.

# lsof

Short for \"list open files,\" this utility shows information about
files opened by processes information about the process that has opened
the file, such as the process ID (PID), user ID (UID), file descriptor
(FD), and type of access (read, write, etc.). An \"open file\" may be:

-   regular file

-   directory

-   network socket

-   pipe

List open connection:

``` bash
lsof -i -P
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
brave   2250 matt   28u  IPv4 195286      0t0  TCP 10.81.1.39:48422->ec2-52-36-145-123.us-west-2.compute.amazonaws.com:443 (ESTABLISHED)
```

# lsusb

Lists USB devices connected to your system. It provides details about
the bus number, device number, device ID, etc., which can be useful for
troubleshooting USB devices or for scripting.

# nmap

## nmap target selection

Scan a single IP

``` bash
nmap 192.168.1.1
```

Scan a host

``` bash
nmap www.testhostname.com
```

Scan a range of IPs

``` bash
nmap 192.168.1.1-20
```

Scan a subnet

``` bash
nmap 192.168.1.0/24
```

Scan targets from a text file

``` bash
nmap -iL list-of-ips.txt
```

Add target to /etc/hosts and call it by its name:

``` bash
nano /etc/hosts
>> 192.168.1.1      hostname
nmap hostname
```

## nmap port selection

Scan a single Port

``` bash
nmap -p 22 192.168.1.1
```

Scan a range of ports

``` bash
nmap -p 1-100 192.168.1.1
```

Scan 100 most common ports (Fast)

``` bash
nmap -F 192.168.1.1
```

Scan all 65535 ports

``` bash
nmap -p- 192.168.1.1
```

## nmap port scan types

Scan using TCP connect

``` bash
nmap -sT 192.168.1.1
```

Scan using TCP SYN scan (default)

``` bash
nmap -sS 192.168.1.1
```

Scan UDP ports

``` bash
nmap -sU -p 123,161,162 192.168.1.1
```

Scan selected ports - ignore discovery

``` bash
nmap -Pn -F 192.168.1.1
```

## Service and OS detection

Detect OS and Services

``` bash
nmap -A 192.168.1.1
```

Standard service detection

``` bash
nmap -sV 192.168.1.1
```

More aggressive Service Detection

``` bash
nmap -sV --version-intensity 5 192.168.1.1
```

Lighter banner grabbing detection

``` bash
nmap -sV --version-intensity 0 192.168.1.1
```

Run default scripts

``` bash
nmap -sC 192.168.1.1
```

## Custom scripts

Run custom scripts

``` bash
nmap 192.201.242.3 -p80 -sV --script http-shellshock --script-args "http-shellshock.uri=/gettime.cgi" 
```

Convenient way to find nmap smb, http or ftp specific scripts:

``` bash
ls -al /usr/share/nmap/scripts / | grep smb-*
ls -al /usr/share/nmap/scripts / | grep http-*
ls -al /usr/share/nmap/scripts / | grep ftp-*
```

# nslookup

Find IP address of a website - for A record re-direct for example:

``` bash
nslookup google.com
Server:         192.168.0.254
Address:        192.168.0.254#53

Non-authoritative answer:
Name:   google.com
Address: 213.133.225.180
```

# man

Use to check function's manual, for example **man tail** will show the
manual instruction of the **tail** command.

``` bash
tail -f receive_messages.log
```

# mkdir

Use **mkdir** command to make a new directory: **mkdir Music** it will
create a directory called Music.

-   To generate a new directory inside another directory, use this Linux
    basic command **mkdir Music/Newfile**

-   use the **p** (parents) option to create a directory in between two
    existing directories. For example, **mkdir -p Music/2020/Newfile**
    will create the new "2020" file.

# more

The **more** command is a Linux utility that allows you to display the
contents of a file on the terminal, one screen at a time. It is a simple
and basic tool that is often used to display the output of other Linux
commands, such as \"ls\" or \"grep\", which can produce a lot of output
that may not fit on a single screen.

When you run the **more** command, it will display the first screen of
the file and wait for you to press a key to view the next screen. The
most common keys used with **more** are:

-   spacebar: display the next screen

-   enter: display the next line

-   q: quit the **more** command

The **more** command is a basic pager that does not have advanced
features like searching or scrolling back through the output. It is
often used as a quick and simple way to view the contents of a file
without overwhelming the terminal with too much output at once.

However, the **less** \[[41](#less){reference-type="ref"
reference="less"}\] command is a more advanced pager that has additional
features like searching, scrolling, and jumping to specific parts of the
file. If you need more advanced features for viewing and navigating
through the contents of a file, the **less** command is generally a
better choice than **more**.

# mv

Use **mv** command is to move and rename files.

The arguments in **mv** are similar to **cp**. You need to type mv, the
file's name, and the destination's directory.

``` bash
ls
daniel  matt  test.txt
cp test.txt matt
cd matt/
ls matt/
test.txt
```

# pgrep

Find process PID based on name:

``` bash
ping -c 1000 google.com &
[1] 371
pgrep ping
371
```

# ping

Use the **ping** command to check your connectivity status to a server.
For example, by simply entering **ping google.com**, the command will
check whether you're able to connect to Google and also measure the
response time.

# ps

**ps** command for listing processes. Also see **kill**, **jobs**,
**top**, **pgrep** & **htop** commands. Most common use for listing
processes is **ps -aux** with a = all users, u = list, x = everything.

``` bash
ps
  PID TTY          TIME CMD
   11 pts/0    00:00:00 bash
  348 pts/0    00:00:00 ps
ps -u matt
  PID TTY          TIME CMD
   11 pts/0    00:00:00 bash
  350 pts/0    00:00:00 ps
sleep 60
^Z
[1]+  Stopped                 sleep 60
ps -u matt
  PID TTY          TIME CMD
   11 pts/0    00:00:00 bash
  355 pts/0    00:00:00 sleep
  356 pts/0    00:00:00 ps
ps -u matt | grep sleep
  355 pts/0    00:00:00 sleep
ps -aux | grep sublime~  
matt       50341  0.0  0.0   6332  2148 pts/0    S+   20:28   0:00 grep --color=auto sublime~
```

To find a process by its name: **ps -aux \| grep processname**.

``` bash
ps -aux | grep sublime
matt   163  0.0  0.0   8164   652 pts/2    S+   21:41   0:00 grep sublime
ps aux | grep cron
root       15335  0.0  0.0   4040  2304 ?        Ss   Sep16   0:00 /usr/sbin/cron -f
kali       24229  0.0  0.0   3888  2048 pts/0    S+   11:51   0:00 grep --color=auto cron
```

# pstree

Show process tree.

# pwd

**pwd** command for Print Working Directory to find out the path of the
current working directory (folder) you're in. The command will return an
absolute (full) path, which is basically a path of all the directories
that starts with a forward slash (/). An example of an absolute path is
/home/username.

``` bash
pwd
/home/matt
```

# rename

## Single file

To rename a single file using the **rename** command, you can use the
following syntax:

``` bash
rename 's/oldname/newname/' oldname
rename 's/oldname\.txt$/newname\.doc/' oldname.txt
```

## Multiple files

The **rename** command is a utility for renaming multiple files at once.

Rename all files with TXT extension to DOC extension:

``` bash
rename 's/\.txt$/\.doc/' *.txt
```

Note: You can also use the -n flag to do a dry run, which will show you
what the command will do without actually renaming the files. For
example:

``` bash
rename -n 's/\.txt$/\.doc/' *.txt
```

Replace all spaces in file names with underscores:

``` bash
rename 's/ /_/g' *
```

Append the current date to the end of all file names:

``` bash
rename 's/$/_$(date +%Y%m%d)/' *
```

Change all file names to be uppercase:

``` bash
rename 'y/a-z/A-Z/' *
```

Convert all file names to lowercase:

``` bash
rename 'y/A-Z/a-z/' *
```

Remove all digits from the file names:

``` bash
rename 's/[0-9]//g' *
```

## Patterns

**New pattern**\
Use the rename command to rename all files in the current directory that
end with PNG extension to the new pattern 'Twitter_XXXX.png':

``` bash
rename 's/\.png$/_(\\d{4})\.png/' *.png
```

**Existing pattern**\
Using **rename** command (may need to be installed) Using the
'$s/oldname/newname/$' syntax to search for and replace *oldname* with
*newname*. Below 'file' will be replaced by 'text' for all TXT files.

``` bash
rename -v 's/file/text/' *.txt
```

# rmdir

If you need to delete a directory, use the **rmdir** command. However,
**rmdir** only allows to delete empty directories.

# rm

The **rm** command is used to delete directories and the contents within
them. If you only want to delete the directory --- as an alternative to
rmdir --- use **rm -r**. To prevent from having to approve each and
individual notification per file, add **-f**, example: **rm -r -f**.

Note: Be very careful there is no undo!

# rTorrent

1.  Starting up rTorrent and download

    ``` bash
    rTorrent
    ENTER
    <PASTE TORRENT URL>
    ENTER
    <SELECT TORRENT with UP/DOWN KEYS>
    CTRL+S
    ```

2.  Stop torrent

    ``` bash
    <SELECT TORRENT with UP/DOWN KEYS>
    CTRL+D
    ```

    WARNING - Press only once, 2nd time is to delete the file.

3.  Exit rTorrent

    ``` bash
    CTRL+Q
    ```

# scp

**scp** (secure copy) is a command-line utility that allows you to
securely copy files and directories between two locations. With **scp**,
you can copy a file or directory:

-   From your local system to a remote system

-   From a remote system to your local system

-   Between two remote systems from your local system

When transferring data with **scp**, both the files and password are
encrypted so that anyone snooping on the traffic doesn't get anything
sensitive.

-P - Specifies the remote host ssh port. -p - Preserves files
modification and access times. -q - Use this option if you want to
suppress the progress meter and non-error messages. -C - This option
forces **scp** to compresses the data as it is sent to the destination
machine. -r - This option tells **scp** to copy directories recursively.

Copy test.txt from a local to remote system:

``` bash
kali@kali:~/www.site$ scp index.html  pi@100.87.21.13:~/
pi@100.87.21.13's password:
index.html                                              100% 3241   527.6KB/s   00:00
```

Copy folder from local to remote system:

``` bash
kali@kali:~/www.site$ scp -r css/  pi@100.87.21.13:~/
pi@100.87.21.13's password:
styleguide.css                                          100%   12     3.9KB/s   00:00
index.css                                               100% 1406   186.1KB/s   00:00
globals.css                                             100%  625    52.0KB/s   00:00
```

Note: By not including the trailing '/' at the end of foo, you will copy
the directory itself (including contents), rather than only the contents
of the directory.

# sed

**sed** is a powerful text stream editor. Can do insertion, deletion,
search and replace(substitution).

``` bash
cat > geekfile.txt
unix is great os. unix is opensource. unix is free os.
learn operating system.
unix linux which one you choose.
unix is easy to learn.unix is a multiuser os.Learn unix .unix is a powerful.
```

Replacing or substituting string : **sed** command is mostly used to
replace the text in a file. The below simple **sed** command replaces
the word 'unix' with 'linux' in the file.

``` bash
sed 's/unix/linux/' geekfile.txt
linux is great os. unix is opensource. unix is free os.
learn operating system.
linux linux which one you choose.
linux is easy to learn.unix is a multiuser os.Learn unix .unix is a powerful.
```

Here the "s" specifies the substitution operation. The "/" are
delimiters. The 'unix' is the search pattern and the 'linux' is the
replacement string. By default, the **sed** command replaces the first
occurrence of the pattern in each line and it won't replace the second,
third\... occurrence in the line.

Replacing the nth occurrence of a pattern in a line : Use the /1, /2 etc
flags to replace the first, second occurrence of a pattern in a line.
The below command replaces the second occurrence of the word "unix" with
"linux" in a line.

``` bash
sed 's/unix/linux/2' geekfile.txt
```

Replacing all the occurrence of the pattern in a line : The substitute
flag /g (global replacement) specifies the **sed** command to replace
all the occurrences of the string in the line.

``` bash
sed 's/unix/linux/g' geekfile.txt
```

# shutdown

The **shutdown** \[OPTIONS\] \[TIME\] \[MESSAGE\] command expressions
take the following form:

-   OPTIONS - reboot \[-r\], halt \[-h\], or power-off (default)

-   TIME - when to perform the shutdown process, either 'now' or delay
    in seconds: '-t 30'

-   MESSAGE - specifies a message which will be broadcast to all users

Example:

``` bash
sudo shutdown -r now
```

# ssh

[ssh]{acronym-label="ssh" acronym-form="singular+full"} command provides
a secure encrypted connection between two hosts over an insecure
network. This connection can be used for terminal access, file
transfers, and for tunneling other applications. Graphical X11
applications can also be run securely over SSH from a remote location,
**-X** Enables X11 forwarding.

``` bash
ssh -i "key-sydney.pem" ec2-user@ec2-13-239-35-169.ap-southeast-4.compute.amazonaws.com
```

In example above, a PEM key is passed along after **-i** argument, then
follows username@remotehost-address. If a key is not attached, a
password will be required for login to the ssh session. Pass **-p**
argument to specify port if different from default 22.

Copy files across ssh:

``` bash
scp fileName username@remotehost-address:/home/username/destination
```

Print your origin IP address using:

``` bash
echo $SSH_CLIENT | awk '{ print $1}'
```

# ss

Command used for network socket information and can be useful for
troubleshooting and analyzing network connections on a Linux system.

``` bash
sudo ss -ntplu
```

-   -n instructs ss to display numeric addresses instead of resolving
    hostnames. This can be helpful for performance and to avoid
    potential delays in hostname resolution.

-   -t specifies that only TCP sockets should be displayed. This option
    filters the output to show only TCP-related information.

-   -p displays the process name and ID (PID) associated with each
    network socket. It can help you identify which processes are using
    specific network ports.

-   -lshows only listening sockets. This option filters the output to
    display sockets that are actively listening for incoming
    connections.

-   -u displays UDP sockets. By including this option, you can also see
    information about UDP connections and listening sockets.

# stress

``` bash
matt@kali:~$ sudo apt install stress
matt@kali:~$ stress --cpu 2
```

# sudo

Short for "SuperUser Do", this command enables you to perform tasks that
require administrative or root permissions. However, it is not advisable
to use this command for daily use because it might be easy for an error
to occur if you did something wrong. Use **sudo su -** to upgrade
yourself as root without that command timing out. If you forgot to use
**sudo** and get an error message, type **sudo !!** to run that command
again under **sudo**. This saves you from entering that command again
and adding sudo at the front.

``` bash
matt@kali:~$ sudo su -
```

# sysbench

Sysbench, as the name suggests, is a command line app to run benchmarks
on your system. Written in Lua, Sysbench is mainly intended for doing
database benchmarking. However it includes options to test CPU, memory
and file throughput as well.

``` bash
matt@kali:~$ sudo apt install sysbench
```

To start a benchmark using Sysbench, run the following command:

``` bash
matt@kali:~$ pi@raspberrypi:~$ sysbench cpu --threads=2 run
sysbench 1.0.20 (using system LuaJIT 2.1.0-beta3)

Running the test with following options:
Number of threads: 2
Initializing random number generator from current time


Prime numbers limit: 10000

Initializing worker threads...

Threads started!

CPU speed:
events per second:  1169.21

General statistics:
total time:                          10.0017s
total number of events:              11703

Latency (ms):
     min:                                    1.70
     avg:                                    1.71
     max:                                    2.31
     95th percentile:                        1.76
     sum:                                19991.98

Threads fairness:
events (avg/stddev):           5851.5000/7.50
execution time (avg/stddev):   9.9960/0.00
```

# systemctl

In a Kali Linux distribution, which is based on Debian, systemd is
commonly used as the init system to bootstrap user space during system
startup and manage system processes thereafter. The **systemctl**
command is used to control the systemd system and service manager.

However, for backward compatibility, many Linux distributions including
Kali Linux provide a **service** command that acts as a utility for
initializing and managing system services. Under the hood, this
**service** command is often a wrapper that interfaces with systemd to
manage services in a way that is compatible with older SysV init
scripts. When you use **service** on a system running systemd, the
service utility usually redirects the commands to **systemctl**.

For example, both of the following commands achieve the same
result---starting the SSH service:

``` bash
sudo systemctl start ssh
```

``` bash
sudo service ssh start
```

## Starting & stopping Services

``` bash
sudo systemctl start application.service #Start a service

sudo systemctl stop application.service #stop a currently running service

sudo systemctl restart application.service #restart a running service

sudo systemctl reload application.service #reload its configuration files (without restarting)
```

## Checking the Status of Services

``` bash
sudo systemctl status yum-cron

sudo systemctl start yum-cron

sudo systemctl status yum-cron
yum-cron process started

systemctl list-units 'cloud*'  #filter by services starting with 'cloud*'
UNIT                       LOAD   ACTIVE SUB       DESCRIPTION
cloud-config.service       loaded active exited    Apply the settings specified in cloud-config
cloud-final.service        loaded active exited    Execute cloud user/final scripts
cloud-init-local.service   loaded active exited    Initial cloud-init job (pre-networking)
cloud-init.service         loaded active exited    Initial cloud-init job (metadata service crawler)
cloud-init-hotplugd.socket loaded active listening cloud-init hotplug hook socket
cloud-config.target        loaded active active    Cloud-config availability
cloud-init.target          loaded active active    Cloud-init target

LOAD   = Reflects whether the unit definition was properly loaded.
ACTIVE = The high-level unit activation state, i.e. generalization of SUB.
SUB    = The low-level unit activation state, values depend on unit type.
7 loaded units listed. Pass --all to see loaded but inactive units, too.
To show all installed unit files use 'systemctl list-unit-files'.
```

## System State Overview

``` bash
systemctl list-units #list all units currently active on the system
```

The output has the following columns:

-   UNIT: The systemd unit name

-   LOAD: Whether the unit's configuration has been parsed by systemd.
    The configuration of loaded units is kept in memory.

-   ACTIVE: A summary state about whether the unit is active. This is
    usually a fairly basic way to tell if the unit has started
    successfully or not.

-   SUB: This is a lower-level state that indicates more detailed
    information about the unit. This often varies by unit type, state,
    and the actual method in which the unit runs.

-   DESCRIPTION: A short textual description of what the unit is/does.

## Displaying Dependencies

``` bash
systemctl list-dependencies sshd.service #display hierarchy of dependencies
```

By now, you should be familiar with some of the basic capabilities of
the systemctl command that allow you to interact with and control your
systemd instance. The systemctl utility will be your main point of
interaction for service and system state management.

While systemctl operates mainly with the core systemd process, there are
other components to the systemd ecosystem that are controlled by other
utilities. Other capabilities, like log management and user sessions are
handled by separate daemons and management utilities
(journald/journalctl and logind/loginctl respectively). Taking time to
become familiar with these other tools and daemons will make management
an easier task.

# tail

This one has a similar function to the head command, but instead of
showing the first lines, the **tail** command will display the last ten
lines of a text file. For example, **tail -n filename.ext**. Use
**tail - f** to see a live feed of the log file.

# tar

The **tar** command is the most used command to archive multiple files
into a tarball --- a common Linux file format that is similar to zip
format, with compression being optional. This command is quite complex
with a long list of functions such as adding new files into an existing
archive, listing the content of an archive, extracting the content from
an archive, and many more.

Command below run in website directory **/var/www/html/** compresses and
bundles whole website (all files = **\***) including sub-directories,
into **key.tar.gz**. Prefixes **-cvzf** respectively: **-c** for create
archive, **-v** for verbose output, **-z** for filter the archive
through gzip, **-f** for filename **key.tar.gz**. Alternatively, **-j**
would have filter the archive through bzip2. WARNING: **-f** prefix must
be last one, pointing to the filename.

::: {#tab:tar-arguments}
  **Arg**   **Description**
  --------- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **-c**    Create a new archive file containing the specified files or directories
  **-C**    Change to the specified directory before performing the operation. Useful to **tar** files from a different directory or extract files into a specific directory
  **-f**    Specify the name of the archive file. Typically used right before specifying the filename, e.g., **tar -cf myarchive.tar mydirectory/**
  **-j**    Compress the archive using **bzip2** compression and create a **.tar.bz2** file. When used with the **x** option, it extracts from a **.tar.bz2** file
  **-J**    Compress the archive using **xz** compression. When used with the **c** option, it creates a **.tar.xz** file. When used with the x option, it extracts from a **.tar.xz** file
  **-t**    Show files & directories stored in the tarball without extracting them
  **-v**    Verbose mode, provides detailed output about what **tar** is doing
  **-x**    Extract files & directories from the **tar** archive file
  **-z**    Compress the archive using **gzip** compression. When used with the **c** option, it creates a **.tar.gz** file. When used with the **x** option, it extracts from a **.tar.gz** file

  : tar command arguments
:::

## Compress

``` bash
tar -cvzf mytarball.tar.gz *          #gz
tar -jtvf mytarball.tar.bz2 *         #bz2
tar -Jtvf mytarball.tar.xz *          #xz
```

Note: bz2 is about 2x faster than gz but with slightly lower compression
ratio.

## Check / Read only

View archive contents using:

``` bash
tar -ztvf mytarball.tar.gz
```

## Extract

``` bash
tar -xzvf mytarball.tar.gz          #gz
tar -xjvf mytarball.tar.bz2         #bz2
tar -xJvf mytarball.tar.xz          #xz
```

Extract with destination directory:

``` bash
tar -xzvf mytarball.tar.gz -C /home/backups/        #gz
tar -xjvf mytarball.tar.bz2 -C /tmp/                #bz2
tar -xJvf mytarball.tar.xz -C /tmp/                 #xz
```

# time

Calculate time used by function to run. Test below performed on 4610
files (7.86GB)

``` bash
time tar -zcvf gzip.tar.gz *
...
real    2m49.320s
user    2m45.397s
sys     0m12.880s

time tar -jcvf bzip2.tar.bz2 *
...
real    1m21.479s
user    1m20.261s
sys     0m9.085s

time tar -Jcvf xz.tar.xz *
...
real    16m2.717s
user    15m56.146s
sys     0m53.151s
```

Conclusion do not use xz, prefer bz2.

# tmux

Terminal multiplexer. CTRL+B+C to create a new terminal window. CTRL+B+0
to get back to terminal 0 and same for all other numbers.

# toilet

Turn any text into ASCII character art:

``` bash
toilet matt
                 m      m
 mmmmm   mmm   mm#mm  mm#mm
 # # #  "   #    #      #
 # # #  m"""#    #      #
 # # #  "mm"#    "mm    "mm
```

# top

**top** command displays a list of running processes and how much
hardware resources each process uses. Best alternative is **htop**. By
default, it filters on CPU. To filter by memory use, use **top -o
rsize**.

# touch

The touch command allows you to create a blank new file through the
Linux command line. As an example, enter **touch
/var/www/html/index.html** to create an HTML file entitled Web under the
Documents directory.

# trunkate

**truncate** command specifically shrinks or extends a list of files to
the desired size. -c do not create any files (default creates new files
if the specified file does not exist) -s set or adjust the file size by
SIZE bytes -r base size on file

``` bash
ls -lh test2.txt
-rw-rw-r-- 1 ec2-user ec2-user 5.0K Nov 15 12:40 test2.txt
```

# uname

The **uname** command, short for [unix]{acronym-label="unix"
acronym-form="singular+abbrv"} Name, will print detailed information
about your Linux system like the machine name, operating system, kernel,
and so on. To find which architecture you are running on, run:

``` bash
uname -m
x86_64
```

# unrar

unrar is a common compression app which comes free / paid on Windows
systems, however it is already part of most Linux distributions. This is
why I use my WSL to decompress RAR archives without having to install
anythgin under Windows.

``` bash
unrar x myarchive.rar
```

# updatedb

The **updatedb** command creates or updates a database that is used by
the **locate** command to find files across the entire filesystem.

# uptime

**uptime** is used to check for how long the system has been running.

# useradd, userdel

**useradd** is used to create a new user, while **passwd** is adding a
password to that user's account. To add a new person named John type,
**useradd John** and then to add his password type, **passwd
123456789**.

To remove a user is very similar to adding a new user. To delete the
users account type, **userdel UserName**

# w

Show who is logged on and what they are doing.

``` bash
w
 10:59:31 up 2 days, 20:46,  3 users,  load average: 0.00, 0.00, 0.00
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
root     tty1     -                Thu14    2days  0.94s  0.74s -zsh
root     ttyS0    -                Thu14    2days  0.92s  0.88s -zsh
kali     pts/0    120.149.86.230   10:50    0.00s  1.05s  0.01s w
```

# watch

The **watch** command provides an easy way to monitor the output of a
command or script in real-time without having to run the command
repeatedly.

1.  Run the **ls -l** command every 1 second and display the output in
    the terminal. The -n option is used to specify the interval at which
    the command is run.

    ``` bash
    watch -n 1 "ls -l"
    ```

2.  Run the **free -m** command every 5 seconds and display the output
    in the terminal. The free command is used to display information
    about the system's memory usage, and the **-m** option is used to
    display the information in megabytes.

    ``` bash
    watch -n 5 "free -m"
    ```

# wc

Wordcount example:

``` bash
tshark -r HTTP_traffic.pcap | wc -l
```

# wget

To download files from the internet simply type **wget** followed by the
download link. Example to scrub all jpg, jpeg, png, and gif files from a
website:

``` bash
wget -r -nd -H -A jpg,jpeg,png,gif --no-parent --ignore-length --reject -e robots=off http://alljpporn.com/
```

# which

To find the location of an executable file (i.e., a program or script)
in your system's PATH.

``` bash
which traceroute
/usr/sbin/traceroute
```

To find out which *shell* is currently running:

``` bash
echo $SHELL
/bin/bash
which $SHELL
/bin/bash
```

While **echo \$SHELL** simply displays the value stored in the
**\$SHELL** variable, **which \$SHELL** takes the value stored in the
**\$SHELL** variable and tries to locate an executable file with that
path in your system's PATH. It effectively attempts to find the location
of the shell executable associated with the path in the **\$SHELL**
variable.

In contrast, **locate** is a better choice for quickly locating any file
or directory by name or pattern throughout the entire file-system based
on the pre-built database called the \"locate database\".

# who

Show who is logged on.

``` bash
who
root     tty1         2023-09-14 14:12
root     ttyS0        2023-09-14 14:12
kali     pts/0        2023-09-17 10:50 (120.149.86.230)
```

# whoami

**whoami** is used to display the username.

# whois

The whois command queries the database of the [rir]{acronym-label="rir"
acronym-form="singular+full"} responsible for the IP address and returns
information about the IP address and its owner. Example below for my
OpenVPN exit point in Singapore (AWS ap-southeast-1):

``` bash
whois 52.76.221.243
#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at: https://www.arin.net/resources/registry/whois/tou/
#
# If you see inaccuracies in the results, please report at
# https://www.arin.net/resources/registry/whois/inaccuracy_reporting/
#
# Copyright 1997-2023, American Registry for Internet Numbers, Ltd.
#


NetRange:       52.0.0.0 - 52.79.255.255
CIDR:           52.0.0.0/10, 52.64.0.0/12
NetName:        AT-88-Z
NetHandle:      NET-52-0-0-0-1
Parent:         NET52 (NET-52-0-0-0-0)
NetType:        Direct Allocation
OriginAS:
Organization:   Amazon Technologies Inc. (AT-88-Z)
RegDate:        1991-12-19
Updated:        2021-02-10
Ref:            https://rdap.arin.net/registry/ip/52.0.0.0



OrgName:        Amazon Technologies Inc.
OrgId:          AT-88-Z
Address:        410 Terry Ave N.
City:           Seattle
StateProv:      WA
PostalCode:     98109
Country:        US
RegDate:        2011-12-08
Updated:        2022-09-30
Comment:        All abuse reports MUST include:
Comment:        * src IP
Comment:        * dest IP (your IP)
Comment:        * dest port
Comment:        * Accurate date/timestamp and timezone of activity
Comment:        * Intensity/frequency (short log extracts)
Comment:        * Your contact details (phone and email) Without these we will be unable to identify the correct owner of the IP address at that point in time.
Ref:            https://rdap.arin.net/registry/entity/AT-88-Z


OrgAbuseHandle: AEA8-ARIN
OrgAbuseName:   Amazon EC2 Abuse
OrgAbusePhone:  +1-206-555-0000
OrgAbuseEmail:  abuse@amazonaws.com
OrgAbuseRef:    https://rdap.arin.net/registry/entity/AEA8-ARIN

OrgRoutingHandle: ARMP-ARIN
OrgRoutingName:   AWS RPKI Management POC
OrgRoutingPhone:  +1-206-555-0000
OrgRoutingEmail:  aws-rpki-routing-poc@amazon.com
OrgRoutingRef:    https://rdap.arin.net/registry/entity/ARMP-ARIN

OrgTechHandle: ANO24-ARIN
OrgTechName:   Amazon EC2 Network Operations
OrgTechPhone:  +1-206-555-0000
OrgTechEmail:  amzn-noc-contact@amazon.com
OrgTechRef:    https://rdap.arin.net/registry/entity/ANO24-ARIN

OrgNOCHandle: AANO1-ARIN
OrgNOCName:   Amazon AWS Network Operations
OrgNOCPhone:  +1-206-555-0000
OrgNOCEmail:  amzn-noc-contact@amazon.com
OrgNOCRef:    https://rdap.arin.net/registry/entity/AANO1-ARIN

OrgRoutingHandle: IPROU3-ARIN
OrgRoutingName:   IP Routing
OrgRoutingPhone:  +1-206-555-0000
OrgRoutingEmail:  aws-routing-poc@amazon.com
OrgRoutingRef:    https://rdap.arin.net/registry/entity/IPROU3-ARIN


#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at: https://www.arin.net/resources/registry/whois/tou/
#
# If you see inaccuracies in the results, please report at
# https://www.arin.net/resources/registry/whois/inaccuracy_reporting/
#
# Copyright 1997-2023, American Registry for Internet Numbers, Ltd.
#
```

``` bash
nslookup linkedin.com
Server:         172.24.112.1
Address:        172.24.112.1#53

Non-authoritative answer:
Name:   linkedin.com
Address: 13.107.42.14
Name:   linkedin.com
Address: 2620:1ec:21::14

matt@kali:~$ whois 13.107.42.14

#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at: https://www.arin.net/resources/registry/whois/tou/
#
# If you see inaccuracies in the results, please report at
# https://www.arin.net/resources/registry/whois/inaccuracy_reporting/
#
# Copyright 1997-2023, American Registry for Internet Numbers, Ltd.
#


NetRange:       13.64.0.0 - 13.107.255.255
CIDR:           13.96.0.0/13, 13.104.0.0/14, 13.64.0.0/11
NetName:        MSFT
NetHandle:      NET-13-64-0-0-1
Parent:         NET13 (NET-13-0-0-0-0)
NetType:        Direct Allocation
OriginAS:
Organization:   Microsoft Corporation (MSFT)
RegDate:        2015-03-26
Updated:        2021-12-14
Ref:            https://rdap.arin.net/registry/ip/13.64.0.0



OrgName:        Microsoft Corporation
OrgId:          MSFT
Address:        One Microsoft Way
City:           Redmond
StateProv:      WA
PostalCode:     98052
Country:        US
RegDate:        1998-07-10
Updated:        2022-03-28
Comment:        To report suspected security issues specific to traffic emanating from Microsoft online services, including the distribution of malicious content or other illicit or illegal material through a Microsoft online service, please submit reports to:
Comment:        * https://cert.microsoft.com.
Comment:
Comment:        For SPAM and other abuse issues, such as Microsoft Accounts, please contact:
Comment:        * abuse@microsoft.com.
Comment:
Comment:        To report security vulnerabilities in Microsoft products and services, please contact:
Comment:        * secure@microsoft.com.
Comment:
Comment:        For legal and law enforcement-related requests, please contact:
Comment:        * msndcc@microsoft.com
Comment:
Comment:        For routing, peering or DNS issues, please
Comment:        contact:
Comment:        * IOC@microsoft.com
Ref:            https://rdap.arin.net/registry/entity/MSFT


OrgTechHandle: IPHOS5-ARIN
OrgTechName:   IPHostmaster, IPHostmaster
OrgTechPhone:  +1-425-538-6637
OrgTechEmail:  iphostmaster@microsoft.com
OrgTechRef:    https://rdap.arin.net/registry/entity/IPHOS5-ARIN

OrgTechHandle: MRPD-ARIN
OrgTechName:   Microsoft Routing, Peering, and DNS
OrgTechPhone:  +1-425-882-8080
OrgTechEmail:  IOC@microsoft.com
OrgTechRef:    https://rdap.arin.net/registry/entity/MRPD-ARIN

OrgAbuseHandle: MAC74-ARIN
OrgAbuseName:   Microsoft Abuse Contact
OrgAbusePhone:  +1-425-882-8080
OrgAbuseEmail:  abuse@microsoft.com
OrgAbuseRef:    https://rdap.arin.net/registry/entity/MAC74-ARIN


#
# ARIN WHOIS data and services are subject to the Terms of Use
# available at: https://www.arin.net/resources/registry/whois/tou/
#
# If you see inaccuracies in the results, please report at
# https://www.arin.net/resources/registry/whois/inaccuracy_reporting/
#
# Copyright 1997-2023, American Registry for Internet Numbers, Ltd.
#
```

# yum

Same as **apt** for Debian / Kali systems, yum is the installer for
Fedora / Amazon Linux systems. In the examples provided for **apt**,
just replace **apt** by **yum**.

# zip, unzip

Use the **zip** command to compress your files into a zip archive, and
use the **unzip** command to extract the zipped files from a zip
archive.

``` bash
zip plug.zip plug.php
adding: plug.php (deflated 35%)
```
