# A C++ (mbed) Library template and How-To
A C++ template and how-to for converting proof-of-concept code to a building block for (larger) projects.

## What is a library (for)
It is a bundle of code, packaged up, enabling some specific functionality.
Typically it makes it easier to use this bundle of code as a building block for a program. Also you can easily make it available to others so they (or yourself in the future) don't have to write code to implement the same functionality.

## How to go about creating a library

### Step 1 - Proof of concept
After you've spend some time coding, you're in a good place, your code is working and it's doing something useful.
So let's move on to step 2 and start to refactor it with the goal of turning it into a library with a clear goal and a clean interface.

Our code might look something like this:
```
#include "mbed.h"
 
DigitalOut pin(LED2);
 
int main() {
    // do something...
 
    // flash 5 times
    for(int i=0; i<10; i++) {
        pin = !pin;
        wait(0.2);
    }
 
    // do something else
 
    // flash 2 times
    for(int i=0; i<4; i++) {
        pin = !pin;
        wait(0.2);
    }
 
    // do another thing
}
```

### Step 2 - Keeping your code DRY
Take a good long look at your code, are you happy with it? Are you finding some duplicate code, maybe the result of some quick copy-paste coding? No worries, now is the time to DRY it off.

Group the parts of your code that do the same thing in a function.
After doing this our code might look a little more like this:
```
#include "mbed.h"
 
DigitalOut pin(LED2);
 
void flash(int n) {
    for(int i=0; i<n*2; i++) {
        pin = !pin;
        wait(0.2);
    }
}
 
int main() {
    // do something...
 
    // flash 5 times
    flash(5);
 
    // do something else
 
    // flash 2 times
    flash(2);
 
    // do another thing
}
```

Check if it's still functioning as intended. All good? Perfect, let's move on to step 3. Not good? Take your time, where not going anywhere without you.


### Step 3 - Turning it into a class
Take a look at the class template in this repo. It's in the src directory. You will see two files there, a .cpp file and an .h (header) file.

(If you would like to see the example code above refactored into a class, feel free to follow the link at the bottom of this README. However, the code is not up-to-date, more specifically, it contains an older method of assuring pre-processor definitions/includes happen only once)

Be sure NOT to follow the guide on how to publish a library found on the website of which the link can be found below.

If you have been pushing your code to Github this whole time, then you are ready. Just make sure your repo is public. Anyone that wants to use it will be able to.
If you haven't yet done that, create a repo and push your project to Github. There, you're ready too.

Also a word about the `.gitignore` file, if you make use of library's yourself then make sure to add those directories to the `.gitignore` file (not the .lib files, only the directories of those libraries).
You are not responsible for that code, so it should not be in your library's repo.

If someone wants to use your library the `mbed add` command (see the last step in this readme for a little more info on that) will incorporate those library's into the project as wel.

### Step 4 - Documentation
Arguably the most important step.

You have just created this library, you probably know how to use it quite well. However, someone else (or yourself in the future) will need allot of time to figure it out without proper documentation.
Use the README in the root of your project to explain how people should make use of your library. In other words: a short description of what it does, what methods are available (i.e. what it's API is), how they should import it into their project, ...

Anybody wanting to use it will be forever grateful to you for offering clear documentation (ok, maybe not, but no one will use it if they don't know how :)

### Step 5 - Making use of your freshly brewed library
* In the project where you want to make use of it open up a terminal
* type `mbed add [https link to the github repo of the library]`
* ``#include`` the header file of the class you want to use where you need it
* you're set, time to rock 'n roll !



---
Based upon the following mbed cookbook example (code examples are copied from this site):
[https://os.mbed.com/cookbook/Writing-a-Library](https://os.mbed.com/cookbook/Writing-a-Library)