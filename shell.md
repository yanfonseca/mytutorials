# Introduction to Shell 

   An Introduction to command line, some really good tips that can help you do some specic things using the terminal window. 

### Checking installation
* which - Used with a program. 
   - which bash. It prints where bash is installed.
   - program -v or program --version. It prints the program's version.
   - program --help or command --help. It prints a quicky help.

### Special characters
* ..    : The directory above the one you are in.
* .     : Current directory.
* ~     : Home directory.

### Wildcards: 
* `*` : It matches zero or more words or characters.
* ? : It matches a single character.
* `[ ]` : It matches any one character inside square brackets.
   - [0123] - Matches to 0, 1, 2 or 3.
* { } : It matches any of the patterns comma-separeted.
   - {*.csv, *.txt} - Matches to files ended by the specification.

## Commands

* man    : To access the manual's command.
   - man commandname or man program: It shows comandname's manual.

* pwd   : *Print working directory* - It shows where you are in the filesystem.

* history: Print a list of commands used recently.
    - !command - It will run the recent use of the command.
    - !2 - It will run the second command from history.
    - ctrl + R - It helps seach commands that you have used recently.

* ls    : *listing* - It lists the contents of your current directory. 
    - ls .    : The contents of the current directory.
    - ls path/   : It lists the contents of a path.
    - ls -R -F: It lists recursively all contents and which is folder or executable.
    
* mv    : *move* - Move a file or directory from a directory to another one.
    - mv path1/filename1.csv path2/filename2.csv    - It Changes the name of a file too. 
    - mv path/filename1.csv path/filename2.csv path2 - Move files to a new path. 
    
* cp    : *copy* - Copy file.
    - cp path/filename1.csv path/filename2.csv - Copy and change the name.
    - cp path/filename1.csv path/filename2.csv path2 - Copy files to a new path. 
    - cp path1/filename1.csv path2/filename2.csv path3 - Copy files from different paths to a new path.
    
* rm    : *remove* - Remove files.
    - rm path/filename1.csv path/filename2.csv - Remove files.

* rmdir: *remove directory* - Remove a empty directory.
    - rmdir name - Remove an empty directory.
    - rm -r name - Remove a directory.
   
* cat : *concatenate*. 
  - cat *.csv - It concatenates and shows all contents.
  - cat *.csv | more - It concatenates and shows parts of the content.
  - cat *.csv | less - It concatenates and shows parts of the content with navigation between files.
  - cat -n filename.csv - It concatenates file with line numbers.
  - cat *.csv >> filename.csv - It concatentes and exports to a filename.csv.
  - cat -e filename.csv - It goes to the end of a file.
  
* paste: Join files horizontally.
   - paste filename1.csv filename.csv
 
* less: It shows just one page. Use :n to go to the next file, :p to go back to the previous one and :q to quit.
   - less filename1.txt filename2.txt.

* more: Old way to see the content of a file.
   - more filename.txt 
 
 * head: It shows the first 10 lines.
    - head filename.txt - First 10 lines.
    - head -n 2 filename.txt - First two lines.
 
 * tail: It shows the last 10 lines and it is the opposite of head command.
 
 * cut: It selects columns from a text file.
    - cut -f 2-5,8 -d , filename.csv - Columns 2 to 5 and 8. The flag -d shows the comma separator. It is obligated to inform the fields with the flag -f.

* grep: *general regular expression parser* - It selects lines that contains a text. It accepts REGEX.
    - Common flags: 
    > -c => Print only a count of selected lines. 
    -h => It don´t print the name of files. 
    -i => Not case sensitive. 
    -l => Print only the name of files that contain matches but not the matches. 
    -n => Print line numbers. 
    -v => Only the lines that don't match.
    
    - grep -v word path/filename.csv - It prints line that don't match.
    - grep -n -v word path/filename.csv - It prints lines that don't match and the numbers of the lines.
    - grep i word path/filename1.csv path/filename2.csv - With not sensitive case.
    - grep '[pc]' filename.txt - REGEX
 
* wc: *word count* - It counts the number of characters, words and lines in a file and uses -c, -w and -l.
      - grep word filename.csv : wc -l - It prints the number of the lines that word searched is find.

* sort: 
   - sort filename.csv - Ascending alphabetical order.
   - sort -n filename.csv - Numerically order.
   - sort -n -r filename.csv - Using -r flag reverse order.
   - sort -b -n filename.csv - Ignore branks.
   
