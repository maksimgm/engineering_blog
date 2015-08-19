The Javascript Event Loop
===
####Intro

Javascript (JS) is the universal scripting language, which can be used to add interactivity to your webpage. However, JS is very deep and complex in the way that it operates *under the hood*. Understanding its complexities and functions will help any developer write cleaner and more modularized code. This is where the event loop comes into play.

The event loop, is a construct built into programs that controls and dispatches events. It is the link between your program and the operating system. The event loop is made up of 3 different data structures:


**The Call Stack**- This data structure stores information about the active routines under the hood. This data structure is specific to function and executes in its operations using the LIFO (last in first out) method.

**The Heap**- This data structure stores objects. When anything is declare it is stored in the heap. Since everything in Javascript is an object, everything gets stored in heap as information

**The Queue**- This data structure stores events that are meant to be executed at a later time; the most common  being timers. The stack must be empty for objects to move to the stack. The method used to executes these objects as FIFO (first in first out).

![The Stack](https://encrypted-tbn1.gstatic.com/images?q=tbn:ANd9GcRd8vnnxLXGD40oNqKPs7OYf0EuhHsFHKj0lnFN2rw_sfxPUdfPkQ)

###### Example 1
```
function goodbye(){
	return "Hello!"
}

function hello(){
	return "Goodbye!"
}
hello();
goodbye();
```
1. `hello();` gets called and is sent to the stack. The function runs and `returns "Hello!"`.
2. `hello();` gets popped off the stack.
3. `goodbye();` gets called and is sent to the stack. The function runs and returns "Goodbye!".
4. `goodbye();` gets popped off the stack.


###### Example 2
```
function sayHello(){
	return "Hello... later!"
}
function sayHi(){
	return "Hi...now!";
}

setTimeout(sayHello, 10);
sayHi();
```

1. `setTimeout` gets sent to the heap, then is immediately stored in the queue (after 10 milliseconds). 

2. While `setTimeout` is in the queue, `sayHi();` is called and sent to the stack. This demonstrate the asynchronicity of javascript. under the hood, Javascript will not wait for other commands to execute. It will run as many commands as it can. 

3. The `sayHello();` executes and returns "Hi...now!". Then it pops off the stack since it has nothing else to do. 

4. Only, after, `sayHi();` is executed, the `setTimeout` moves from the queue to the stack and executes the `sayHello();` function. The stack must be empty before anything moves from the queue to the stack.


###### Example 3
```
function goFirst(){
console.log ("I'm first");
}

setTimeout(function(){console.log("I'm next")},0)

function goThird(){
console.log ("I'm third");
}

goFirst();
goThird();
```

1. `setTimeout`is called and is sent to the heap, then immediately to the queue (since it is set to 0), where it waits.

2. `goFirst()` is called to the stack, where it `console.logs`, "I'm first". Then it pops off.

3. `goSecond()` is called to the stack where it `console.logs`, "I'm third". Then it pops off.

4. Once the stack is empty, `setTimeout` moves to the stack and `console.logs` "I'm next". Then it pops off. 


#### Conclusion

As you've observed, things do not work in the order which they appear in Javascript, since it is an asynchronous language. I only internalized the asynchronicity of JS when I learned about the event loop and what happens *under the hood*. If you take anything away from this piece it should be the following, run your programs and understand why they work the way that they do. Understand what bits of code should be executed first and why. This goes back to understanding the event loop and its importance. Hope this helps. Good hunting!