The Javascript Event Loop
===
####Intro

Javascript (JS) is the universal scripting language, which can be used to add interactivity to your webpage. However, JS is very deep and complex in the way that it operates *under the hood*. Understanding its complexities and functions will help any developer write cleaner and more modularized code. This is where the event loop comes into play.

The event loop, is a construct built into programs that controls and dispatches events. It is the link between your program and the operating system. The event loop is made up of 3 different data structures:


**The Call Stack**- This data structure stores information about the active routines under the hood. This data structure is specific to function and executes in its operations using the LIFO (last in first out) method.

**The Heap**- This data structure stores objects. When anything is declare it is stored in the heap. Since everything in Javascript is an object, everything gets stored in heap as information

**The Queue**- This data structure stores events that are meant to be executed at a later time; the most common  being timers. The stack must be empty for objects to move to the stack. The method used to executes these objects as FIFO (first in first out).

![The Stack](data:image/jpeg;base64,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)

###### Example 1


	function goodbye(){
		console.log("Goodbye!"); 
	}

	function hello(){
		console.log("Hello!");
	}

	hello();
	goodbye();



1. `hello();` gets called and is sent to the stack. The function runs and `returns "Hello!"`.

2. `hello();` gets popped off the stack.

3. `goodbye();` gets called and is sent to the stack. The function runs and returns "Goodbye!".

4. `goodbye();` gets popped off the stack.


###### Example 2


	function sayHello(){
		return "Hello... later!"
	}
	function sayHi(){
		return "Hi...now!";
	}

	set	Timeout(sayHello, 10);
	sayHi();



1. `setTimeout` gets sent to the heap, then it is  stored in the queue (after 10 milliseconds).

2. While `setTimeout` is in the queue, `sayHi();` is called and sent to the stack. This demonstrate the asynchronicity of javascript. under the hood, Javascript will not wait for other commands to execute. It will run as many commands as it can. 

3. `sayHello();` executes and returns "Hi...now!". Then it pops off the stack since it has nothing else to do. 

4. Only, after, `sayHi();` is executed, the `setTimeout` moves from the queue to the stack and executes the `sayHello();` function. The stack must be empty before anything moves from the queue to the stack.


###### Example 3



	function goFirst(){
		console.log ("I'm first");
	}

	setTimeout(function(){console.log("I'm next")},0)

	function goThird(){
		console.log ("I'm third");
	}

	goFirst();
	goThird();



1. `setTimeout`is called and is sent to the heap, then immediately to the queue (since it is set to 0), where it waits.

2. `goFirst()` is called to the stack, where it `console.logs`, "I'm first". Then it pops off.

3. `goSecond()` is called to the stack where it `console.logs`, "I'm third". Then it pops off.

4. Once the stack is empty, `setTimeout` moves to the stack and `console.logs` "I'm next". Then it pops off. 


#### Conclusion

As you've observed, things do not work in the order which they appear in Javascript, since it is an asynchronous language. I only internalized the asynchronicity of JS when I learned about the event loop and what happens *under the hood*. If you take anything away from this piece it should be the following, run your programs and understand why they work the way that they do. Understand what bits of code should be executed first and why. This goes back to understanding the event loop and its importance. Hope this helps. Good hunting!