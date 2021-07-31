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
   aquare:{entire func} | 
   square2:undefined |
   square4:undefined |
 6. So in second phase i.e "Code execution phase" code is actually started running(calulation & everything), when JS starts from line by line from the top, once again
 7. now when JS sees the first line it replaces undefined with actual value <br/>

   

