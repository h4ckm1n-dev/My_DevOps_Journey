# Bash Scripting Tutorial

Bash (Bourne Again Shell) is a popular command-line shell and scripting language on various operating systems, including Linux and macOS. This tutorial provides a quick guide for various Bash concepts, syntax, and useful commands, complete with examples.

## Shebang and Execution

Every Bash script starts with a shebang (`#!/bin/bash`) to specify the Bash interpreter. The script can be made executable using `chmod +x script.sh`, and executed with `./script.sh`.

Example:

```bash
#!/bin/bash
echo "Hello, World!"
```

Save this to a file, make it executable, and run it. It should print "Hello, World!" to the terminal.

## Variables

Variables in Bash are created with `variable="value"` and their values are accessed with `$variable`. You can declare a variable as read-only with `readonly variable`, or delete it with `unset variable`.

Example:

```bash
#!/bin/bash
name="Alice"
echo "Hello, $name"
```

## Input/Output

The `read` command reads input and assigns it to a variable. You can redirect output to a file with `>` (overwrite) or `>>` (append), and discard output with `command > /dev/null 2>&1`.

Example:

```bash
#!/bin/bash
echo "Enter your name:"
read name
echo "Hello, $name"
```

## Arithmetic Operations

You can perform arithmetic operations with `expr`, `$((expression))`, or `let`.

Example:

```bash
#!/bin/bash
a=10
b=20
sum=$((a + b))
echo "Sum: $sum"
```

## String Manipulation

You can assign strings to variables, get their lengths, extract substrings, and replace substrings.

Example:

```bash
#!/bin/bash
str="Hello, World!"
length=${#str}
echo "Length of string: $length"
```

## Conditional Statements

Bash supports `if`, `if-else`, and `if-elif-else` statements, as well as the `case` statement.

Example:

```bash
#!/bin/bash
echo "Enter a number:"
read num
if [[ $num -gt 0 ]]; then
  echo "Positive number."
else
  echo "Non-positive number."
fi
```

## Looping Constructs

You can use `for` loops, `while` loops, and `until` loops in Bash, and control loop execution with `break` and `continue`.

Example:

```bash
#!/bin/bash
for ((i=0; i<5; i++)); do
  echo "This is iteration $i"
done
```

## Functions

Functions in Bash can be defined with `function_name() { commands }`, and called with `function_name arguments`.

Example:

```bash
#!/bin/bash
greet() {
  echo "Hello, $1"
}
greet "World"
```

## Arrays

Bash also supports arrays.

Example:

```bash
#!/bin/bash
fruits=("apple" "banana" "cherry")
echo "I like ${fruits[1]}s."
```

## Exit Status

The `$?` variable holds the exit status of the last command. You can also chain commands together with `&&` (run second command if first succeeds) or `||` (run second command if first fails).

Example:

```bash
#!/bin/bash
ls /nonexistentdirectory || echo "Directory does not exist."
```

## File Operations

Bash has commands for creating, copying, moving, and deleting files and directories.

Example:

```bash
#!/bin/bash
mkdir newdir
touch newdir/newfile.txt
echo "File created."
```

## Command-Line Arguments

Scripts can accept command-line arguments, accessible through `$0`, `$1`, etc. The `$#` variable holds the number of arguments, and `$@` and `$*` hold all arguments.

Example:

```bash
#!/bin/bash
echo "Script name: $0"
echo "First argument: $1"
echo "Second argument: $2"
echo "All arguments: $@"
```

## Error Handling

Bash scripts can handle errors and exit when a command fails.

Example:

```bash
#!/bin/bash
set -e
nonexistentcommand
echo "This will not print."
```



# Advanced Bash Scripting Tutorial

## Parameter Expansions

Bash provides powerful parameter expansion capabilities. For example, string manipulation, array slicing, substitution, and default values.

Example:

```bash
#!/bin/bash
str="Hello, World!"
lowercase=${str,,}
echo "Lowercase string: $lowercase"
```

## Process Substitution

Bash allows you to use the output of a command as an input file for another command using `<(command)`. Similarly, `>(command)` can be used to send the output of a command to another command.

Example:

```bash
#!/bin/bash
diff <(ls /dir1) <(ls /dir2)
```

## Trap Command

The `trap` command allows you to catch signals and execute code when they occur. This is useful for cleanup tasks.

Example:

```bash
#!/bin/bash
cleanup() {
  echo "Cleaning up..."
  rm temp_file
}
trap cleanup EXIT
touch temp_file
```

## Here Documents

A "here document" allows you to use input redirection to supply a command with multiple lines of input.

Example:

```bash
#!/bin/bash
cat << EOF
This is a here document.
It can span multiple lines.
EOF
```

## Regular Expressions

