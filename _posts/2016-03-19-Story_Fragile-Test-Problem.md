---
layout: post
title: (Story) The Fragile Test Problem
---

The fragile test problem as story? Yeah, let's start ;)

So imagine there are two developers A and B working in different companies. A thinks writing tests is a bad practice, 
just a waste of time. He practiced some manual testing of all the code written by himself. B is the opposite of him. He 
thinks writing tests is a good practice, resulting in a more stable and safe product.

At one day a manager came to A and said: "Hey A, we need a piece of production code doing this and that... Use it into this and that class."

"No prob man!" was the answer.

```
public class FooA {
    public void bar() {
        // doing some magic here...
    }
}     
```

That was easy. He extended also class X and Y to use the FooA object and the bar method. After doing some manual testing 
he went home early.

The same happened to developer B. He developed exactly the same code but did writing unit tests, covered all possible 
test cases and also all lines of code. He left late the company that day.

```
public class FooATest {
    @Test
    public void shouldBarWithThisAndThat() {
        // test
    }
    @Test
    public void shouldBarWithThatAndThis() {
        // test
    }
    // a very lot more
}     
```
        
So the next morning arrived and the manager came again and said: "Hey A, lets throw an IOException in bar and handle it lovely."

"No prob man!" was the answer.

```
public class FooA {
    public void bar() throws IOException {
        // doing some magic here...
        // at some point throw the exception
    }
}     
```

He fixed also the usage in class X and Y and did a lovely try and catch. Some manual testing after lunch and he went 
home early that day. 

The same happened to developer B.

"Holy shit..." was his thought on that.

First he changed the hundreds of tests...

```
public class FooATest {
    @Test
    public void shouldBarWithThisAndThat() throws IOExcepion {
        // test
    }
    @Test(expected=java.io.IOException.class)
    public void shouldBarWithThatAndThis() {
        // test
    }
    // a very lot more...
}     
```

After that he changed the class FooA and also X and Y. He went home late that day.

Next morning arrived. "Hey A, what the hell is that IOException thing, change it to AbcException please."

"No prob man!" was the answer.

```
public class FooA {
    public void bar() throws AbcException {
        // doing some magic here...
        // at some point throw the exception
    }
}     
```

He also changed again X and Y and went home earlier then ever.

The same happened to developer B.

"F*cking sick..." was his thought on that. Okay he thought, something went wrong here... Changing FooA to throw an 
AbcException would cause so many compilation errors in the test classes again. He detected the "Fragile Test Problem".

So he changed the tests in that way:

```
public class FooATest {
    @Test
    public void shouldBarWithThisAndThat() throws Excepion {
        // test
    }
    @Test(expected=java.io.AbcException.class)
    public void shouldBarWithThatAndThis() throw Exception {
        // test
    }
    // a very lot more...
}     
```

Then he changed FooA and also tests and production code for X and Y. He went home late that day.

"Good morning A, we have different conditions now. Please remove that exception thing. We should'nt throw here something..."

"No prob man!" was the answer.

Faster than light, A changed the FooA and also X and Y. He went home so early he didn't does in the past. 

The same happened to developer B.

... but... on that day, he smiled :)

He just changed the test that expected AbcException to that:

```
public class FooATest {
    @Test
    public void shouldBarWithThisAndThat() throws Excepion {
        // test
    }
    @Test
    public void shouldBarWithThatAndThis() throw Exception {
        // test
    }
    // a very lot more...
}     
```

Then he changed FooA, tests and classes for X and Y. After this small change he run all of the tests. He reached full 
test coverage in FooA, in X and also in Y. 

"Could you assure that the software will work well?" the manager asked him.

"Yes, it will. All tests passed!"

"Good news for you, go home early today, cya!"
 
B went home early that day and got a nice rest.

The next morning arrived... Screaming, crying in the company of developer A. The whole system was broken. There was a 
mistake in FooA the whole night! The shares became worthless... Too bad. Never heard about that company again. It 
disappeared quickly. 

What happened that morning in developer B's company? 

"Good news B! Our competitor was down the whole night! Their shares became worthless now. It was a good point that you test everything and also handled the Fragile Test Problem!"

 