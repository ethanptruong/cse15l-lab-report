# Lab Report 4
## Step 4: Remote Connection
![Image](https://imgur.com/YJnytU7)
> Keys Pressed: I typed ```ssh cs15lfa23hb@ieng6.ucsd.edu``` and then ```<Enter>```.
> The ```ssh``` command was used to remotely connectoto the ```ieng6``` computer using my username.


## Step 5: Clone Repository
![Image]([https://imgur.com/RqXonnH)
> Keys Pressed: I cloned the forked repository by typing ```git clone git@github.com:ethanptruong/lab7.git```, and then ```<Enter>```.
> The git clone command cloned the ```SSH``` repository from GitHub to the local machine (in this case the ```ieng6``` computer) to create
> a local copy of the forked repository.

## Step 6: Failed Tests
![Image](https://imgur.com/1iE0VE7)
> Keys Pressed: I typed ```bash test.sh``` and then ```<Enter>```.
> The ```bash``` command runs the ```test.sh``` script, which will execute all of the necessary code to execute the JUnit tests.
> The test demonstrated that one of the tests failed due to a different expected output, but one test did pass.

## Step 7: Fixing the Error
![Image](https://imgur.com/wYnu2W5)
> Keys Pressed: ```vim ListExamples.java``` then the ```<j>``` key 44 times in total, and the ```<l>``` key 12 times, then ```<r>``` and finally
> ```<2>```. The ```vim``` command opened the ```ListExamples.java``` in ```vim``` for editing. Pressing the ```<j>``` key 44 times caused
> the cursor to move down to the 44th line, and the ```<l>``` key 12 times caused the cursor to move 12 characters to the right until it
> was on the 1 of ```index1```. I then used ```<r>``` and ```<2>``` to replace the current character so the variable is ```index2```.

## Step 8: Passed Tests
![Image](https://imgur.com/y9hvLvd)
> I typed ```:wq```, ```bash test.sh```, then ```<Enter>```.
> The ```:wq``` command saved my changes to the ```ListExamples.java``` file and exited ```vim```. Running the ```bash test.sh``` command
> ran the ```test.sh``` script, which executed the necessary code to run the JUnit Tests, which demonstrated that the code has passed all
> tests.

## Step 9: Pushing to Git
![Image](https://imgur.com/pXzc04P)
> I pressed ```git add ListExamples.java```, ```<Enter>```, ```git commit -m "Fixed bug in file"```, ```<Enter>```, ```git push```, and
> ```<Enter>```. Using the ```git add``` command prepares the changed file, ```ListExamples.java```, to be committed to git. The
> ```git commit -m "Fixed bug in file"``` adds a commit message that will describe the fix or changes made when the file is pushed. Finally,
> ```git push``` will upload the changes in the file to the remote repository on GitHub to update it. 
