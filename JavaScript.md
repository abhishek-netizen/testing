# Welcome to JavaScript.

# Day-1
## How JavaScript Works & Execution Context:
[Namaste JavaScript Ep.1](https://youtu.be/ZvbzSrg0afE) <br />
Everything in javascript happens inside a **Execution Context**: <br />
we can assume the 'Execution Context' as a big box or container in which whole JS code is executed. <br/>
'Execution Context' has two component, first one is ***memory component*** also known as **Variable Environment** <br />
and the second component is ***code component*** also called as **Thread of Execution**. <br /><br/>
**Variable Environment(memory component):-** this is the place in which all the variables and functions are stored in **key:value** pairs <br/>
**Thread of Excetion(code component):-** this is the place where code is executed one line at a time, thats where the words comes in > ***JavaScript is a Syncronous Single-Threaded Language***. <br/>
single threaded means it only executes one line at a time, syncronous single threaded means JS can only executes one line at a time in a specific order, it will only move to the next line only if the current line execution is finished.

[IMAGE YET TO COME]

Learn more about JS how does it works internally 👉 [JavaScript Internals](https://medium.com/@bdov_/javascript-typescript-execution-vs-lexical-vs-variable-environment-37ff3f264831) must read!!! tc of flaws in the article

# Day-2 
## How JavaScript Code is executed? & Call Stack:
[Namaste JavaScript Ep. 2](https://youtu.be/iLWTnMzWtj4) <br />

```
//Example code

var n = 2;
function square(num){
   var ans = num * num;
   return ans;
 }

var square2 = square(n);
const square4 = square(4);
```
Remember everything happens in javascript within ```Excecution Context```

when we run the above code <br/>
1. Global Excecution Context is created
2. It has two components **Memory component** & **Code component**
3. Excecution context done in two phase "Memory Creation phase" & "Code excecution phase"
4. in "Memory Creation" phase it will store all the variables as 'undefined', <br /> incase of function its literally stores entire func inside memory
5. So in first phase i.e "Memory Creation phase" folllowing things will happen, when JS starts from line by line from the top.
   **Memory** | **Code**
   -----------|---------
   n:undefined| 
   saquare:{entire func} | 
   square2:undefined |
   square4:undefined |
 6. So in second phase i.e "Code execution phase" code is actually started running(calulation & everything), when JS starts from line by line from the top, once again
 7. now when JS viewed 1st line it replaces undefined with actual value
     **Memory** | **Code**
     -----------|---------
      n:2| 
 8. in line 2 to 5 nothing to excecute, so its move to the line 6. <br/>
 Here the magic happens!!.  JS has to "envoke a function" <br/>
 9. When a function is Envoked it has to create another local ```Excecution Context``` <br/> thats exactly what happened here, when it encountered square(n) in line num 6
 10. so again memory and code and again phase 1 and phase 2
 11.  in phase 1
      **Memory local** | **Code local**
      -----------|---------
      num:undefined| 
      ans:undefined|
 12. in phase 2 code excecution start <br/>
```
var n = 2;
function square(num){  //argument
   var ans = num * num;
   return ans;
 }

var square2 = square(n); //parameter
var square4 = square(4);
```
1. parameter is passed to the function argument <br/> i.e 2
2. and the calcutn happens and its store the value in ans <br/>
   **Memory local** | **Code local**
   -----------|---------
    num: 2| 
    ans: 4|
 3. and then it encouters the ```return ans``` keyword <br/>
which literally tells the JS to ***Give back the control to the original excecution context,<br/>
where in which function is excecuted.*** in our case it is square(n)
4. so in 5TH Step (see above) it changes the value of square in Memory, and our ```local excecution context``` is done and deleted.
   **Memory** | **Code**
   -----------|---------
      n: 2| 
   square2: 4 |
5. ahh!! we done with till line var square(2), when JS move to line var square(4), <br/>it enokes a function i.e square(4) and passes the parameter i.e 4 to argument num
6. once again ```local excecution is created``` and do the calctn and updates local exceution context values, <br/> and when it encouters the ``return ans``
 it give back the control to global exceution where in which the function is envoked in our case it is square(4), <br/> and then it updates square4 variable value from undefined to 16
 
13. and finally our global excecution looks something like this 

**Memory** | **Code**
-----------|---------
n:2| 
square2:4 |
square4:16 |

Once JS finished all its work by excecuting all its line  then ```Global Excecution Context``` is also deleted uff!!

14. So now one more question arises, what if? if we have function invocation inside the function haha <br/>
then we have ```Global execution context ``` and we have ```local execution context``` inside another ```local execution context``` and so on.. <br/>
kind of nested local execution inside another local execution.

So how does JS manages all these contexts isn't that difficult to keep track of all those context ????

![its time](https://media.giphy.com/media/SKcxqI1GiASU783uT2/giphy.gif)

### Call Stack
It is a Stack : everytime in the bottom of the stack we have GEC or ```Global Excecution context``` <br/>
which means whenever a JS program is run    ```Global Excecution context``` is pushed to this call stack bottom. <br/>
and then when ```local execution context - E1``` is created or a function is envoked it is pushed on the top of the ```Global Excecution context``` <br/>
and when the E1 done with its job(in this case return ans) its popped out, and  the control goes to the GEC ```Global Excecution context``` where its left off in our case it is var square(2) <br/>
same goes with ```local execution context - E2``` .


 

   

