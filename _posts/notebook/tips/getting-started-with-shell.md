
# Positional Argument
```bash
 GNU nano 4.8                position_arg.sh    
echo "$0"
echo "$1"
echo "$2"
echo "$@"
echo "$*"
```
```bash
lamegaton@DESKTOP-R1NK0HV:~/codes$ ./position_arg.sh dog cat mouse X Y
./position_arg.sh
dog
cat
mouse
dog cat mouse X Y
dog cat mouse X Y
```

# Load file using while read
```bash
 GNU nano 4.8                load_file_using_while_read.sh   
#!/bin/bash
# IFS is internal field separator
# what is /etc/passwd?
# -> /etc/passwd is a text file that store usernames
# -> /etc/shadow is a text file that store encrypted passwords

while IFS= read -r LINE; do
        echo "$LINE"
done < "$1"
```

