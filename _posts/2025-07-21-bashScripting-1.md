---
layout: post
title: "Bash 1" 
date: 2025-07-21
categories: [blog/bash/]
---
Let's get you started with a comprehensive tutorial on Bash scripting\! Bash is a powerful command processor that runs in a text window, allowing you to automate tasks and interact with your operating system in a highly efficient way.

-----

## Bash Scripting: A Comprehensive Tutorial

Bash (Bourne Again SHell) is the default command-line interpreter on most Linux distributions and macOS. Bash scripting allows you to write sequences of commands that the shell can execute automatically, making it an incredibly powerful tool for automation, system administration, and development workflows.

### What You'll Learn:

1.  **What is Bash Scripting?**
2.  **Your First Bash Script (Hello World\!)**
      * Shebang (`#!/bin/bash`)
      * Executable Permissions (`chmod`)
      * Running a Script
3.  **Comments**
4.  **Variables**
      * Declaring and Using Variables
      * Read-Only Variables
      * Special Variables (e.g., `$0`, `$1`, `$#`, `$?`)
5.  **User Input** (`read`)
6.  **Arithmetic Operations**
      * `expr`
      * `$(( ))`
7.  **Conditional Statements**
      * `if`, `elif`, `else`, `fi`
      * Test Operators (numbers, strings, files)
      * Logical Operators (`-a`, `-o`, `!`)
8.  **Loops**
      * `for` loops
      * `while` loops
      * `until` loops
      * `break` and `continue`
9.  **Functions**
10. **Command Line Arguments**
11. **Piping and Redirection**
      * `|` (Pipe)
      * `>` (Output Redirection)
      * `>>` (Append Output Redirection)
      * `<` (Input Redirection)
      * `2>` (Stderr Redirection)
      * `&>` (Stdout and Stderr Redirection)
12. **Exit Status** (`$?`)
13. **Common Utilities**
      * `echo`
      * `printf`
      * `cut`, `grep`, `sed`, `awk` (brief mention)
      * `find`
      * `xargs`
14. **Debugging Bash Scripts**
15. **Best Practices**

-----

### 1\. What is Bash Scripting?

A Bash script is simply a plain text file containing a series of commands that you would normally type into your terminal, executed sequentially by the Bash interpreter. It allows you to:

  * **Automate repetitive tasks:** Backups, log rotation, file processing.
  * **Create custom commands:** Simplify complex operations.
  * **Chain commands:** Combine multiple utilities into a powerful workflow.
  * **Manage system administration:** User management, service control.

### 2\. Your First Bash Script (Hello World\!)

Let's create the classic "Hello World" script.

1.  **Create a file:** Open your terminal and use `nano` (or `vim`, `code`, etc.) to create a new file.
    ```bash
    nano hello.sh
    ```
2.  **Add the script content:**
    ```bash
    #!/bin/bash
    # This is our first Bash script!
    echo "Hello, Bash Scripting World!"
    ```
3.  **Save and Exit:** (Ctrl+X, Y, Enter for nano)

**Explanation:**

  * `#!/bin/bash`: This is called the **shebang** (or hashbang). It *must* be the very first line of your script. It tells the operating system which interpreter to use to execute the script (in this case, `/bin/bash`).
  * `# This is our first Bash script!`: This is a **comment**. Any line starting with `#` (except the shebang) is ignored by the shell.
  * `echo "Hello, Bash Scripting World!"`: `echo` is a built-in Bash command that prints text to the standard output (your terminal).

**Making it Executable:**

By default, newly created files are not executable. You need to give your script permission to run.

```bash
chmod +x hello.sh
```

  * `chmod`: Change mode (permissions).
  * `+x`: Add executable permission.

**Running the Script:**

Now you can run your script in a few ways:

1.  **Using the path:**
    ```bash
    ./hello.sh
    ```
    The `./` indicates that the script is in the current directory.
2.  **Using the interpreter explicitly (no `chmod +x` needed for this method, but good practice to make it executable):**
    ```bash
    bash hello.sh
    ```

You should see:

```
Hello, Bash Scripting World!
```

### 3\. Comments

As seen above, comments start with a `#`. They are essential for explaining your code, especially in longer or more complex scripts.

```bash
#!/bin/bash

# This script demonstrates comments.
# This line will be ignored by Bash.
echo "Comments make scripts readable." # Inline comment
```

### 4\. Variables

Variables are used to store data in a script.

