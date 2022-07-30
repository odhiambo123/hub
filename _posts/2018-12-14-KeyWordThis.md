---
layout: post
title: "Keyword This"
date: 2018-12-14
categories: JavaScript
---

when a function is invoked a new execution context is created
Remember not to confuse this with the object that we've been discussing.
The object sitting in memory that is a function has properties and methods.
It has a name property and a code property where the code lives.
But when that code is invoked and
execution context is created and put on the execution stack.
And that determines how that code is Run, is executed.
So think of the execution context
as focusing on that code portion of that function object.
What happens when I run the code in that code property?
So we know that an execution context is created.
Each executions context has this variable environment.
Where the variables created inside that function live.
It has a reference to its outer environment.
Its outer lexical environment, where it sits physically in the code,
which tells it how to look down the scope chain.
In other words, if I ask for a variable and
it's not there inside that function's variable environment.
It'll go out and out further, and all the way out until it reaches the global
environment looking for that variable or that function.
So it has that outer reference.
And we also know that in JavaScript engine every time
an execution context is created, that is every time a function is Run.
It gives us, without us having to create it, declare it or
anything, it gives us this variable called this, which can be useful.
And this will be pointing at a different object,
a different thing, depending on how the function is invoked.
This can cause a lot of confusion.
There are a few scenarios where this
will be changed depending on how the function is called.
For the JavaScript engine will decide that this should point to something different.
That the this keyword is a particular object or another,
depending on where the function is and how it's called.
So let's take a look at a couple of these scenarios, and
we'll see this again later in the course as well.
So, the this keyword.
I once again have my empty app.js file, and
we'll use some simple examples to explain what this,
the keyword this will be under certain circumstances.
Now you maybe thinking that you'd like to see some more concrete complete examples.
I agree.
As this course goes on especially toward the end, we'll look at far more complex
examples of the concepts that we're using in the real world and
in very popular JavaScript libraries and frameworks.
But I believe it's important first to understand the concept and
not get bogged down in the details of implementation of more complex examples.
So right now we're focusing on just
understanding what's happening under the hood with JavaScript.
And then later we'll build on that knowledge with more complex example.
For now, let's move on talking about this keyword.
We've already seen that this is immediately available, the keyword this.
Even at the global execution context level.
So I can run this, and inside the browser, it's going to show me the window object.
Because this points to the global object at this level in the code.
And inside the browser, the global object is,
as you might recall, the Window object.
Now let's look at another example, let's say I have a function.
I'll just call it a, and I'm going to log this.
And then, I'll invoke a.
Remember that invoking a, means run that code property
which contains all the lines of code inside the function.
And the first thing it does is create that execution context, and one of that
pieces of the puzzle is the creation of the keyword this.
So what will the keyword this be
inside the execution context that's created by invoking a?
Execution context for running the a function.
Now let's take a look.
It's also the Window object.
So when you create a function, the this keyword is still going to
point to the global object.
If you decided to use this, if you're simply invoking the function.
Similarly, if I use a function expression
to set up the object, and then set that equal to a variable.
Actually I mean this.
So, var b gets this function expression to declare it, to create it.
What will this be in that case?
Well, I'll go ahead and
invoke b, using the variable name to point to that function.
And it's still Window.
So whenever I create a function
that's simply a function expression or a function statement.
Creating a function at this level in the code,
then this will point to the global object.
And that's true even though there's actually
three execution contexts that we see here.
The global one, then the one that's created when a is invoked, and
another execution context that's created when b is invoked.
And in each of those cases, they get their own this keyword.
But in all those cases, the keyword points to the same address,
the same location in your computer's memory.
So they're all pointing at the global object.
Makes sense?
That means you could even do strange things like this.newvariable
let's say equals hello.
I've attached it to the global object.
So after I call a, I could actually console.log newvariable.
Cuz that's been created and using the dot operator,
I've attached a new variable to the global object.
And remember,
any variables attached to the global object, I can just reference like that.
I don't need to use the dot operator.
It just assumes I'm asking for a variable on the global object.
So I can refresh this and
actually see that hello, kind of strange.
If you don't understand what this keyword is pointing to and
you think you're somehow attaching this to the function, you're not.
You're actually crashing into the global namespace and
you could cause yourself a lot of problems.
So when you're just invoking the function, this points to the global variable.
However, you may have seen something that looks like this when learning JavaScript.
We're gonna talk about that later in the course about what circumstance
when you would use the this variable inside a function like this.
Now that said, what about an object method?
Let me create a little space here and I'll create a new object literal and
now that we understand function expressions,
I can do something that we haven't done before inside an object literal.
I can create a method.
Remember, if the value is a primitive, it's called a property.
And if the value a function, it's called a method.
So, I'll create a name-value pair.
I'll just call it name, so we can recognize the object and
I'll call it the c object and then a comma and I'll create a method.
I'll do log: so that's the name and
then the value I want to create a function object.
So, I'll just use a function expression.
An anonymous function, no name and
then I'll console.log this and
then I'll call c.log So
now I can invoke the function that was created inside this object literal,
which is attached to this log.
So this is the log method of the object c.
See that?
What will this turn out to be?
Remember every time a function is invoked, a new execution context is created and
the JavaScript engine decides what that keyword,
the keyword this should be pointing to.
In these other cases, it was the window object.
But in this case, it's a method on an object and
that means, see that there at the bottom?
In the case where a function is actually a method
attached to an object, this keyword becomes
the object that that method is sitting inside of c.
See that?
These functions, this keyword.
The JavaScript engine said, you're attached to an object.
So when you see, when you use the this keyword I'm going to
be pointing at that very object that contains you.
So I could actually say,
this.name = 'Updated c object'
And then when this is logged, see that?
I changed that property on this parent object,
the object that holds the function.
So that's useful.
I can mutate that is change the object,
that contains me if I'm a method of that object by using of this keyword.
You can imagine that can be very useful to be able to access other properties and
methods on the same object that a particular method lives on.
This is very common to use and it's neat.
Now there's one more thing to show you and
this a lot of people feel is a bug in JavaScript.
Now you might be saying, what do you mean a bug in JavaScript?
Well, JavaScript is a programming language and the engines and the language was
designed by people and so decisions were made about how things should work.
And in this one case, this decision a lot of people feel is wrong.
Let me show you.
Let's suppose that I create a function inside this method, we can do that right.
I'm gonna call it setname, I'll use a variable and
I'll set a function expression.
This time, I'll pass a variable to my function.
Let's say, new name.
I can do that.
And inside here, I'm gonna say this.name = newname.
So, I'm trying to update or
mutate my object with this newname.
And then let's say that here,
I'm going to go ahead and call setname and
I'll say 'Updated again!
The c object') and
then console.log(this) again.
So I mutate it and I should see 'Updated c object'.
I create a function that also, well when executed, create a new execution context.
And I would expect, personally that this keyword would
still point to the containing object,
because it's a function inside of a function, inside of an object.
And since this keyword points to the object, I would expect, well, one more
function down and it'll still point to the object and I can mutate it, change it.
So I would expect that after calling this setname function,
I'll see updated again the c object as the name on that second console.log.
Let's try it.
Well, that's a problem.
"Updated c object" and Updated c object".
Meaning, this ran, but
this didn't seem to do anything or did it.
Oh, let's try going back and taking a look
at the window object, the global object.
And if I take a good look, look at that.
See that?
That name property here was instead created and
added by the equals operator on the global object.
That means that this internal function, when its execution
context was created, the this key word points to the global object,
even though it's sitting kind of inside an object that I created.
I think that's wrong and a lot of people do, but
that's the way JavaScript works in this case and
there's not a lot we can do about it at this point.
So what can we do when I have this kind of scenario?
To make sure that I'm using the right object.
That this keyword isn't causing me to make an unintended error.
Well there's a very common pattern that we can use in this case.
And we'll understand it because We understand
that objects are set by reference.
Now that we understand that, we can understand this pattern.
I can simply say I'm going to set a variable.
I'll call it self.
Some people call it that, but I like self.
Because I'm inside this object.
And I'm going to set that equal to this.
It was the very first line of my object method.
So what happened right here?
Well, now we have a new variable called self, and
since these are objects, it's going to be set equal to by reference.
So self will be pointing at the same location in memory as the this keyword.
And right now, the this keyword on this line of code is pointing to
my whole object.
And then for sanity's sake, we simply use self everywhere where we normally
would have used this, even inside these sub-functions.
That way I don't have to think about, am I pointing to the right object?
This is still pointing.
The self variable is still pointing to the same location in memory as this.
So when I mutate it, when I change it, when I add something to it or change it or
whatever, it's going to update the appropriate thing,
in this case, my whole object.
So self, I can log that, and then when I look
at this new function that I created, and this gets executed right here.
I don't even worry about the this variable.
I simply say self.
So what's going to happen?
Well, self isn't declared inside this function.
So the JavaScript engine will look down the scope chain.
Where is this function sitting physically in the code?
Well, right inside here.
So we can see that'll it just go outside to the next area outside, the outer
lexical reference, and look for it, a variable called self and it will find it.
And so this right here, the self variable inside this function,
will end up being this one here.
And that's still pointing to my whole object.
So I can mutate my object here, as well.
So now, this should show up properly.
I have a proper reference to my object.
And then I just use it from there on out, just for sanity's sake, so
I don't have to think about it.
And then I'll mutate it, I'll change it.
And then I'll create a function, and
I'll call that function and that will mutate the object.
And I'll put it again.
So this time I should see, look at that.
That's proper.
That's what I expected.
So what did we learn?
We learned that no programming language is perfect.
They all have their quirks, and JavaScript certainly isn't an exception.
But there are patterns we can use to get around
any problems the programming language might have.
Now I also wanna make mention that this pattern you'll see very often if
you're working in any real-world JavaScript scenarios.
However, the let keyword, which will be an alternative
to the var keyword, is meant to clear some of these problems up.
So as that becomes available in modern browsers,
and depending on the kind of project you're working on,
if you're working on a web project and you don't have to worry about older browsers.
That's something that you'll soon start to be able to use,
and bonus lectures in this course will help with that, as time goes on.
But for now, realize that this pattern is a good one.
It is used quite often and is quite useful.
So we've seen the this key word.
It's the global variable, or
the global object, when just invoking a function like this.
And when the function is a method of an object,
the this keyword points to the object.
However, any internal functions have a problem.
So we can use this concept of setting a variable equal to this,
and then just carrying that with us the rest of the way to
make sure that we don't run across any unintentional errors,
or somehow throw things onto the global object that we didn't mean to.
All right, let's move on.