Bash provides regular expression matching with `[[ string =~ regex ]]`.

Example:

```bash
#!/bin/bash
read -p "Enter a date (YYYY-MM-DD): " date
if [[ $date =~ ^[0-9]{4}-[0-9]{2}-[0-9]{2}$ ]]; then
  echo "Valid date."
else
  echo "Invalid date."
fi
```

## Associative Arrays

Bash supports associative arrays (since version 4.0).

Example:

```bash
#!/bin/bash
declare -A animals
animals["cow"]="moo"
animals["cat"]="meow"
echo "A cow goes ${animals[cow]}"
```

## Debugging

Bash scripts can be debugged by running them with `bash -x`.

Example:

```bash
#!/bin/bash
for ((i=1; i<=3; i++)); do
  echo "Iteration $i"
done
```

Run with: `bash -x script.sh`.

## Multithreading

Bash can execute commands in the background using `&`, and wait for all background jobs to finish with `wait`.

Example:

```bash
#!/bash/bin
echo "Long running process started."
sleep 10 &
pid=$!
echo "Doing other stuff."
wait $pid
echo "Long running process finished."
```

## Interacting with the Filesystem

Bash scripts can check for file types, read files line by line, and check if files or directories exist.

Example:

```bash
#!/bin/bash
if [[ -d "/path/to/dir" ]]; then
  echo "Directory exists."
else
  echo "Directory does not exist."
fi
```

These advanced concepts should allow you to write more complex and robust Bash scripts. Remember, the best way to learn is to experiment and practice. Happy scripting!



# Bash Scripting

Bash (Bourne Again Shell) is a prevalent command-line shell and scripting language in Linux and macOS. This enhanced cheat-sheet provides a guide with examples for various concepts, syntax, and useful commands in Bash scripting.

## Shebang and Execution

COMMAND | DESCRIPTION | EXAMPLE
---|---|---
`#!/bin/bash` | Shebang to specify the Bash interpreter | `#!/bin/bash` at the beginning of a script file
`chmod +x script.sh` | Make the script executable | `chmod +x myscript.sh`
`./script.sh` | Execute the script | `./myscript.sh`

## Variables

COMMAND | DESCRIPTION | EXAMPLE
---|---|---
`variable="value"` | Create a variable and assign a value | `greeting="Hello, world"`
`echo $variable` | Print the value of a variable | `echo $greeting`
`readonly variable` | Declare a read-only (constant) variable | `readonly pi=3.14159`
`unset variable` | Unset (delete) a variable | `unset greeting`

## Input/Output

COMMAND | DESCRIPTION | EXAMPLE
---|---|---
`read variable` | Read input and assign it to a variable | `read name`
`echo "text" > file.txt` | Redirect output to a file (overwrite) | `echo "Hello" > hello.txt`
`echo "text" >> file.txt` | Redirect output to a file (append) | `echo "World" >> hello.txt`
`command > /dev/null 2>&1` | Discard both stdout and stderr | `find / -name "myfile" > /dev/null 2>&1`

## Arithmetic Operations

COMMAND | DESCRIPTION | EXAMPLE
---|---|---
`expr 2 + 2` | Perform arithmetic operations | `expr 2 + 2`
`$((2 + 2))` | Perform arithmetic operations (alternative) | `echo $((2 + 2))`
`$[2 + 2]` | Perform arithmetic operations (alternative) | `echo $[2 + 2]`
`let "variable = 2 + 2"` | Perform arithmetic operations and assign the result | `let "sum = 2 + 2"`

## String Manipulation

COMMAND | DESCRIPTION | EXAMPLE
---|---|---
`variable="Hello World"` | Assign a string to a variable | `greeting="Hello World"`
`${#variable}` | Get the length of a string | `echo ${#greeting}`
`${variable:2:4}` | Extract a substring | `echo ${greeting:2:4}`
`${variable//o/O}` | Replace all occurrences of a substring | `echo ${greeting//o/O}`
`${variable/#Hello/Hi}` | Replace a substring at the beginning | `echo ${greeting/#Hello/Hi}`
`${variable/%World/Universe}` | Replace a substring at the end | `echo ${greeting/%World/Universe}`

## Conditional Statements

COMMAND | DESCRIPTION | EXAMPLE
---|---|---
`if condition; then ... fi` | If statement | `if [ $num -gt 10 ]; then echo "Yes"; fi`
`if condition; then ... else ... fi` | If-else statement | `if [ $num -gt 10 ]; then echo "Yes"; else echo "No"; fi`
`if condition; then ... elif condition; then ... else ... fi` | If-elif-else statement | `if [ $num -gt 10 ]; then echo "Big"; elif [ $num -eq 10 ]; then echo "Equal"; else echo "Small"; fi`
`[[ condition ]]` | Extended test command (preferred) | `if [[ $num -gt 10 ]]; then echo "Yes"; fi`
`[ condition ]` | Test command (alternative) | `if [ $num -gt 10 ]; then echo "Yes"; fi`
`case "$variable" in pattern) ... ;; esac` | Case statement | `case "$input" in 1) echo "One";; 2) echo "Two";; esac`