#### Declaring and Using Variables:

  * **No spaces around the `=` sign when assigning.**
  * Refer to a variable's value using `$` before its name.
  * It's good practice to enclose variable names in curly braces `{}` when used within strings, especially when immediately followed by other characters.

<!-- end list -->

```bash
#!/bin/bash

MY_NAME="Alice"
GREETING="Hello"
AGE=30 # Numbers don't need quotes

echo "$GREETING, $MY_NAME!"
echo "I am $MY_NAME and I am $AGE years old."
echo "The script name is: $0" # Special variable for script name
echo "Today is $(date +%F)" # Command substitution: runs a command and substitutes its output
```

**Output:**

```
Hello, Alice!
I am Alice and I am 30 years old.
The script name is: ./your_script_name.sh
Today is 2025-07-21
```

#### Read-Only Variables:

Use `readonly` to prevent a variable from being changed after it's set.

```bash
#!/bin/bash

PI=3.14159
readonly PI

echo "The value of PI is: $PI"

# PI=3.14 # This line would cause an error: `PI: readonly variable`
```

#### Special Variables:

Bash provides several built-in special variables:

  * `$0`: The name of the script itself.
  * `$1`, `$2`, `$3`, ...: Positional parameters (command-line arguments). `$1` is the first argument, `$2` is the second, etc.
  * `$#`: The number of command-line arguments passed to the script.
  * `$@`: All command-line arguments as separate strings (e.g., "arg1" "arg2"). Best for iterating.
  * `$*`: All command-line arguments as a single string (e.g., "arg1 arg2").
  * `$?`: The exit status of the last executed command (0 for success, non-zero for failure).
  * `$$`: The Process ID (PID) of the current script.
  * `$!`: The PID of the last background command.

### 5\. User Input (`read`)

The `read` command is used to get input from the user.

```bash
#!/bin/bash

echo "What is your name?"
read USER_NAME
echo "Hello, $USER_NAME! Nice to meet you."

echo "Enter your age: "
read AGE
if [ "$AGE" -lt 18 ]; then # Using conditional check here
  echo "You are a minor."
else
  echo "You are an adult."
fi
```

### 6\. Arithmetic Operations

Bash can perform arithmetic calculations.

  * **`expr`:** Older, more limited. Requires spaces around operators.
  * **`$(( ))`:** Preferred, more powerful, allows standard arithmetic operators.

<!-- end list -->

```bash
#!/bin/bash

NUM1=10
NUM2=5

# Using expr (note spaces and escaping multiplication)
SUM_EXPR=$(expr $NUM1 + $NUM2)
PRODUCT_EXPR=$(expr $NUM1 \* $NUM2) # Need to escape *

echo "Using expr:"
echo "Sum: $SUM_EXPR"
echo "Product: $PRODUCT_EXPR"

# Using $(( )) (preferred)
SUM=$(( NUM1 + NUM2 ))
DIFFERENCE=$(( NUM1 - NUM2 ))
PRODUCT=$(( NUM1 * NUM2 ))
QUOTIENT=$(( NUM1 / NUM2 ))
REMAINDER=$(( NUM1 % NUM2 ))

echo ""
echo "Using \$(( ))"
echo "Sum: $SUM"
echo "Difference: $DIFFERENCE"
echo "Product: $PRODUCT"
echo "Quotient: $QUOTIENT"
echo "Remainder: $REMAINDER"

# Increment/Decrement
COUNT=1
echo "Initial count: $COUNT"
COUNT=$(( COUNT + 1 )) # Increment
echo "Count after increment: $COUNT"
((COUNT++)) # Shorthand increment
echo "Count after shorthand increment: $COUNT"
```

### 7\. Conditional Statements (`if`)

`if` statements execute code blocks based on conditions.

```bash
#!/bin/bash

read -p "Enter a number: " NUMBER

if [ "$NUMBER" -gt 10 ]; then
  echo "$NUMBER is greater than 10."
elif [ "$NUMBER" -eq 10 ]; then
  echo "$NUMBER is equal to 10."
else
  echo "$NUMBER is less than 10."
fi

# Example with string comparison
NAME="Bash"
if [ "$NAME" == "Bash" ]; then
  echo "Welcome, Bash user!"
fi

# Check if a file exists
FILE="non_existent_file.txt"
if [ -f "$FILE" ]; then
  echo "$FILE exists."
else
  echo "$FILE does not exist."
fi

# Logical Operators
read -p "Enter your age: " AGE
read -p "Are you a student? (yes/no): " IS_STUDENT

# -a for AND, -o for OR
if [ "$AGE" -ge 18 -a "$IS_STUDENT" == "yes" ]; then
  echo "You are an adult student."
elif [ "$AGE" -lt 18 -o "$IS_STUDENT" == "no" ]; then
  echo "You are either a minor OR not a student (or both)."
else
  echo "You are an adult but not a student."
fi
```