* uniq: Remove adjacent duplicates. It is like a group by of any programming language but it is necessary to sort the data before it runs this command.
   - uniq -c filename.csv - Group by unique and count of duplicates.
   - sort | uniq -c

* mkdir - Create a directory
     - mkdir name

## Flags

#### Commands share flags and it is also possible to combine flags.

* -n : Number of lines.
* -R : Recursive.
* -F : Print / after all directories and * after runnable programms.
* -e : Print the end of a file.
* -f : Columns from a text file.
* -d : Separator - ','` ` ';'` ` ':'

## Output command in a file

#### By using the shell commands it is possible to export to a new file:

* `>` - it exports to a file.
   - head -n 5 filename.csv > newfilename.csv - It exports the first five rows to a newfilename.csv
   - `>` newfilename.csv head -n 1 filename.csv - It is other way to export data to newfilename.csv

#### Combine commands using pipe

 * | - The pipe symbol informs the shell to use the left output as input.
   - head filename.csv | tail -n 1 - It shows only the 10th row from filename.csv.

## Print variable's value

* echo: It prints a value or a variable's value. The character $ is used do access the variable.
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
   - var="The date is `date` - It is possible to show commands with backticks(` `)
   - var="The date is $(date)" - This way (with parenthesis) is more modern.
   
* A file.sh can begin with #!/usr/bash in the first line and that code is called shebang. The /usr/bash is the location of Bash.

   - bash script.sh - To run.
   - ./script.sh - If shebang is mentioned in the first line it is possible use ./filename.extension.
   - $@ or $* - For access all arguments.
   - $# - Lenght of arguments.
   - expr 1 + 4 - This expression returns 5. The expr command used only with integer numbers. 
   - echo "5 + 7.5" | bc . The program bc, basic calculator, makes possible to run with decimals. 
   - echo "scale=2; 5/3 " | bc
   
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

* It is possible write the commands learned before inside a script ended by .sh using some editor and run it.
   - bash scripname.sh - It does what is inside the script, can be data manipulations or other.

### Pass filenames to scripts

* Using dollar sign followed by at-sign means that all command-line arguments are given to script.
  - bash scriptname.sh \.- It runs scriptiname for each file.

* Process a single argument using $1, $2 to command-line parameters. It is possible pass n numbers of arguments and the first one it will be filename.
   - cut -d, -f $2 $1 inside the file.sh - Inside file.sh for example.
   - bash file.sh filename.csv number_columns - $1 is number_columns and $2 is the file
   - The shell waits forevers for the argument if it isn't informed.
   
# Download File

### Using Client URL present in UNIX OS.

* Flags 
   - -L Redirect the http url if a 300 error occurs.
   - -C Resume a previous file transfer.

* curl
   - curl -O http://www.anp.gov.br/images/dadosabertos/precos/200[1-9]-1_CA.csv
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
   
 * csvkit - This kit has a lot of tools to manipulate data, it is similar to pandas that is used in Python. For now I often use python but can be a useful tool for some specific cases.
 
 - The tool: https://csvkit.readthedocs.io/en/latest/
 - There are tools to convert csv to other extensions, to manipulate a dataset, to query with sql.

# Automation with Cron - Installed in Linux distribuitions.

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

* Inside of the block and after *do* is possible to run commands learned before, like: head, cut, grep and others. It is possible to do one manipulation by file or merge all files and after do what is necessary.

* Space in the name of the file causes problems
   - head 'file name.csv' - It is one file but without quotation marks bash does not understand like one file.
   - head file name.csv - It will be a problem because file and names.csv are informed like two different files.


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

   Like any other languages but with restrictions, of course, Shell has if statments, loops, functions, arrays, associative arrays(they are equivalent form to dictionaries in python, for example). In fact the Terminal window is useful to solve a variaty of problemns and using Shell language it is possible to do more, but it is better to use it in specic cases when it is easier and more fast than other solutions. I dind't focus in the details about the Shell language and I just learned what was important to solve problems with this different point view. 


Obs:

zip -r arquivo.zip pasta
zip arquivo.zip file.zip

unzip -l arquivo.zip
unzip arquivo.zip

touch arquivo.txt 

tar -vczf teste2.tar.gz teste
tar -vxzf teste2.tar.gz 



