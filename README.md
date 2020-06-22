# Introduction to Shell

This content is a brief way to learn and review some basic and expert commands to make your daily data manipulation easier and productive.

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
    - grep -v word path/filename.csv - Print line that don't match
    - grep -n -v word path/filename.csv - Print line that don't match and the number of the line.
    - grep i word path/filename1.csv path/filename2.csv - Print the count of matching lines.
 
* mkdir - Create a directory
     - mkdir name

* wc: *word count* - Count number of characters, words and line in a file and uses -c, -w and -l. 
      - grep word filename.csv : wc -l - Prints the number os lines that word seached shows.

* sort: 
   - sort filename.csv - Ascending alphabetical order.
   - sort -n filename.csv - Numerically order
   - sort -n -r filename.csv - Using -r flag reverse order
   - sort -b -n filename.csv - Ignore branks
   
* uniq: Remove adjacent duplicates. To be like group by of any language has to sort the data before.
   - uniq -c filename.csv - Groupby unique and count of duplicates
   
#### Flags

* -n : Number of lines.
* -R : Recursive
* -F : Print / after all directories and * after runnable programms.
* -e : Print the end of a file.
* -f : Columns from a text file
* -d : Separator - ','` ` ';'` ` ':'

###### It is possible to combine flags.

#Output command in a file

##By using the shell comands it is possible to export to a new file:

* > : Export to a csv file
      - head -n 5 filename.csv > newfilename.csv - Exports the first five rows to a newfilename.csv.
      - > newfilename.csv head -n 1 filename.csv - It is other way to export data to newfilename.csv
## Combine commands using pipe

 * | - Pipe symbol inform the shell to use the left output as input
     - head filename.csv | tail -n 1