**Test Operators (Common ones in `[ ]` or `[[ ]]`):**

  * **Numbers:**
      * `-eq`: is equal to
      * `-ne`: is not equal to
      * `-gt`: is greater than
      * `-ge`: is greater than or equal to
      * `-lt`: is less than
      * `-le`: is less than or equal to
  * **Strings:**
      * `==`: is equal to
      * `!=`: is not equal to
      * `<`: less than (alphabetically)
      * `>`: greater than (alphabetically)
      * `-z`: string is zero length (empty)
      * `-n`: string is non-zero length (not empty)
  * **Files:**
      * `-f`: file exists and is a regular file
      * `-d`: file exists and is a directory
      * `-e`: file exists (regardless of type)
      * `-r`: file is readable
      * `-w`: file is writable
      * `-x`: file is executable

### 8\. Loops

Loops allow you to execute a block of code multiple times.

#### `for` loops:

Iterate over a list of items.

```bash
#!/bin/bash

# Iterate over a list of strings
for FRUIT in Apple Banana Orange; do
  echo "I like $FRUIT."
done

echo ""

# Iterate over numbers (C-style for loop)
for (( i=1; i<=5; i++ )); do
  echo "Count: $i"
done

echo ""

# Iterate over command output
for FILE in $(ls *.sh); do # finds all .sh files in current directory
  echo "Processing script: $FILE"
done
```

#### `while` loops:

Execute commands as long as a condition is true.

```bash
#!/bin/bash

COUNT=1
while [ $COUNT -le 5 ]; do
  echo "Loop count: $COUNT"
  COUNT=$(( COUNT + 1 )) # Increment the counter
done
```

#### `until` loops:

Execute commands as long as a condition is false.

```bash
#!/bin/bash

COUNT=5
until [ $COUNT -lt 1 ]; do # Loop until COUNT is less than 1
  echo "Counting down: $COUNT"
  COUNT=$(( COUNT - 1 ))
done
```

#### `break` and `continue`:

  * `break`: Exits the loop immediately.
  * `continue`: Skips the current iteration and moves to the next.

<!-- end list -->

```bash
#!/bin/bash

for i in 1 2 3 4 5 6 7 8 9 10; do
  if [ $((i % 2)) -eq 0 ]; then
    continue # Skip even numbers
  fi
  echo "Odd number: $i"

  if [ $i -eq 7 ]; then
    echo "Reached 7, breaking loop."
    break # Stop at 7
  fi
done
```

### 9\. Functions

Functions allow you to group reusable blocks of code.

```bash
#!/bin/bash

# Function definition
greet_user() {
  echo "Hello, $1!" # $1 refers to the first argument passed to the function
  echo "You are running the greet_user function."
}

# Function with a return value (exit status)
add_numbers() {
  SUM=$(( $1 + $2 ))
  echo "The sum is: $SUM"
  return 0 # 0 for success, non-zero for error
}

# Call the functions
greet_user "Alice"
greet_user "Bob"

echo ""

add_numbers 10 20
STATUS=$? # Capture the return status
echo "Function status: $STATUS"

add_numbers 5 7
```

### 10\. Command Line Arguments

As mentioned with special variables (`$1`, `$2`, `$#`, `$@`).

```bash
#!/bin/bash

echo "Script name: $0"
echo "Number of arguments: $#"

if [ "$#" -eq 0 ]; then
  echo "No arguments provided."
else
  echo "All arguments: $@" # Best for iterating: "arg1" "arg2"
  echo "First argument: $1"
  echo "Second argument: $2"

  echo "Iterating through arguments:"
  for ARG in "$@"; do
    echo "  Argument: $ARG"
  done
fi
```

**Run example:** `./your_script.sh file1.txt hello 123`

### 11\. Piping and Redirection

