# Introduction to Shell

This content is a brief way to learn and review some basic and expert commands to make your daily data manipulation easier and productive.

## Cheking installation
- which command

## Special characters
* ..    : The directory above the one you are.
* .     : Current directory.
* ~     : Home directory. // COMO ALTERAR O HOME DIRECTORY? ###########################################################

## Wildcards: 
* `*` - Matches zero or more words or characters.
* ? - Matches a single character.
* [] - Matches any one character inside square brackets.
   - [0123] - Matches to 0, 1 or 3.
* {} - Matches any of the patterns comma-separeted
   - {*.csv, *.txt} - Matches to files ended by the specification.

## Commands

* man    : To access the manual's command.
   - man comandname: Shows comandname's manual

* pwd   : *Print working directory* - Shows where you are in the filesystem.

* history: Print a list of comands used recently
    - !comand - It will run the recent use of the comand.
    - !2 - It will run te second comand from history. It is !number.

* ls    : *listing* - Lists the contents of your current directory. 
    - ls .    : The contentes of the current directory
    - ls path/   : Lists the contents of path.
    - ls -R:
* mv    : *move* - Move a file or directory from a directory to another one.
    - mv path1/filename1.csv path2/filename2.csv    - Change the name of a file. 
    - mv path/filename1.csv path/filename2.csv path2 - Move files to a new path. 
    - mv path1/filename1.csv path2/filename2.csv path3 - Move files from different paths to a new path.
* cp    : *copy* - Copy file
    - cp path/filename1.csv path/filename2.csv - Copy and change the name
    - cp path/filename1.csv path/filename2.csv path2 - Copy files to a new path. 
    - cp path1/filename1.csv path2/filename2.csv path3 - Copy files from different paths to a new path.
* rm    : *remove* - Remove files but not directory
    - rm path/filename1.csv path/filename2.csv - Remove files.
    - rm path1/filename1.csv path2/filename2.csv - Copy files from different paths to a new path.

* rmdir: *remove directory* - Remove a empty directory
    - rmdir name - Remove and empty directory.
   - rm -r name - Remove an empty directory.
* cat : *concatenate* - Contents of a file
  - cat *.csv - Concatenate and show all content.
  - cat *.csv | more - Concatenate and show part of the content.
  - cat *.csv | less - Concatenate and show part of the content with navigation between files.
  - cat -n filename.csv - Concatenate file with line numbers
  - cat *.csv >> filename.csv - Concatente and append to a filename.csv.
  - cat -e filename.csv - Go to the end of a file
  
* paste: Join files horizontally.
 - paste filename1.csv filename.csv
 
* less: Show just one page. Use :n to go to the next file, :p to go back to the previous one and :q to quit.
    - less filename1.txt filename2.txt

* more: Old way to see the content of a file
 - more filename.txt 
 
 * head: Shows the first 10 lines.
    - head filename.txt - First 10 lines.
    - head -n 2 filename.txt - First two lines.
 
 * tail: Show the last 10 lines and it is the opposite of head command.
 
 * cut: Select columns from a text file.
    - cut -f 2-5,8 -d , filename.csv - Shows columns 2 to 5 and 8. The flag -d show comma separator

* grep: *general regular expression parser* - Select lines that contains a text
    - Common flags: -c => Print a count of the matching lines. 
    -h => It don´t print the name of files. 
    -i => Not case sensitive. 
    -l => Print only the name of files that contain matches but not the matches. 
    -n => Print line numbers. 
    -v => Only the lines that don't match.
    - grep -v word path/filename.csv - Print line that don't match.
    - grep -n -v word path/filename.csv - Print line that don't match and the number of the line.
    - grep i word path/filename1.csv path/filename2.csv - Print the count of matching lines.
 
* mkdir - Create a directory
     - mkdir name

* wc: *word count* - Count number of characters, words and line in a file and uses -c, -w and -l
      - grep word filename.csv : wc -l - Prints the number os lines that word seached shows

