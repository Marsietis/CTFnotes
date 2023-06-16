# CTF preparation notes

## Linux basics

exiftool filename | find exif data
xdg-open filename| open file
xdg-open . | open current folder in file explorer
eog filename| open file (gnome)

echo -n 0x39 | xxd -r -p | outptu to ascii

echo 'Secret message.' > secret.txt | write message to file

steghide embed -ef secret.txt -cf DSCN0042.jpg | hide message in image
steghide extract -sf DSCN0042.jpg -xf secret_extract.txt | extract message

cd - | move to previous dir
ls -la | detailed info

cat | display file content (usage cat filename)
strings | just like cat but with readable text only (usage strings filename)

--help | display usage

mkdir
touch

stat filename | details about file

history | grep mkdir | history with specified word

#### rm
rm filename | removes file
rm -d directory | removes empty dir
rm -rf | removes non empty dir

### cp
cp file.txt file_backup.txt | copy file
cp file.txt /tmp | copy file to dir
cp -R Pictures /opt/backup | copy dir

### mv
mv file.txt /tmp 
mv file.txt file1.txt | rename file
mv file.txt file1.txt /tmp | move multiple files 

In Linux, each file is associated with an owner and a group and assigned with permission access rights for three different classes of users:

    The file owner (user) - 'u'

    The group members (group) - 'g'

    Everybody else (others) - 'o'

Three permission types apply to each class:

    The read permission - 'r'

    The write permission - 'w'

    The execute permission - 'x'

### chmod
chmod 600 new_file.txt

    'r' (read) = 4

    'w' (write) = 2

    'x' (execute) = 1

    no permissions = 0

The permissions number of a specific user class is represented by the sum of the values of the permissions for that group.

    To set read, write and execute permissions to file owner, sum up all values '4+2+1 = 7'.

    To set read and write permissions to file group, sum up read and write values '4+2 = 6'.

    To set only read permissions to everybody else use value '4'.

    Now you have to put together all numbers in correct order - first number represents file/folder owner permissions, second number represents group permissions and last number represents permissions for everybody else: '764'

### chown
chown username filename.txt | change ownership

### find
find /etc -name '*.conf' | find file with part of name
find /etc -name 'client.conf' | find file with exact filename

Asterisk '*' character can be used in following places:

    'file*' - will search for all files and folders which begin with 'file'

    '*file' - will search for all files and folders which end with 'file'

    '*file*' - will search for all files and folder which has 'file' in any place

### grep
grep 'Directory' /etc/rsyslog.conf | search for word in file
grep -i 'Directory' /etc/*.conf | -i case insensitive
grep -i -R 'Directory' /etc/ | serach whole dir

### wget
wget https://filesamples.com/samples/document/txt/sample1.txt -O new_name.txt | get specified file (-O to change save file name)

## Base64

echo -n 'Text that will be base64 encoded' | base64 | encode to base64
echo -n 'Text that will be base64 encoded' | base64 | base64  | multiple times

echo -n 'VGV4dCB0aGF0IHdpbGwgYmUgYmFzZTY0IGVuY29kZWQ=' | base64 --decode | decode from base64
echo -n 'VkdWNGRDQjBhR0YwSUhkcGJHd2dZbVVnWW1GelpUWTBJR1Z1WTI5a1pXUT0K' | base64 -d | base64 -d | can be shortened to -d
echo -n 'VkdWNGRDQjBhR0YwSUhkcGJHd2dZbVVnWW1GelpUWTBJR1Z1WTI5a1pXUT0K' | base64 --decode | base64 --decode