Powerful features for directing input/output of commands.

  * **`|` (Pipe):** Sends the `stdout` (standard output) of one command as the `stdin` (standard input) to another command.

    ```bash
    ls -l | grep "myfile" # List files, then filter for lines containing "myfile"
    cat /etc/passwd | cut -d ':' -f 1 # Get usernames from passwd file
    ```

  * **`>` (Output Redirection):** Redirects `stdout` to a file. **Overwrites** the file if it exists.

    ```bash
    echo "This will be written to file.txt" > file.txt
    ls -l > file_list.txt # Saves the output of ls -l to file_list.txt
    ```

  * **`>>` (Append Output Redirection):** Redirects `stdout` to a file, **appending** to it if it exists.

    ```bash
    echo "This is the first line." > log.txt
    echo "This is the second line." >> log.txt # Appends to log.txt
    ```

  * **`<` (Input Redirection):** Redirects the content of a file as `stdin` to a command.

    ```bash
    # Instead of typing input, command reads from input.txt
    wc -l < input.txt # Counts lines in input.txt
    ```

  * **`2>` (Stderr Redirection):** Redirects `stderr` (standard error) to a file.

    ```bash
    # Attempt to list a non-existent directory and capture the error
    ls -l /non_existent_dir 2> error.log
    ```

  * **`&>` (Stdout and Stderr Redirection):** Redirects both `stdout` and `stderr` to the same file.

    ```bash
    # Capture both regular output and errors
    ls -l /home /non_existent_dir &> combined_output.log
    ```

### 12\. Exit Status (`$?`)

Every command and script returns an exit status (or exit code).

  * `0`: Indicates success.
  * Non-zero (typically 1-255): Indicates an error or failure.

You can use `$?` to check the status of the last command.

```bash
#!/bin/bash

ls /etc/hosts # This should succeed
if [ $? -eq 0 ]; then
  echo "Successfully listed /etc/hosts"
else
  echo "Failed to list /etc/hosts"
fi

ls /non_existent_path # This should fail
if [ $? -ne 0 ]; then
  echo "As expected, /non_existent_path failed to list."
fi
```

### 13\. Common Utilities (Brief Mention)

Bash scripts often orchestrate other command-line tools.

  * **`echo` / `printf`:** For printing output. `printf` offers more formatting control.
  * **Text Processing:**
      * **`grep`:** Filters lines matching a pattern.
      * **`cut`:** Extracts columns/fields from lines.
      * **`sed`:** Stream editor for text transformations (find and replace).
      * **`awk`:** Powerful text processing language, excels at column-based data.
  * **`find`:** Searches for files and directories based on various criteria.
  * **`xargs`:** Builds and executes command lines from standard input. Useful for piping output of `find` to other commands.
  * **`sort`, `uniq`, `wc` (word count):** Basic data manipulation.
  * **`curl` / `wget`:** For making web requests.

### 14\. Debugging Bash Scripts

Debugging is crucial for finding errors.

  * **`set -x`:** Prints each command and its arguments as they are executed. Place at the top of your script or before a problematic section.
    ```bash
    #!/bin/bash
    set -x # Turn on debugging

    echo "Starting script..."
    MY_VAR="test"
    echo "My variable is: $MY_VAR"
    ls /no_such_dir
    echo "Script finished."
    ```
  * **`set -e`:** Exits immediately if any command fails (returns non-zero exit status). Useful for preventing scripts from continuing after an error.
    ```bash
    #!/bin/bash
    set -e # Exit on first error

    echo "This will run."
    ls /etc/hosts # This succeeds
    ls /no_such_dir # This will cause the script to exit here
    echo "This will NOT run if the previous command fails."
    ```
  * **Linting:** Use shell script linters like `shellcheck` (installable via package manager) to identify common errors and bad practices.

### 15\. Best Practices

  * **Always include the Shebang:** `#!/bin/bash`
  * **Use Comments:** Explain complex logic or non-obvious commands.
  * **Use Double Quotes for Variables:** `echo "$MY_VAR"` prevents issues with spaces or special characters in variable values.
  * **Be Mindful of Paths:** Use absolute paths (`/home/user/script.sh`) or `dirname $0` for robust scripts.
  * **Check Exit Status:** Use `if [ $? -ne 0 ]` or `set -e` for error handling.
  * **Validate Input:** If taking user input or arguments, validate them.
  * **Use Functions for Reusability:** Break down complex scripts into smaller, manageable functions.
  * **Avoid Parsing `ls` output:** It's generally unreliable. Use `find` or globbing instead (`for file in *.txt`).
  * **Start Simple:** Build your scripts incrementally, testing each piece.

-----

This comprehensive tutorial gives you a strong foundation in Bash scripting. The best way to learn is by doing: start writing simple scripts, automate your daily tasks, and gradually explore more complex concepts and utilities\!