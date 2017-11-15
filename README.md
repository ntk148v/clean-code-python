# Clean Code in Python :snake:

:sparkler: Inspired by [Ryan McDermott's repository](https://github.com/ryanmcdermott/clean-code-javascript)

:sparkler: Refer [Mariano Anaya's presentation in EuroPython2016](https://ep2016.europython.eu/media/conference/slides/clean-code-in-python.pdf)

:sparkler: Refer [What is Clean Code](https://theholyjava.wordpress.com/2012/12/15/what-is-clean-code-quotes/)

<!-- TOC -->

- [Clean Code in Python :snake:](#clean-code-in-python-snake)
    - [Introduction / \_\_init\_\_.py](#introduction-initpy)
        - [What is Clean Code?](#what-is-clean-code)
            - [Conclusion](#conclusion)
            - [So, how to measure good and clean code?](#so-how-to-measure-good-and-clean-code)
        - [What is not Clean Code? (Dirty Code)](#what-is-not-clean-code-dirty-code)
    - [How to produce Clean Code? Write Pythonic code.](#how-to-produce-clean-code-write-pythonic-code)
        - [Follow coding standard!](#follow-coding-standard)
        - [Naming](#naming)
        - [Comment](#comment)
        - [Follow KISS - Keep It Simple, Stupid](#follow-kiss---keep-it-simple-stupid)

<!-- /TOC -->

## Introduction / \_\_init\_\_.py

> Writing code is an art as much as a science.

### What is Clean Code?

* [Ward Cunningham](https://en.wikipedia.org/wiki/Ward_Cunningham), inventor of Wiki and Fit, co-inventor of Extreme
  Programming.

> You know you are working with clean code when each routine you read turns
> out to be `pretty much what you expected`. You can call it beautiful code
> when the code also makes it look like the language was made for the problem.

* [Bjarne Stroustrup](https://en.wikipedia.org/wiki/Bjarne_Stroustrup),
  inventor of C++.

> I like my code to be elegant and efficient. The logic should be
> `straightforward` and make it hard for bugs to hide ... Clean code `does one
> thing` well.

* [Grady Booch](https://en.wikipedia.org/wiki/Grady_Booch), author of
  Object-Oriented Analysis and Design with Applications.

> Clean code is simple and direct. Clean code reads like well-written prose.
> Clean code never obscures the designers’ intent but rather is full of crisp
> abstractions and straightforward lines of control.

#### Conclusion

Clean code:

- Does one thing well
- Evert f(x) does what you'd expect
- Easily accessible to others (straightforward, clear intent, good
  abstractions, good names)

#### So, how to measure good and clean code?

![measure good code](https://ssujan.files.wordpress.com/2015/11/cleancode.gif)

### What is not Clean Code? (Dirty Code)

- Complex, obfuscated code
- Duplicated code
- Code that is not intention revealing

## How to produce Clean Code? Write Pythonic code.

> These bellow sections are generic coding conventions. Not Python only.

### Follow coding standard!

It doesn't matter what the standard is, follow one.

This makes it easy for people who come into the project later to write code
exactly the same way as you wrote it. It aslo makes code easier to read, as
the variable/method names are consistent, as is the formatting/layout of code.

[PEP 8 - Style Guide for Python Code](https://www.python.org/dev/peps/pep-0008/) gives coding conventions
for Python code comprising the standard library in the main Python
distribution. This is a **must-read** & **should-follow** documentation when start
developing Python.

### Naming

Take care about names! We name everything: variables, methods, arguments,
classes, packages.

- Use pronounceable & meaningful names.
- Do not be redundant.
- Stick to [PEP8 naming convention](https://www.python.org/dev/peps/pep-0008/#naming-conventions). I won't be
  list all these conventions here, it's redundant (check No2). You can easily
  get it from the above link.

### Comment

Code is read a million times, written once. Clean code should be **self-documenting**!

Bad code:

```python
# Init a & b to 0
a = 0
b = 0

# Read a & b
a, b = readvalues()

# Add a and b
c = a + b

# Divide c by 2
d = c /2

# Print result
print(d)
```

You can see that the code above has a lot of comments which have a WTF
quality. Naming is bad too.

Good code:

```python
number1 = 0
number2 = 0

number1, number2 = readvalues()

sum = number1 + number2
average = sum / 2
print(average)
```

No comments, but it's clear what I am doing because everyone knows what an
average is.

So when should you use comments? When it's not clear from the code, or when
the reader may be confused. Keep in mind that there is always someone reading
the code.

```python
# NOTE(kiennt): Code doesn't work correctly when having special_case, so we
#               have to add this extra checks
if special_case:
    do_fancy_thing
```

This comment is useful because 6 months from now, you'll forget why you wrote
this code.

![understand your own codes](https://i.pinimg.com/564x/b0/fd/2c/b0fd2c7e11f37c1c0335b1c6436d0710.jpg)

Regarding Comment, one thing I want to remind you:

- Don't comment bad code, rewrite it!
- `Clean` all bad comment out, litterally!

![commented out](https://4loc.files.wordpress.com/2009/11/lines_of_code.jpg)

### Follow KISS - Keep It Simple, Stupid

- Don't put all in one method. It's really really hard to understand.
- Meaning & logic separation

```python
def elapse(year):
    days = 365
    if year % 4 == 0 or (year % 100 == 0 and year % 400 == 0): # Hold on, I need more time to understand it.
        days += 1
    for day in range(1, days + 1):
        print('Day {} of {}' . format(day, year))

# Better!
def elapse(year):
    days = 365
    if is_leap(year):
        days += 1
    # ... Too lazy to write these again ...

def is_leap(year):
    # ... Lazy ...
```
