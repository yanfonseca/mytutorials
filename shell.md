# Introduction to Shell 

### Checking installation
* which - Used with a program. 
   - which bash. It prints where bash is installed.
   - program -v or program --version. It prints the program's version.

### Special characters
* ..    : The directory above the one you are.
* .     : Current directory.
* ~     : Home directory. // COMO ALTERAR O HOME DIRECTORY? 

## Wildcards: 
* `*` : It matches zero or more words or characters.
* ? : It matches a single character.
* `[ ]` : It matches any one character inside square brackets.
   - [0123] - Matches to 0, 1 or 3.
* { } : It matches any of the patterns comma-separeted.
   - {*.csv, *.txt} - Matches to files ended by the specification.

# Commands

* man    : To access the manual's command.
   - man commandname/program: It hows comandname's manual.

* pwd   : *Print working directory* - It shows where you are in the filesystem.

* history: Print a list of comands used recently.
    - !command - It will run the recent use of the command.
    - !2 - It will run te second command from history.

* ls    : *listing* - It lists the contents of your current directory. 
    - ls .    : The contentes of the current directory.
    - ls path/   : It lists the contents of path.
    - ls -R -F: It lists recursively all contents and what is folder or executable.
    
* mv    : *move* - Move a file or directory from a directory to another one.
    - mv path1/filename1.csv path2/filename2.csv    - It Changes the name of a file too. 
    - mv path/filename1.csv path/filename2.csv path2 - Move files to a new path. 
    - mv path1/filename1.csv path2/filename2.csv path3 - Move files from different paths to a new path.
    
* cp    : *copy* - Copy file
    - cp path/filename1.csv path/filename2.csv - Copy and change the name.
    - cp path/filename1.csv path/filename2.csv path2 - Copy files to a new path. 
    - cp path1/filename1.csv path2/filename2.csv path3 - Copy files from different paths to a new path.
    
* rm    : *remove* - Remove files but not directory.
    - rm path/filename1.csv path/filename2.csv - Remove files.
    - rm path1/filename1.csv path2/filename2.csv - Copy files from different paths to a new path.

* rmdir: *remove directory* - Remove a empty directory.
    - rmdir name - Remove an empty directory.
    - rm -r name - Remove an empty directory.
   
* cat : *concatenate*. 
  - cat *.csv - Concatenate and show all content.
  - cat *.csv | more - Concatenate and show part of the content.
  - cat *.csv | less - Concatenate and show part of the content with navigation between files.
  - cat -n filename.csv - Concatenate file with line numbers.
  - cat *.csv >> filename.csv - Concatente and append to a filename.csv.
  - cat -e filename.csv - Go to the end of a file.
  
* paste: Join files horizontally.
 - paste filename1.csv filename.csv
 
* less: Show just one page. Use :n to go to the next file, :p to go back to the previous one and :q to quit.
    - less filename1.txt filename2.txt.

* more: Old way to see the content of a file.
 - more filename.txt 
 
 * head: It shows the first 10 lines.
    - head filename.txt - First 10 lines.
    - head -n 2 filename.txt - First two lines.
 
 * tail: It shows the last 10 lines and it is the opposite of head command.
 
 * cut: It selects columns from a text file.
    - cut -f 2-5,8 -d , filename.csv - Columns 2 to 5 and 8. The flag -d shows the comma separator.

* grep: *general regular expression parser* - It selects lines that contains a text. It accepts REGEX.
    - Common flags: 
    > -c => Print a count of the matching lines. 
    -h => It don´t print the name of files. 
    -i => Not case sensitive. 
    -l => Print only the name of files that contain matches but not the matches. 
    -n => Print line numbers. 
    -v => Only the lines that don't match.
    
    - grep -v word path/filename.csv - It prints line that don't match.
    - grep -n -v word path/filename.csv - It prints lines that don't match and the numbers of the lines.
    - grep i word path/filename1.csv path/filename2.csv - With not sensitive case.
    - grep '[pc]' filename.txt - REGEX
 
* wc: *word count* - It counts the numbers of characters, words and lines in a file and uses -c, -w and -l.
      - grep word filename.csv : wc -l - It prints the number of the lines that word seached is find.

* sort: 
   - sort filename.csv - Ascending alphabetical order.
   - sort -n filename.csv - Numerically order.
   - sort -n -r filename.csv - Using -r flag reverse order.
   - sort -b -n filename.csv - Ignore branks.
   
* uniq: Remove adjacent duplicates. It is like group by of any language but it has to sort the data before run this command.
   - uniq -c filename.csv - Group by unique and count of duplicates
   - sort | uniq -c

#do an UPDATE HERE
* sed: 

* mkdir - Create a directory
     - mkdir name
   
### Flags

#### Commands share the flags and it is possible to combine flags.

* -n : Number of lines
* -R : Recursive
* -F : Print / after all directories and * after runnable programms
* -e : Print the end of a file
* -f : Columns from a text file
* -d : Separator - ','` ` ';'` ` ':'

# Output command in a file

### By using the shell commands it is possible to export to a new file:

* `>` - it exports to a csv file.
   - head -n 5 filename.csv > newfilename.csv - It exports the first five rows to a newfilename.csv
   - `>` newfilename.csv head -n 1 filename.csv - It is other way to export data to newfilename.csv

