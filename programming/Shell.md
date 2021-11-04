# Shell basics

- can be executed in the terminal or in a script

#### File/folder operations:

- cat - prints files
- ls - list directory content
- mkdir - makes folder
- cp - copy
- mv - move
- rm - remove
  - rm -rf for folders - careful!
- cd - move to location
- pwd - present working directory
- find -name “name.txt”
- touch - creates a file
- grep - search for patterns
- chmod - file permissions
- alias - assign alias to command
- | - pipe, pass the output of one command into another

#### Scripting:

- ```shell
  #!/usr/bin/env bash
  ```

- variable=“Some string”

- echo - prints output

- $ will refer to the variable value, e.g.

  - ```shell
    echo $Variable
    echo ${Variable/Some/A} # will replace Some with A
    echo ${Variable:0:7} # return up to 7 chars
    echo ${#Variable} # string length
    ```

- arrays are declared similarly

  - array=(one,two)

- read - reading a value from input

  