## Looping Constructs

COMMAND | DESCRIPTION | EXAMPLE
---|---|---
`for item in list; do ... done` | For loop | `for i in 1 2 3; do echo $i; done`
`for ((i=0; i<5; i++)); do ... done` | C-style for loop | `for ((i=0; i<5; i++)); do echo $i; done`
`while condition; do ... done` | While loop | `while [ $i -lt 5 ]; do echo $i; i=$((i+1)); done`
`until condition; do ... done` | Until loop | `until [ $i -ge 5 ]; do echo $i; i=$((i+1)); done`
`break` | Exit the innermost loop | `for ((i=0; i<5; i++)); do if [ $i -eq 3 ]; then break; fi; echo $i; done`
`continue` | Skip the current iteration | `for ((i=0; i<5; i++)); do if [ $i -eq 3 ]; then continue; fi; echo $i; done`

## Functions

COMMAND | DESCRIPTION | EXAMPLE
---|---|---
`function_name() { ... }` | Define a function | `greet() { echo "Hello, $1"; }`
`function_name() command` | Define a single-line function | `greet() echo "Hello, $1"`
`function_name argument` | Call a function | `greet "World"`
`$1`, `$2`, ... | Access function arguments | `echo "First arg: $1; Second arg: $2"`

## Arrays

COMMAND | DESCRIPTION | EXAMPLE
---|---|---
`array=("item1" "item2" "item3")` | Create an array | `fruits=("Apple" "Banana" "Cherry")`
`${array[0]}` | Access array element at index 0 | `echo ${fruits[0]}`
`${array[@]}` | Access all array elements | `echo ${fruits[@]}`
`${#array[@]}` | Get the length of an array | `echo ${#fruits[@]}`
`array+=(new_item)` | Append an item to the array | `fruits+=("Dragonfruit")`
`unset array[1]` | Remove an element from the array | `unset fruits[1]`
`unset array` | Delete the entire array | `unset fruits`

## Exit Status

COMMAND | DESCRIPTION | EXAMPLE
---|---|---
`$?` | Get the exit status of the last command | `echo $?`
`command || echo "Failed"` | Execute the second command only if the first fails | `ls /nonexistent_dir || echo "Failed"`
`command && echo "Succeeded"` | Execute the second command only if the first succeeds | `ls /home && echo "Succeeded"`

## File Operations

COMMAND | DESCRIPTION | EXAMPLE
---|---|---
`touch file.txt` | Create an empty file | `touch newfile.txt`
`cp file.txt newfile.txt` | Copy a file | `cp original.txt copy.txt`
`mv file.txt newdir/file.txt` | Move/Rename a file | `mv oldfile.txt newdir/newfile.txt`
`rm file.txt` | Remove a file | `rm unwantedfile.txt`
`mkdir directory` | Create a directory | `mkdir new_directory`
`rmdir directory` | Remove an empty directory | `rmdir empty_directory`
`ls`, `ls -l`, `ls -a` | List files and directories | `ls -l /home`

## Command-Line Arguments

COMMAND | DESCRIPTION | EXAMPLE
---|---|---
`$0` | Name of the script | `echo "Script name: $0"`
`$1`, `$2`, ... | Command-line arguments | `echo "First argument: $1"`
`$#` | Number of command-line arguments | `echo "Number of arguments: $#"`
`$*` | All command-line arguments as a single string | `echo "All args: $*"`
`$@` | All command-line arguments as separate strings | `echo "All args separately: $@"`

## Error Handling

COMMAND | DESCRIPTION | EXAMPLE
---|---|---
`command || exit 1` | Exit if the command fails | `ls /nonexistent_dir || exit 1`
`set -e` | Exit immediately if any command fails | `set -e; ls /nonexistent_dir; echo "This will not print"`
`set -o pipefail` | Return the exit status of the last command in a pipeline | `set -o pipefail; ls | grep nonexistent_dir`

## Miscellaneous

COMMAND | DESCRIPTION | EXAMPLE
---|---|---
`alias name="command"` | Create an alias for a command | `alias ll="ls -l"`
`source script.sh` or `. script.sh` | Execute a script in the current shell environment | `source myscript.sh`
`man command` | Display the manual page for a command | `man ls`
`Ctrl+C` | Terminate the currently running command | `[Keyboard input] Ctrl+C`
`Ctrl+Z` | Suspend the currently running command | `[Keyboard input] Ctrl+Z`
