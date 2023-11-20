# Part 1 - Bugs
Choose one of the bugs from week 4's lab.

The bug I will be selecting is the __ReverseInPlace__ method within the __ArrayExamples__ class.

Each criteria for this report will be addressed in the following ordered manner.
<ol type='a'>
  <li>
    A failure-inducing input for the buggy program, as a JUnit test and any associated code (write it as a code block in Markdown)
  </li>
  <li>
    An input that doesn’t induce a failure, as a JUnit test and any associated code (write it as a code block in Markdown)
  </li>
  <li>
    The symptom, as the output of running the tests (provide it as a screenshot of running JUnit with at least the two inputs above)
  </li>
  <li>
    The bug, as the before-and-after code change required to fix it (as two code blocks in Markdown)
  </li>
</ol>

__(a)__

```
@Test 
	public void testReverseInPlace() {
    int[] input1 = { 1,2,3,4,5 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 5,4,3,2,1 }, input1);
	}
```
__Stack Trace__
```
JUnit version 4.13.2
.E.
Time: 0.007
There was 1 failure:
1) testReverseInPlace(ArrayTests)
arrays first differed at element [3]; expected:<2> but was:<4>
	at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
	at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:28)
	at org.junit.Assert.internalArrayEquals(Assert.java:534)
	at org.junit.Assert.assertArrayEquals(Assert.java:418)
	at org.junit.Assert.assertArrayEquals(Assert.java:429)
	at ArrayTests.testReverseInPlace(ArrayTests.java:9)
	... 32 trimmed
Caused by: java.lang.AssertionError: expected:<2> but was:<4>
	at org.junit.Assert.fail(Assert.java:89)
	at org.junit.Assert.failNotEquals(Assert.java:835)
	at org.junit.Assert.assertEquals(Assert.java:120)
	at org.junit.Assert.assertEquals(Assert.java:146)
	at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria.java:8)
	at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
	... 38 more

FAILURES!!!
Tests run: 2,  Failures: 1


```
__ReverseInPlace__
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
__(b)__

```
@Test 
	public void testReverseInPlace() {
    int[] input1 = { 1 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 1 }, input1);
	}
```
__Stack Trace__
```
JUnit version 4.13.2
..
Time: 0.005

OK (2 tests)

```
__ReverseInPlace__
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
__(c)__

The symptom, as the outputs was stated above but I will restate here for clarity:
![image](https://github.com/camman00/cse15l-lab-reports/assets/20690269/e8dac0bf-9d74-4b70-a482-02cea1415a8c)
and with the second input
![image](https://github.com/camman00/cse15l-lab-reports/assets/20690269/02750c53-131c-4996-a64d-e9f9d3f71af8)

__(d)__
The bug as the before and after code to fix it.

Incorrect:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
Correct:
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length / 2; i += 1) {
      int temp = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = temp;
    }
  }
```
When reversing an array we need to have a temp variable to hold the value of the swap so that after we swap the first value we can perform the second swap. We introduce temp as this variable and set it to the value of the current index.
after performing the swap as usual we need to then perform the second swap which we will then use the temp variable. We only need to perform these swaps until we reach the middle of the array thus we modify the loop condition from i < arr.length to
i < arr.length / 2.
#Part 2 - Researching Commands
I decided that I was going to research the find command. We need two examples of using the new option on the ./technical directory. Show each example as a code block that shows the command and its output. Write a sentence about what its doing and why its useful

### 1
```
find technical/ -empty | pbcopy
(no output)
```
The command is recursively traversing through the technical directory searching for empty directories. Since the output was bland I piped it with pbcopy which will copy the output of any command to the clipboard. Pretty cool right?
### 2
```
find technical/biomed/ -empty
technical/biomed//blasnk.txt
```
When a file is provided as a path this command will print output if the file is empty. In this case blasnk.txt is printed since it is empty.
### 3
```
find technical/biomed/ -mtime -500s
technical/biomed//blasnk.txt
```
The -mtime -time flag allows us to find items that were last modified within the last time provided. We were able to find this file we recently made this could be very helpful.
### 4

```
find technical/biomed/ -mtime -0s
No ouput
```
Honestly was just curious what would happen when 0 was provided for the time. As expected nothing was modified within the last 0 seconds.
### 5
```
find technical/biomed/ -size +1MB
No output
```
This one will try and find within the technical/biomed directory that is > 1MB.
### 6
```
find technical/biomed/ -size +200
technical/biomed//1471-2105-3-2.txt
```
We were able to find a certain directory with the +200 flag which is used for kb. Very useful if you are looking for big and small files.
### 7
```
find technical/ ! -type f
technical/
technical//government
technical//government/About_LSC
technical//government/Env_Prot_Agen
technical//government/Alcohol_Problems
technical//government/Gen_Account_Office
technical//government/Post_Rate_Comm
technical//government/Media
technical//plos
technical//biomed
technical//911report
```
This one is really interesting the ! is the not operator and searches for everything that is not a file.
### 8
```
find technical/ -not -type f -and -size 1GB
no output
```
We can use more logical operators such as -and or instead of using ! we can use -not as a subsitute. Its important to note in some shells ! will wrap all the following parameters as a not.

##### Citing my sources: ChatGPT
#### Provided Prompt
```
Consider the commands less, find, and grep. Choose one of them. Online, find 4 interesting command-line options or alternate ways to use the command you chose. To find information about the commands, a simple Web search like “find command-line options” will probably give decent results. There is also a built-in command on many systems called man (short for “manual”) that displays information about commands; you can use man grep, for example, to see a long listing of information about how grep works. Also consider asking ChatGPT!

