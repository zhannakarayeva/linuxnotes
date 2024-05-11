# sed command
- This command is used for manipulating the text files. It works by processing the stream of text line by lnie, and allows users to edit text in each line. 
    * `In Place Editing`: By default, sed modifies the original file, unless you specify otherwise. 
    * `Non-Interactive`: Sed operates through commands without user interaction within the script. 
    * `Line-oriented`: Sed edits text one line at a time, making it efficient for handling large files. 

-`SYNTAX`
```bash
sed 'operator/pattern/replacement/flags' filename
```
* `operator`: Decides what we are going to do with mathced 
pattern. 
* `pattern`: The text you want to find. 
* `replacement`: The text you want to replace the pattern with.
* `flags`:(optional): Controlling how the change is going to happen

1. `Substitution`
- `sed 's/pattern/replacement/flags`
    * `g` flag: Will change the all occurences in the line, rather than changing first occurence in all the lines. 
`sed 's/pattern/replacement/' filename`
2. `Deletion`
-  `sed 'd/info/' filename`
- Deletes the all the lines containing `pattern`.

3. `Insertion`:
- Insert a line of text before the matching line. 
`sed '/pattern/i\newtext' filename`
`sed '/ERROR/i\!!! CAUTION !!!'  servicelogs.log`
4. `Appending`
- Appends a line of text after the matching line. 
`sed 'a\newtext' /pattern/ filename`

**NOTE**: `sed` command by default will not save the changes in the file. 
We could use `-i` option to save our changes in the file. 
Such as:
```bash
sed -i 'opr/pattern/repl./flags' filename

```

* `-e` option
- Allows mutliple sed changes in the file. 
```bash
sed -e 'opr/pattern/repl./flags/' -e 'd/pattern' filename
```
* `sed 'a ERROR HAPPENED' /ERROR/  servicelogs.log`
- ` ERROR HAPPENED` will be added after each line that contains `ERROR.  

# AWK
- It is a powerfult programming language fro pattern scanning and processing. It's particularly usef for text processing, and it is commonly used in UNIX like system for data extraction and reporting. 
* `SYNTAX`
```bash
awk [options] 'pattern {action}' filename
```
- The `pattern` specifies when the action should be performed. If the `pattern` is omitted, the action is performed on every line. 
**NOTE**: This `pattern` could also be a condition.

1. **Common Options**
- `-F`: Specifies the input field separator. Default is whitespace. 
- `-v`: Assign a value to variable. 
- `-f`: Specifies the file containing awk script. 

2. **Basic Actions**
- `print`: Prints the contents of the input. `print $0` prints the entire line. `print $1` prints the first field. 
- `if (condition) action`: It will execute the action on the line if the condition is true. 
- `BEGIN`: Actions inside this block will be executed before any of the lines read.
- `END`: After all the lines are executed, then the action in this block will be executed. 

- 
```
For variables we have post and preincrement. These operators increases the value of numerical variables by 1. 
if the `count` var. is equal to 1, `count++` will make that 
2 in the next usage. 
if the `count` var. is equal to 1, `++count` will make that 2 in the current usage. 
```
`Assume the count is 0`
```awk
{print ++count} -> 1
{print count} -> 1
```
`Assume the count is 0`
```awk
{print count++} -> 0
{print count} -> 1
```

# print the employees with more than avg. exp. 
**NOTE!** To eliminate the first line you can use
`NR`. Which stands for number of records, and by using this we could start
the file from any line we would like. 
`NR == 1` will only read first line. 
`NR > 1` will read lines after first line.
`NR < 10` will read lines before line 10. 
# Find the average experience of this employees. 
```bash
awk -F, 'BEGIN {sum = 0; count = 0} NR > 1 {count++; sum+= $3} END {avg=sum/count; print avg}' devops.csv
```
# print the employees with more than avg. exp
```bash
# For now let's just assume we know the average
awk -F, '$3 > avg {print $1}' devops.csv
```
**NOTE** We could use `system()` command to execute awk command inside another awk. 
`awk -F, 'BEGIN {sum = 0; count = 0} NR > 1 {count++; sum+= $3} END {avg=sum/count; print avg; system("awk -F, '$3 >" avg "{print $1}' devops.csv")}' devops.csv
`
**NOTE** When using inner awk scripts with functions like `system`. 
Use `\047` instead of `'`.