# Lab Report 4
Do the following steps and explain each keystroke:
* Log into ieng6
* Clone your fork of the repository from your Github account (using the SSH URL)
* Run the tests, demonstrating that they fail
* Edit the code file to fix the failing test
* Run the tests, demonstrating that they now succeed
* Commit and push the resulting change to your Github account (you can pick any commit message!)

# Log into ieng6
<img width="480" alt="image" src="https://github.com/camman00/cse15l-lab-reports/assets/20690269/8134c16e-af94-4640-a308-05485e8e8aa5">

ssh cs15lfa23ho@ieng6.ucsd.edu
# Clone the repo
<img width="563" alt="image" src="https://github.com/camman00/cse15l-lab-reports/assets/20690269/f00ac7a1-2ed8-47b8-983d-25213ce65f19">

git clone https://github.com/camman00/lab7.git
# Run Tests (Failures)
<img width="568" alt="image" src="https://github.com/camman00/cse15l-lab-reports/assets/20690269/c9a80b0b-c771-4bfe-a441-86ca9fea1e1f">

cd lab7

bash test.sh

# Edit The Code
<img width="560" alt="image" src="https://github.com/camman00/cse15l-lab-reports/assets/20690269/9a9994d2-074b-47c7-aed9-465e16faf6d4">

<img width="559" alt="image" src="https://github.com/camman00/cse15l-lab-reports/assets/20690269/7a6d5a37-8747-4469-815f-fa68b3131538">

vim ListExamples.java
```
/result.add(0
<right><right><right><right><right><right><right><right><right><right><right>
i
<backspace><backspace>
<right>
<backspace>
(
<esc>
/while(index < list2.size()
<down><down><down>
<right><right><right><right><right><right>
i
2
<esc>
:wq
```
# Rerun The Tests

bash test.sh

<img width="565" alt="image" src="https://github.com/camman00/cse15l-lab-reports/assets/20690269/f2504dd7-c8d1-4436-b677-fcbe08c36b7e">
# Commit to GitHub

# Commit & Push
<img width="909" alt="image" src="https://github.com/camman00/cse15l-lab-reports/assets/20690269/40dbdc67-7abc-4d20-8406-d2d5864942a5">

<img width="566" alt="image" src="https://github.com/camman00/cse15l-lab-reports/assets/20690269/25945383-de2b-41ed-804d-6cbabd4dbc5f">

ssh-keygen (for ssh part)
git add ListExamples.java
git commit -m "Yay"
git push git@github.com:camman00/lab7.git