### Combine commands using pipe

 * | - The pipe symbol informs the shell to use the left output as input.
   - head filename.csv | tail -n 1

## Print variable's value

### echo

* It prints a value or a variable's value. The character $ is used do access the variable.
   - echo $OSTYPE - It prints the variable's value.
   - echo Hello - It prints "Hello".
   - var=filename.csv - It can't have any space next to `=`.
   - head -n 3 $var - Access the filename.csv using the variable var.

```
var_1='Hello'
var_2='Good'
echo "It is:" $var_1 $var_2
```

* Shell-within-a-shell - Using command date. 
   - var="The date is `date` - It is possible to chall commands with backticks(` `)
   - var="The date is $(date)"
   
* It can begin with #!/usr/bash in the first line - shebang. The /usr/bash is the location of Bash.

   - bash script.sh - To run.
   - ./script.sh - If shebang is mentioned in the first line.
   - $@ or $* - For all arguments.
   - $# - Lenght of arguments.
   - expr 1 + 4 -  It will be 5.
   - echo "5 + 7.5" | bc . The program bc makes possible to run. 
   - echo "scale=2; 5 /3 " | bc
   
* Double bracket notation

```
expr 2 + 3
echo $((3 + 3))

5
5
```
```
num1=10
num2=20
echo "the value is $(echo "($num1 + $num2) / 2" | bc)"
```

```
num1=10
num2=20
value=echo "($num1 + $num2) / 2" | bc
echo "the value is $(value)"
```

## Run commands later

* Sabe the commands learned before inside a script ended by .sh using some editor and run it.
   - bash scripname.sh - It does what is inside the script, can be manipulations or others.

### Pass filenames to scripts

* Using dollar sign followed by at-sign means that all command-line arguments are given to script.
  - bash scriptname.sh \.- It runs scriptiname for each file.

* Process a single argument using $1, $2 to command-line parameters. It is possible pass n numbers of arguments and the first one it will be filename.
   - cut -d, -f $2 $1 inside the file.sh - Inside file.sh for exemple.
   - bash file.sh filename.csv number_columns - $1 is number_columns and $2 is the file
   - The shell waits forevers for the argument if it isn't informed.
   
# Download File

### Using Client URL present in UNIX OS.

* Flags 
   - -L Redirect the http url if a 300 error occurs.
   - -C Resume a previous file transfer.

* curl
   - curl -O https://site.com/filename.csv - Download and save file with original name.
   - curl -o newfilename.csv https://site.com/filename
   
* Use wildcard to download multiple files
   - curl -O https://site.com/*.csv

* Using Globbing Parser - filename001.csv, filename002.csv, filename020....filename100.csv
   - curl -O https://site.com/filename[001-100].csv
   - curl -O https://site.com/fileame[001-100:10].csv - Increment 10.
   
### Using Wget - World Wide Web and get are present in UNIX OS. Various file formats and it's better to multiple file downloads.

* Flags
   - b - Go to background after startup.
   - q - Turn off the Wget output.
   - c - Resume broken dowload.
   - i - List of urls to download.
   
* wget
   - wget -bqc http://site.com/filename.txt
   - wget [flags] [url]
   - wget --help
   
* Multiple file to download with wget
   - wget -i url_list.txt
   - wget --limit-rate=300k -i url_list.txt - It limits download in 300k.
   - wget --wait=3.5 -i url_list.txt - 3.5 seconds between files download.

* Others
   - unzip filename.zip
   - unzip filename.zip && rm filename.zip - Unzip and delete file. (&& it means and)

# Pip

### Some observation about pip

- pip install -r requirements.txt - requirements is a list of packages.
- pip install package1 package2.

# Automation with Cron

* Cron

   - crontab -l - Verify if exits some cron job.
   - `* * * * *` - minute, hour, day of month, month, day of week.
   - echo " * * * * * python filename.py" | crontab 
  
# Script anatomy

* Array in Bash - index start at 0.

   - declare -a array
   - array=(30 40 50) -  Without comma.
   - echo ${arra[@]} - Returns all.
   - echo ${#array[@]} - Array's length
  
# Loop

## The structure is:

* 1 
   - It is possible write the loop in line using (;).

```
 for file in file1 file2 file3; do echo $file; done 
```

* 2

```
for file in file1 file2 file3 
do 
    echo $file 
done 
```

* 3

```
for file in path/*.csv
do 
   echo $file
   grep word $file| head -n 3| tail -n 1 
done 
```

* Inside of the block and after *do* is possible to run commands learned before, like: head, cut, grep and others. It is possible to do one manipulation by file or merge all files and after do what is necessary

* Space in the name of the file causes problems
   - head 'file name.csv' - it is one file but without quotation marks bash does not understand like one file.
   - head file name.csv - it will be a problem because of bash file is a file and names.csv is another one.


# If statement

```
if [ condition ]; then
   #code
else
   #code
fi
```

* Using AND and OR - To use inside the if.

- AND = &&
- OR = ||

```
if grep -q 'teste' text.txt; then
   echo "teste inside"

fi
```

# Functions

* The variables are global, it is the default mode. To be local add "local" before de var
   - local var="text"
   - local var=$1

```
function function_name{
   return
}
```

#UPDATE HERE
## Associative array