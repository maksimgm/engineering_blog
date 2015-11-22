Blocks, Procs, Yields in Ruby
===

Ruby is a synchronous object oriented language created in order to make writing code more efficient and readable. However, due to Ruby's  synchronicity, methods run in the order which they are written. Whereas, Javascript is asynchronous ,which means things don't get executed in the order which they are written, hence the use of callback functions. The great thing about Ruby is that it has the equivalent of callback functions even though it is synchronous. Blocks and yields are Rubys way of creating asynchronicity.

#####Features of a block

1. consists of chunks of code
2. block has a name
3. codes inside the block is always enclosed within {}
4. a block is always invoked from a function with the same name as that of the block
5. We invoke a block by using a yield statement

Syntax of block without parameters:

```
def block_test
  puts "We're in the method!"
  puts "Yielding to the block..."
  yield
  puts "We're back in the method!"
end

block_test { puts "We're in the block!" }



OUTPUT:

We're in the method!
Yielding to the block...
We're in the block!
We're back in the method

```

Block test calls the  block method which runs yield,  leading to the execution fo the code executes the code


```
def block_test_params
	puts 'We are in the method'
	yield 2
end

block_test_params{
	|i| puts 'We are in the block #{i}'
}

OUTPUT:

We are in the method!
We are in the block, 2

```

Everything is an object in ruby, except for blocks.


Because of this, blocks can't be saved to variables and don't have all the powers and abilities of a real object. For that, we'll need procs. A  proc is a saved block. They are great for keeping your code dry.

Now that you have a basic understanding of Ruby blocks and procs, go use them. They are a wonderful way of creating synchronicity in your code. Good hunting.