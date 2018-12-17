# E98-autograder
## Most Recent Update on Dec 16th, 2018 - 6:33PM PST - Rev C
#### Author: Paul Shao

### Usages:
The E98-autograder compiles the primary scripts required to automate testing of students' Ruby assignments.
The autograder can be used in the following 2 ways:
1. Streamline testing students' codes against expected outputs and generate final scores through `automate.py`.
2. Unit testing individual methods (should only be used for debugging or validating purposes) through `test_assignments_demo.rb`.
______________________________________________________________________________________________________________________________
**To all course staff**: Please run the tests to generate the scores **directly through `automate.py`**. Feel free to consult me **first** if you are confused about the process or want to test individual methods.
______________________________________________________________________________________________________________________________
### Primary Procedures (this should be how you use the autograder):
The streamlined version of the autograder is run through the CLI directly. Follow the steps below to generate scores for your students for this week's assignments:
1. `git clone` this repository. (If cloned already, `git pull` to check for test-cases updates).
2. `cd` into this repository and enter the command `python -i automate.py`.
3. Now that we are interacting with the Python main execution file, we will be relying on the method `fetch_from_github`.
4. `fetch_from_github` takes in 4 parameters: `usernames`, `week`, `chapters`, `files`:
   1. `usernames` is a list of the Github usernames for your students.
   2. `week` is a string indicating the current week of the assignment (e.x. `week1`).
   3. `chapters` is a list of the chapters this assignment contains (e.x. `['ch02', 'ch05']`).
   4. `files` is a list of the files the autograder will test (e.x. `['age_in_seconds.rb', 'hours_in_year.rb']`).
5. Fill in all 4 parameters, and hit `Enter` to execute the scripts, you should see statements such as `fetch success` during the entire process.
6. In the end, a `csv` file containing all the students' scores will be generated in the main directory of this Python script:
   1. The `csv` file contains 4 columns: `Github username`, `Week`, `Tested Method`, and `Score`. 
   2. `Score` is generated on a scale of 2 per method (it is computed by normalizing the total number of passed test cases).

______________________________________________________________________________________________________________________________
### Alternative Usages (for unit testing/debugging purposes ONLY)
#### Again, please discuss with me before using the autograder this way.

To allow for unit testing of specific methods locally, run `test_assignments_demo.rb`, it will invoke both the **static unit test and interactive test instances** on different methods.
______________________________________________________________________________________________________________________________
### Current Testing Parameters/Functionalities Supported:

* Interactive or Static (One-time) Input
* Time Limit
* Specific by-line Error Feedback

______________________________________________________________________________________________________________________________

### Demos:

**Unit Test for Static (One-time Input and Output) Methods**

Primary Testing Method: `assert_equal`

`add.rb`

**Interactive Test**

Primary Testing Method: `Interactive.test_match`

`greet.rb`
`angry_grandma.rb`

### How it works for Interactive Test
It takes in the following 4 files, 
1. `students_program.rb`
2. `test_input.txt`
3. `test_output.txt`
4. `expected_output.txt`

Then, with a **given time constraint**, the interactive class will run the program with the test input in the textfile, redirect the output stream to the empty textfile, and in the end, compare that against the expected output line by line. 

