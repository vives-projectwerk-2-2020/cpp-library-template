# A C++ Library template and How-To
A C++ template and how-to for converting proof-of-concept code to a building block for (larger) projects.

## What is a library (for)
It is a bundle of code, packaged up, enabling some specific functionality.
Typically it makes it easier to use this bundle of code as a building block for a program. Also you can easily make it available to others so they (or yourself in the future) don't have to write code to implement the same functionality.

## How to go about creating a library

### Step 1 - Proof of concept
After you've spend some time coding, you're in a good place, your code is working and it's doing something useful.
So let's move on to step 2 and start to refactor it with the goal of turning it into a library with a clear goal and a clean interface.

Example code at this stage:
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

The goal here is that if it's not yet a class that we 








---
Based upon the following mbed cookbook example (code examples are copied from this site):
[https://os.mbed.com/cookbook/Writing-a-Library](https://os.mbed.com/cookbook/Writing-a-Library)