#### For each of the commands cd, ls, and cat, and using the workspace you created in this lab:

##### 1) Share an example of using the command with no arguments.
##### 2) Share an exmaple of using the command with a path to a directory as an argument.
##### 3) Share an example of using the command with a path to a file as an argument.

#### So that’s 9 total examples (3 for each command). For each, include:

A screenshot or Markdown code block showing the command and its output
What the working directory was when the command was run
A sentence or two explaining why you got that output (e.g. what was in the filesystem, what it meant to have no arguments).
Indicate whether the output is an error or not, and if it’s an error, explain why it’s an error.

#cd with no args
<img width="206" alt="image" src="https://github.com/camman00/cse15l-lab-reports/assets/20690269/461dbcb8-d117-4724-9d6b-41199ea0bdaf">
* cd ran w/o args produces no result as technically you are going in the same directory
* There is no error as this functionality is intentional

#cd with a path to dir as arg
<img width="276" alt="image" src="https://github.com/camman00/cse15l-lab-reports/assets/20690269/c1dfd959-933f-45ae-9370-877d2ae30e5c">
* cd ran with file directory. Terminal is now based on that directory. Essentially we navigate from the previous directory to the new directory with the command
* No errors. This is what is supposed to happen.

#cd with a file as an arg
<img width="361" alt="image" src="https://github.com/camman00/cse15l-lab-reports/assets/20690269/331a2f82-bb77-49f6-8ea0-77fb64f75fc5">
* cd ran with a direct path to file results in an error/warning in console. This is because the arg should be for a dir not a file
* Error/warning occured. Needs a legit dir in order to work.

------------

#ls with no args
<img width="380" alt="image" src="https://github.com/camman00/cse15l-lab-reports/assets/20690269/0971422e-4bd8-437e-b886-5a6d4c085f83">
* ls with no args lists all the files in the current directory
* no errors this is expected

#ls with dir as arg
<img width="294" alt="image" src="https://github.com/camman00/cse15l-lab-reports/assets/20690269/536d93ce-9244-4bd3-ac08-3c5db32fe74a">
* ls with a dir as arg displays that specific dir contents
* No errors here!

#ls with file path as arg
<img width="358" alt="image" src="https://github.com/camman00/cse15l-lab-reports/assets/20690269/a0edbf62-b9ab-4268-b3a7-8e54e4bd37d1">
* ls with a file path as an arg just prints the file name itself
* This is not an error but something I did not expect.

-------------

#cat with no args
<img width="273" alt="image" src="https://github.com/camman00/cse15l-lab-reports/assets/20690269/d073ead6-2973-4425-ae9f-1a4ef93747c8">
* cat with no args it seems like the console just stalls
* no error displayed it just looks like its expecting its args

#cat with dir as arg
<img width="363" alt="image" src="https://github.com/camman00/cse15l-lab-reports/assets/20690269/ded041a4-b432-490c-8818-5f84653b8789">
* cat with a dir as an arg is similar to cd with a file path as arg
* console informs us that the the provided path is a dir

#cat with file path as an arg
<img width="590" alt="image" src="https://github.com/camman00/cse15l-lab-reports/assets/20690269/4663b8e6-412f-4642-bb91-db32164ab55f">
* it displayed the internal text of the file - very cool
* no errors this is correct!