Lets do find
```
#### Output

Certainly! The `find` command is a powerful tool used in Unix-like operating systems for searching files and directories in a directory hierarchy. Here are four interesting command-line options for the `find` command:

1. **Search by File Type:**
   You can use the `-type` option to specify the type of file you are looking for. For example, to find all the text files in a directory, you can use:
   ```bash
   find /path/to/directory -type f -name "*.txt"
   ```
   This command will search for files (`-type f`) with names ending in ".txt" in the specified directory.

2. **Search for Empty Files or Directories:**
   To find and list empty files or directories, you can use the `-empty` option:
   ```bash
   find /path/to/directory -type f -empty
   ```
   This command will find and display the names of all empty files in the specified directory.

3. **Execute Commands on Found Files:**
   The `-exec` option allows you to execute a command on the files found. For example, to delete all `.tmp` files in a directory, you can use:
   ```bash
   find /path/to/directory -type f -name "*.tmp" -exec rm {} \;
   ```
   This command finds all files with the ".tmp" extension and executes the `rm` command on each of them.

4. **Combine Multiple Conditions with Logical Operators:**
   You can use logical operators like `-and`, `-or`, and `-not` to combine multiple conditions. For instance, to find all `.txt` files modified in the last 7 days, you can use:
   ```bash
   find /path/to/directory -type f -name "*.txt" -mtime -7
   ```
   This command searches for files with the ".txt" extension that have been modified in the last 7 days.

Remember to replace `/path/to/directory` with the actual path you want to search in. The `man find` command in the terminal provides detailed information about all the options and how to use them.

#### Provided Follow Up Prompt
```
Answer the question again
```
#### Output
Certainly! Here are four interesting command-line options or alternate ways to use the `find` command:

1. **Search for Files Modified Within a Specific Time Range:**
   The `-newer` option allows you to find files that were modified more recently than a reference file. For example, to find files modified in the last 24 hours, you can use:
   ```bash
   find /path/to/directory -newermt 2023-11-18 ! -newermt 2023-11-19
   ```
   This command searches for files modified between midnight on November 18, 2023, and midnight on November 19, 2023.

2. **Exclude Directories from the Search:**
   The `! -type d` option can be used to exclude directories from the search results. For instance, to find all files with a `.log` extension but exclude directories from the results, you can use:
   ```bash
   find /path/to/directory -type f -name "*.log" ! -type d
   ```
   This command finds files with the ".log" extension but excludes directories from the output.

3. **Search for Files Based on Size:**
   The `-size` option allows you to search for files based on their size. For example, to find all files larger than 1 megabyte in a directory, you can use:
   ```bash
   find /path/to/directory -type f -size +1M
   ```
   This command searches for files larger than 1 megabyte.

4. **Print Only the Path of the Found Files:**
   The `-printf` option allows you to control the format of the output. To print only the path of the found files, you can use:
   ```bash
   find /path/to/directory -type f -printf "%p\n"
   ```
   This command prints the path of each file found.

These options demonstrate the flexibility and power of the `find` command in searching for files based on various criteria. You can explore more options and details using the `man find` command in the terminal.

##### [https://](https://chat.openai.com/)https://chat.openai.com/
