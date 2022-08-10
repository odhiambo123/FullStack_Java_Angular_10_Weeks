---
layout: post
title:  "Unix Linux Fundamentals"
date:   2022-07-30 18:28:22 -0700
categories: FullStack

---

### Everything is a file
- Everything in linux is a file
    - directory is represented in memory as a file.
    - terminal window, hard disk or partitions are represented as files.
### Working with files.
- `file` 
    - everything is a file
    - use the file command to determine the type of file. e.g file file.txt
    - the file command 
- `ls` 
    - list items in a directory
- `cd`
    - change directory
        - `cd name_of_directory`
- rmdir
    - removes directory
- `touch`
    - is a way to create a file
    - using some flags the touch command can create some properties while creating an empty file 
        - `touch -t 200505050000 SinkoDeMayo`
- `rm`
    - used to remove a file, removes forever
    - `rm -i`  to prevent accidental removals.
    - `rm -r` will not remove non-empty directories.
    - `rm -rf` will erase anything as f means force r means recursive
- `cp`
    - copy a file 
        - use source and target `cp file1 file1.copy`
        - copy to another directory
            - if the target is a directory then the source files are copied to the directory.
        - use `cp -r` copy copy complete directories from source 
        - if copying multiple files, the last argument must be a directory. `cp file1 file1.copy SinkoDeMayo dir42`
        - To prevent overiting files use `-i`.

- `mv`
    - use mv to rename files
        - `mv file1 file2`
    - use mv to rename directories
        - `mv -i` will ask permission to overwrite an existing file
- `rename`
- head
    - displays the first 10 or n lines of a file
        - `head file1`
        - `head -5 file1`
- tail
    - last 10 lines of a file
        - `tail file1`
        - `tail -5 file1`
- cat
    - copy standard input to standard output
    - cat is short for concatenate and can be used to combine files into a larger file `cat file1 file2 file3 >target`
    - use cat to create files `cat>myfile.txt`
    - You can use cat to create flat text files. Type the `cat > myfile.txt`. Type one or more lines, finishing each line with the enter key. After the last line, type and hold the Control (Ctrl) key and press d
    - `<<stop` custom end maker 
         `cat > file1.txt <<stop Its cool, it's summer >stop`
    - used to copy files
        - `cat got.txt > mycopy.txt`
         


- tac
    - is cat backwards!
      ` cat > count << stop
     one
     two
     three
     four
     five
     six
     seven
     eight
     nine
     ten
     stop `
` tac count
ten
nine
eight
seven
six
five
four
three
two
one `

- more
    - use `space bar` to load more on a screen
    - use `q` to quit
- less
- strings
    - display readable ascii strings found in binary files

- vim
    - visual mode
        - type v
    - type mode
        - type i or a
    - editing mode
        - press esc
        - use vim new_file
    - leaving vim
        - go to editing mode
        - :wq