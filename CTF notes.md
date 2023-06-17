# CTF Preparation Notes

## Linux Basics

### File Operations

- View EXIF data of a file: `exiftool filename`
- Open a file: `xdg-open filename`
- Open the current folder in a file explorer: `xdg-open .`
- Open a file (GNOME): `eog filename`
- Convert hexadecimal to ASCII: `echo -n 0x39 | xxd -r -p`
- Write a secret message to a file: `echo 'Secret message.' > secret.txt`
- List files in a website using a wordlist: `dirb <target-website> /path/to/wordlist.txt`

### Steganography

- Hide a message in an image: `steghide embed -ef secret.txt -cf DSCN0042.jpg`
- Extract a message from an image: `steghide extract -sf DSCN0042.jpg -xf secret_extract.txt`

### Forensics

- binwalk: Use binwalk to analyze the file's contents and identify embedded files, hidden data, or appended archives. Run the following command to extract any embedded files `binwalk -e filename`
- Extract files with binwalk: `binwalk --dd='.*' file.pptm`
- View EXIF data of a file: `exiftool filename`

### Directory and File Operations

- Move to the previous directory: `cd -`
- List files and directories with detailed information: `ls -la`
- Display file content: `cat filename`
- Display readable text from a file: `strings filename`
- Display usage information: `--help`
- Create a directory: `mkdir`
- Create a file: `touch`
- Get details about a file: `stat filename`
- View command history with specified word: `history | grep mkdir`

### File Removal (rm)

- Remove a file: `rm filename`
- Remove an empty directory: `rm -d directory`
- Remove a non-empty directory: `rm -rf`

### File Copying (cp)

- Copy a file: `cp file.txt file_backup.txt`
- Copy a file to a directory: `cp file.txt /tmp`
- Copy a directory: `cp -R Pictures /opt/backup`

### File Movement (mv)

- Move a file to a directory: `mv file.txt /tmp`
- Rename a file: `mv file.txt file1.txt`
- Move multiple files to a directory: `mv file.txt file1.txt /tmp`

## Linux File Permissions

In Linux, each file is associated with an owner, a group, and permission access rights for three different classes of users: owner (user), group members (group), and everybody else (others). The following permission types apply to each class:

- Read permission: 'r'
- Write permission: 'w'
- Execute permission: 'x'

The permissions number of a specific user class is represented by the sum of the values of the permissions for that group:

- 'r' (read) = 4
- 'w' (write) = 2
- 'x' (execute) = 1
- No permissions = 0

To set permissions, combine the values for each class and order them as follows:

`<owner permissions><group permissions><others permissions>`

For example, to set read, write, and execute permissions for the owner, read and write permissions for the group, and read permissions for everybody else, use the value `764`.

### Changing Permissions (chmod)

- Change permissions of a file: `chmod 600 new_file.txt`

### Changing Ownership (chown)

- Change ownership of a file: `chown username filename.txt`

## Finding Files (find)

- Find files with a partial name: `find /etc -name '*.conf'`
- Find files with an exact filename: `find /etc -name 'client.conf'`

The asterisk '*' character can be used in the following ways:

- `file*`: Search for all files and folders that begin with 'file'
- `*file`: Search for all files and folders

 that end with 'file'
- `*file*`: Search for all files and folders that have 'file' in any position

## Text Searching (grep)

- Search for a word in a file: `grep 'Directory' /etc/rsyslog.conf`
- Case-insensitive search: `grep -i 'Directory' /etc/*.conf`
- Search recursively in a directory: `grep -i -R 'Directory' /etc/`

## Downloading Files (wget)

- Download a specified file and change its save file name: `wget https://filesamples.com/samples/document/txt/sample1.txt -O new_name.txt`

## Base64 Encoding and Decoding

- Encode text to Base64: `echo -n 'Text that will be base64 encoded' | base64`
- Multiple rounds of Base64 encoding: `echo -n 'Text that will be base64 encoded' | base64 | base64`
- Decode Base64 to text: `echo -n 'VGV4dCB0aGF0IHdpbGwgYmUgYmFzZTY0IGVuY29kZWQ=' | base64 --decode`
- Multiple rounds of Base64 decoding: `echo -n 'VkdWNGRDQjBhR0YwSUhkcGJHd2dZbVVnWW1GelpUWTBJR1Z1WTI5a1pXUT0K' | base64 -d | base64 -d` (can be shortened to `-d`)
- Decode Base64 to text with multiple rounds: `echo -n 'VkdWNGRDQjBhR0YwSUhkcGJHd2dZbVVnWW1GelpUWTBJR1Z1WTI5a1pXUT0K' | base64 --decode | base64 --decode`
