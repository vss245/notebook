# MATLAB

Language created for scientific computing and visualization

#### Syntax:

- variables don’t need to be declared with type
  - x = 3;
  - str = ‘my string’;
- semicolon terminates output into the command window
- file commands:
  - dir (lists of files)
  - cd (current directory)
  - path
  - pwd (present working directory)
- to add packages, the folder should be added in the “set path” window
- command line stuff:
  - clear all, clc, ans (most recent answer), whos (current variables, verbose)
- every script is an .m file
  - functions can also be saved as .m files and run from scripts
- variables can be saved into .mat files
- loops terminated with “end”

#### Data types:

- numbers: int (8, 16, 32, 64), single, double
- array-like: array (vector/matrix), struct (similar to a dict), cell array
- strings: string, char
- methods for conversion: int2str, num2str, str2double etc
- methods for type: is(), iscell(), ischar(), islogical()

#### Vectors:

- **indexing starts with 1!**

- ```matlab
  row_vect = [7 8 9 10 11]
  ```

- ```matlab
  col_vect = [7;  8;  9;  10; 11]
  ```

- slicing: row_vect(2:3) = [8 9 10]
- Useful functions: dot, ones (array of 1), zeros (array of 0), 

#### Matrices:

- ```matlab
  a = [ 1 2 3 4 5; 2 3 4 5 6; 3 4 5 6 7; 4 5 6 7 8];
  v = a(:,4)
  ```
  - : will take all the elements in the row/column
  - deleting elements: a[1] = []
  - transposing: A = A’;
  - useful functions: det, eig (eigenvalues), svd (singular value decomposition), eye (identity matrix), rand (random uniformly distributed values between 0 and 1), cat (concatenate), diag (diagonal), reshape

#### Operators:

- arithmetic operators are the usual (+,-,/)
- adding a dot performs an elementwise operation (e.g. A./B)
- matrix division: \
- transpose: ’
- logical: &, | (or), ^ (xor)

#### Conditionals:

```matlab
if a == b
	a = a+3
elseif a == c
 a = a+2
else
 continue
end
```

#### Plotting:

- figure - creates a figure
- plot(x,y) - also plot3, semilogy, mesh and others
- functions to modify plot: xlabel, ylabel, title, grid on, hold on (for multiple plots on one graph)
- subplot(m,n,p) makes plot at row and column m and n out of p plots
- axis([0 1 ]) sets axis scale

#### Functions:

- can be defined at the end of a script, in a separate .m file or anonymously

- anonymous functions: @(arg) expression

  - ```matlab
    power = @(x, n) x.^n;
    ```

- functions can be nested in other functions
- if you create a subfolder named private, functions in there will be only visible to functions in the parent folder

#### Math:

- solve() can solve algebraic equations

  - ```matlab
    solve('v-u-3*t^2=0', 'v')
    ```

- same with systems of equations

- expand and collect can expact or reduce equations

- calculus: limit(), diff(), dsolve() - for differential equations, int(f) for integration

#### Other useful things:

- parfor can be used to parallelize loops
- tic and toc are used to time code
- help to display method documentation
- input() to prompt user for input