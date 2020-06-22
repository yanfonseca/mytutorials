# Introduction to Shell

This content is a brief way to learn and review some basic and expert commands to make your daily data manipulation easier and productive.

## Special characters
* ..    : The directory above the one you are.
* .     : Current directory
* ~     : Home directory // COMO ALTERAR O HOME DIRECTORY?

## Commands

* pwd   : *print working directory* - Shows where you are in the filesystem.

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
  
* less: Show just one page. Use :n to go to the next file, :p to go back to the previous one and :q to quit.
    - less filename1.txt filename2.txt
* more: Old way to see the content of a file
 - more filename.txt 
 
 * head: Shows the first 10 lines.
    - head filename.txt - First 10 lines.
    - head -n 2 filename.txt - First two lines.
 
* mkdir - Create a directory
    - mkdir name
