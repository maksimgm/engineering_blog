


### Difference between Lambdas and Procs

First, a lambda checks the number of arguments passed to it, while a proc does not. This means that a lambda will throw an error if you pass it the wrong number of arguments, whereas a proc will ignore unexpected arguments and assign nil to any that are missing.

Second, when a lambda returns, it passes control back to the calling method; when a proc returns, it does so immediately, without going back to the calling method.


```


p1 = Post.create(title:"Movies to Watch", content:"Some awesome movies to watch this year", author:"Maksim")

p2 = Post.create(title:"Food", content:"Some amazing recipes", author:"Jack")

p3 = Post.create(title:"Amazing workouts", content:"Amazing exercies for the motivated ones", author:"Shelly")

`&` converts proc to a block