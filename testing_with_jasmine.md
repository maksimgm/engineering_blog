#JavaScript Testing With Jasmine

Most software developer know that they should write tests for their code. However, nine times out of ten, they don't, because it means learning yet another concept. In this piece, I will walk you through testing with Jasmine.

Jasmine is an open source testing framework for JavaScript which aims to run on any JavaScript-enabled platform. It is heavilly influenced by other testing frameworks, such as [ScrewUnit](https://github.com/nkallen/screw-unit), [JSpec](https://github.com/liblime/jspec), and [RSpec](https://github.com/rspec/rspec).

##Behavior Driven Development
Before I dive into BDD, let's understand some fundamentals about testing. 

### Test Driven Development
TDD is the process of writing and running your test. Following TDD makes it possible ot have a high test coverage. Test coverage refers to the percentage of code that is tested, so the higher the better. Additionally TDD, reduces the likelihood of having bugs in your tests, which can otherwise be difficult to track down.

The process consists of the following steps:

1. Start by writing a test.
2. Run the test and watch it fail. If the test does not fail, then you know you have a bug in your test.
3. Write a minimal amount of code required to make the test pass.
4. Run the test to check the new test passes.
5. Refactor your code.
6. Repeat

Now that you understand the process of TDD, let's move on to BDD.

BDD is a bit more complex, because it typically requires a team of developers, rather than a single developer, to practice it fully. Here are a few BDD practices:

* Establishing goals of different stakeholders required for an idea to be implmented, and involving stakeholders in this implementation through outside-in software development.

* Using examples to describe the behavior of different units of code

* Automating said examples to provide rapid feedback and [regression testing](https://en.wikipedia.org/wiki/Regression_testing).

Before I plunge into Jasmine, let's understand some basic testing terminology:

**Unit testing**- Low level tests to check functionality of classes, methods, or functions. This is what I will be focusing on. Unit tests run fast.

**Acceptance/Feature tests**- High level tests conducted to make sure all requirements are met. Acceptance tests run slow.

**Integration/function/service-level testing**- Testing between unit and acceptance tests. In most cases this will involve testing RESTful APIs.

![pyramid of types of tests](http://blog.codeclimate.com/images/posts/rails-testing-pyramid.png)


##Installing Jasmine
First, we will need to install the jasmine gem.

	$ npm install -g jasmine

Second, let's make sure it works, create a directory called, `jasmine_testing`, then type: 

	$ jasmine init

This will generate the following path in our `jasmine_testing` directory:

	spec/support/jasmine/jasmine.json

This file informs Jasmine where to find the tests and any helper files.

Now that we've set up Jasmine, let's learn the syntax and write our first test.

##Learning the syntax

Jasmine tests are primarilly made up of two parts; `describe` blocks and `it` blocks. Let's take a look at how they work.

	describe("fahrenheit_to_celsius_test",function(){
	  it("converts 100 fahrenheit to 			
	  	celsius",function(){
		// Setup
	    var fahrenheit = 100;
    	var result = temp_converter.fahrenheit_to_celsius(fahrenheit);
	    // Checking the result
    	expect(result).toBeCloseTo(37.778,3);
	  });
	});
	
Both `describe` and `it` are functions that take two parameters: a text string and a function. The idea is to make the text string as humanly readable as possible. Notice that both the `describe` and the `it` block form sort of a sentence which gives the developer an idea of what that block tests.

Think of the `describe` block as a general container and the `it` block as a place where you can set up the code nessecary to for your test. Once your `it` block is setup, you'll continue by writing the `expect` function. In this function you will pass in whatever code you are testing. Notice how in my example, I expect the result from the `temp_converter.fahrenheit_to_celsius` function to return a close to 37.778.

In your `jasmine_testing` directory, run the test and watch it fail. i.e.

	$ jasmine
	
Next we will need to write the appropriate