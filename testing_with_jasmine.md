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

##why?

##how?
