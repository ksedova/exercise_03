rm(list=ls())

setwd('D:/university/Amasters/firstsemester/PRG/exercise_03')

# Computational Complexity

## Computational Complexity
### Task 1
* Calculate the computational complexity of this code segment.

```
1   for r ← 1 to m
2     for s ← 1 to n
3       count ← 0
4       for t ← 1 to k
5         if seq(r, s) = bases(t)
6           count ← count + 1
7       if count = 0
8         bases(k + 1) ← seq(r, s)
9         k ← k + 1
```

## Selection Sort
The following algorithm, called Selection Sort, is a naive but simple iterative 
method to solve the sorting problem. First, Selection sort finds the
smallest element in the list of integers, and moves it to the first position by swapping it with
whatever happens to be in the first position. Next, Selection sort
finds the second-smallest element in the list, and moves it to the second position,
again by swapping with value in the second position. At the *i*<sup>th</sup> iteration, Selection sort finds the *i*<sup>th</sup>
smallest element in the list, and moves it to the *i*<sup>th</sup> position.

### Task 2
* In R, implement the function `IndexOfMin()` according to the following pseudocode.

* Input:
    * a list of integers
    * an index of the first position
    * an index of the last position

* Output:
    * an index of the smallest element of the list between the first and last index

* Estimate the number of operations of this function, i.e., the computational complexity, depending on the input size. 

```
IndexOfMin(array, first, last)
1   index ← first
2   for k ← first + 1 to last
3     if array[k] < array[index]
4       index ← k
5   return index
```
IndexOfMin <- function(array, first, last) {
  index <- first
  for (k in (first + 1):last) {
    if (array[k] < array[index]) {
      index <- k
    }
  }
  
  return(index)
}

# --- Test ---
arr <- c(7, 3, 9, 1, 5, 10, 15, 2, 8, 7, 16)
IndexOfMin(arr, 5, length(arr))
# Očekávaný výstup: 4 (protože 1 je nejmenší a je na 4. pozici)



### Task 3 
* In R, implement the function `SelectionSort()` according to the following pseudocode.

* Input:
    * a list of integers
    * a count of integers in the list

* Output:
    * a sorted list of integers

* Estimate the number of operations of this function, i.e., the computational complexity, depending on the input size.
* Determine the *O* notation.

```
SelectionSort(array, n)
1   for i ← 1 to n − 1
2     j ← IndexOfMin(array, i, n)
3     Swap elements array[i] and array[j]
4   return array

```

# pomocná funkce pro výměnu dvou prvků
Swap <- function(array, i, j) {
  tmp <- array[i]
  array[i] <- array[j]
  array[j] <- tmp
  return(array)
}

# Selection Sort
SelectionSort <- function(array, n) {
  for (i in 1:(n - 1)) {
    j <- IndexOfMin(array, i, n)
    array <- Swap(array, i, j)
  }
  return(array)
}

# TEST
arr2 <- c(7, 3, 9, 1, 5)
SelectionSort(arr2, length(arr2))


### Task 4
* In R, implement the function `RecursiveSelectionSort()` according to the following pseudocode.

* Input:
    * a list of integers
    * an index of the first position
    * an index of the last position

* Output:
    * a sorted list of integers

* Estimate the number of operations of this function, i.e., the computational complexity, depending on the input size.
* Determine the *O* notation.
* Decide which algorithm (`SelectionSort()` or `RecursiveSelectionSort()`) algorithm is more efficient.

```
RecursiveSelectionSort(array, first, last)
1   if first < last
2     index ← IndexOfMin(array, first, last)
3     Swap array[first] with array[index]
4     array ← RecursiveSelectionSort(array, first + 1, last)
5   return array
```

# Rekurzivní Selection Sort
RecursiveSelectionSort <- function(array, first, last) {
  if (first < last) {
    index <- IndexOfMin(array, first, last)
    array <- Swap(array, first, index)
    array <- RecursiveSelectionSort(array, first + 1, last)
  }
  return(array)
}

# --- Test ---
arr3 <- c(7, 3, 9, 1, 5)
RecursiveSelectionSort(arr3, 1, length(arr3))
# Očekávaný výstup: c(1, 3, 5, 7, 9)

## Download files from GitHub
<details>
<summary>Basic Git settings</summary>

>* Configure the Git editor
>    ```bash
>    git config --global core.editor notepad
>    ```
>* Configure your name and email address
>    ```bash
>    git config --global user.name "Zuzana Nova"
>    git config --global user.email z.nova@vut.cz
>    ```
>* Check current settings
>    ```bash
>    git config --global --list
>    ```
>
</details>

* Create a fork on your GitHub account. 
  On the GitHub page of this repository find a <kbd>Fork</kbd> button in the upper right corner.
  
* Clone forked repository from your GitHub page to your computer:
```bash
git clone <fork repository address>
```
* In a local repository, set new remote for a project repository:
```bash
git remote add upstream https://github.com/mpa-prg/exercise_03.git
```

#### Send files to GitHub
Create a new commit and send new changes to your remote repository.
* Add file to a new commit.
```bash
git add <file_name>
```
* Create a new commit, enter commit message, save the file and close it.
```bash
git commit
```
* Send a new commit to your GitHub repository.
```bash
git push origin main
```