* sort: 
   - sort filename.csv - Ascending alphabetical order
   - sort -n filename.csv - Numerically order
   - sort -n -r filename.csv - Using -r flag reverse order
   - sort -b -n filename.csv - Ignore branks
   
* uniq: Remove adjacent duplicates. To be like group by of any language has to sort the data before
   - uniq -c filename.csv - Groupby unique and count of duplicates
   
#### Flags

* -n : Number of lines
* -R : Recursive
* -F : Print / after all directories and * after runnable programms
* -e : Print the end of a file
* -f : Columns from a text file
* -d : Separator - ','` ` ';'` ` ':'

###### It is possible to combine flags.

# Output command in a file

## By using the shell comands it is possible to export to a new file:

* `>` - Export to a csv file
   - head -n 5 filename.csv > newfilename.csv - Exports the first five rows to a newfilename.csv
   - `>` newfilename.csv head -n 1 filename.csv - It is other way to export data to newfilename.csv

## Combine commands using pipe

 * | - Pipe symbol inform the shell to use the left output as input.
   - head filename.csv | tail -n 1

# Print variable's value

## echo  
### Easy way to print a value or a variable's value and the character $ is used do access the variable.
   - echo $OSTYPE - Prints the variable's value
   - echo Hello - Prints "Hello"
   - var=filename.csv - echo testing shows the velue of var. Can't have any space next to `=`
   - head -n 3 $var - Access the filename.csv using the variable var
   
## Loop

### The structure is:

> for file in file1 file2 file3; do echo $file; done 

- Using ; it is possible write the loop in line

or 

> for file in file1 file2 file3 \
 do \
   echo $file \
> done \

> for file in path/*.csv \
 do \
   
    echo $file
    grep word &file| head -n 3| tail -n 1 \
> done 

* Inside of the block after *do* is possible run commands learned before, like head, cut, grep and others. So is possible to do one manipulation by file or merge all files and after do what is necessary

* Space in the name of the file causes problems
   - For exemple: head'file name.csv'
   - If it is write: head file name.csv it will be a problem

## Run commands later

* Just save the comands learned before inside a script .sh using some editor and run
   - bash scripname.sh - It will do what is inside the script, can be manipulations or other things

### Pass filenames to scripts

* Using dollar sign followed by at-sign and means all command-line arguments are given to script.
  - head -n 2 $@ | wc -l -c insite of script scriptname.sh
  - bash scriptname.sh filename1.csv filename2.csv filename3.csv

* Process a single argument using $1, $2 to command-line parameters. It is possible pass n number of arguments and the first one it will be filename.
   - Write cut -d, -f $2 $1 inside the file.sh
   - bash file.sh filename.csv number_columns - $1 is number_columns and $2 is the file
   - The shell waits forevers for the argument
   
# Download File

### Using Client URL present in UNIX OS.

* Flags 
   - -L Redirect the http url if a 300 error occurs
   - -C Resume a previous file transfer

* curl
   - curl -O https://site.com/filename.csv - Download and save file with original name.
   - curl -o newfilename.csv https://site.com/filename
   
* Use wildcard to download multiple files
   - curl -O https://site.com/*.csv

* Using Globbing Parser - filename001.csv, filename002.csv, filename020....filename100.csv
   - curl -O https://site.com/filename[001-100].csv
   - curl -O https://site.com/fileame[001-100:10].csv - Increment 10
   
### Using Wget - World Wide Web and get present in UNIX OS. Various file formats and it's better to multiple file downloads.

* Flags
   - b - Go to background after startup.
   - q - Turn off the Wget output
   - c - Resume broken dowload
   - i - List of urls to download
   
* wget
   - wget -bqc http://site.com/filename.txt
   - wget [flags] [url]
   - wget --help
   
* Multiple file to download with wget
   - wget -i url_list.txt
   - wget --limit-rate=300k -i url_list.txt - Limit of download is 300k
   - wget --wait=3.5 -i url_list.txt - 3.5 segundos between file download.
