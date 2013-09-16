
----

# Introduction

<div class="important">

The following exercises are intended to be used to warm up your fingers, rather than
your brain. These should be run through quickly to get you used to using your
development environment.

</div>

## Variables

In Haskell you can define a variable with the `=` sign.

Variables can be defined at the top-level (no-indentation):

~~~{data-language=haskell data-filter=./resources/scripts/check.sh}
myVariable = 2
~~~

Variable names should start with a lowercase letter and contain no spaces, or special characters, besides underscores, numbers, and `'`.

Some examples of variable names are:

* `a`
* `my_name`
* `data43'`

```instruction
Define your own variable.
```

~~~{data-language=haskell .answer data-filter=./resources/scripts/check.sh}
x = "hello"
~~~

```instruction
What is an example of an invalid variable name?
```

~~~{ data-language=haskell .answer .nocheck }
invalid-variable = 123
~~~

## Type Signatures

You can annotate a definition with a valid type-signature:

~~~{data-language=haskell data-filter=./resources/scripts/check.sh}
myVariable2 :: Int
myVariable2 = 1
~~~

```instruction
Give your variable a type-signature.
```

## String Literals

String literals look familiar:

~~~{data-language=haskell data-filter=./resources/scripts/check.sh}
myString :: String
myString = "hello world"
~~~

```instruction
Define a variable containing a string.
```

## Tuples

Tuples look like this:

~~~{data-language=haskell data-filter=./resources/scripts/check.sh}
myTuplePair :: (Int, String)
myTuplePair = (1,"hello")

myTupleTrio :: (Int, String, Int)
myTupleTrio = (1,"hello",3)
~~~

They can be used to group multiple, differently-typed (heterogeneous) values.

```instruction
Define a variable containing a tuple.
```

## Functions

Functions are a core part of Haskell. Function definitions look like this:


~~~{data-language=haskell .nocheck} 
myFunction :: ... -> ...
myFunction x y ... = ...
~~~

If a function `f` takes something of type `a` and returns something of type `b` we write the type signature as:

~~~{data-language=haskell .nocheck}
f :: a -> b
~~~

For example:

~~~{data-language=haskell data-filter=./resources/scripts/check.sh}
myAdd :: Int -> Int -> Int
myAdd x y = x + y
~~~

`myAdd` takes two numbers and returns the result of the addition of those two numbers.


```instruction
Define a function `myMultiply` that multiplies 3 numbers.
```

```instruction
Give your function a type-signature
```

~~~{data-language=haskell .answer data-filter=./resources/scripts/check.sh}
myMultiply :: Int -> Int -> Int -> Int
myMultiply x y z = x * y * z
~~~

## Lists

List are a commonly used data-structure in Haskell. Everything in a list has the same type (they are homogeneous).

Lists are built using the infix data-constructor `(:)` (pronounced "cons"). They also have a compact notation using `[...]`.

List literals look like:

~~~{data-language=haskell data-filter=./resources/scripts/check.sh}
list1 :: [Int]
list2 :: [Int]
list3 :: [String]

list1 = [1,2,3]
list2 = 1 : 2 : []
list3 = "hello" : "world" : []
~~~

More information about why lists can be used the way that they are is
contained in the [ADTs](#adts-algebraic-data-types) chapter.

```instruction
Define a variable containing a list.
```

```instruction
Give your variable a type-signature.
```

You can deconstruct a list by pattern matching the head and tail like so:

~~~{data-language=haskell .nocheck}
f (x:xs) = ...
~~~

```instruction
Define a function to get the first element of a list.
```

Note: In `Prelude` this function is called `head`.

~~~{.answer data-language=haskell data-filter=./resources/scripts/check.sh}
myHead (x:xs) = x -- This is a partial function, Beware!
~~~

```instruction
Define a variable containing the first element of your list.
```

~~~{.answer data-language=haskell .nocheck} 
myFirstElement = myHead myList
~~~

### Define Length

```instruction
Define a function that takes a list and returns the length.
```

~~~{data-language=haskell data-filter=./resources/scripts/check.sh}
-- In Haskell type-signature syntax, this is written as:
myLength :: [a] -> Int
myLength = undefined
~~~

Your solution should have the form of:

~~~{data-language=haskell .nocheck}
myLength []     = ...
myLength (x:xs) = ...
~~~

Things to consider:

* What is the length of an empty list? (the base case)
* What is the length of xs?

~~~{.answer data-language=haskell data-filter=./resources/scripts/check.sh}
mylength []     = 0
mylength (x:xs) = 1 + mylength xs
~~~

### Define `myMap`

```instruction

  
Define a function that takes a function from a to b "a -> b",
and a list of as "[a]", and returns a list of bs "[b]".
```

Things to consider:

* What is the type-signature of myMap?
* What is the base-case of myMap?

~~~{.answer data-language=haskell data-filter=./resources/scripts/check.sh}
myMap :: (a -> b) -> [a] -> [b]
myMap f [] = []
myMap f (x:xs) = f x : myMap f xs
~~~

## Fun List Functions

For your reading pleasure, here are some definintions of common functions:

~~~{data-language=haskell data-filter=./resources/scripts/check.sh}
myFilter f []     = []
myFilter f (x:xs) = if f x then x : myFilter f xs
                           else     myFilter f xs

myFold f z []     = z
myFold f z (x:xs) = f x (myFold f z xs)

myReverse []     = []
myReverse (x:xs) = myReverse xs ++ [x]

myElem e []     = False
myElem e (x:xs) = if e == x then True
                            else myElem e xs
~~~

See if you can determine the type-signatures for these functions.

```open
An open-ended question:

What is a good balance between safety and expressiveness in a
programming-language?
```
