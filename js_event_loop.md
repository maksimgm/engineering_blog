The Javascript Event Loop
===
######Intro

An event loop, waits for and dispatches events in a  program. It is the link between your program and the operating system.



The Call Stack- This data structure stores information about the active routines under the hood. This data structure is specific to function and executes in its operations using the LIFO method(last in first out).

The Heap- This data structure stores objects. When anything is declare it is stored in the heap. Since, everything in Javascript is an object, everything gets stored here as information

The Queue- This data structure stores events that are meant to be executed at a later time; the most common  being timers. The stack must be empty for things to moved to the stack. The method used to executes thes objects, is FIFO(first in first out).

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

1.`setTimeout` gets sent to the heap, then is immediately stored in the queue. 

2. While `setTimeout` is in the queue, `sayHi();` is called, and is sent to the stack. This demonstrate the asynchronicity of javascript. under the hood, Javascript will not wait for other commands to execute. It will run as many commands as it can. 

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

1. `setTimeout`is called and is sent to the heap, then immediatly to the queue,where it waits.

2. `goFirst()` is called to the stack, where it `console.logs`, "I'm first". Then it pops off.

3. `goSecond()` is called to the stack where it `console.logs`, "I'm third". Then it pops off.

4. Once the stack is empty, `setTimeout` moves to the stack and `console.logs` "I'm next". Then it pops off. 