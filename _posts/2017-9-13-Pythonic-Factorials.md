---
title: Factorials! in python
type: post
---
## Simple Python Factorial Script

Sure, you could `import math` and use the `math.factorial(x)` function, but what fun is there in that?
Here, I have a rudimentary factorial script using only the built-in functions that has some pythonic error catching (try/except) built in. 

##What is Pythonic Error Catching?

Hold on...

##What is Pythonic Code?

First, what is Python Code? It is generally accepted to be code that abides by [The Zen of Python](https://www.python.org/dev/peps/pep-0020/). According to the Abstract:

>Long time Pythoneer Tim Peters succinctly channels the BDFL's guiding principles for Python's design into 20 aphorisms, only 19 of which have been written down.

Archived in the archives of Python.org is the [original exchange](https://mail.python.org/pipermail/python-list/1999-June/001951.html) between Tim Peters, Patrick Phalen, Fredrik Lundh and "Guido".

###The Zen of Python (originally, "The Python Way), PEP 20

` 
1. Beautiful is better than ugly.
2. Explicit is better than implicit.
3. Simple is better than complex.
4. Complex is better than complicated.
5. Flat is better than nested.
6. Sparse is better than dense.
7. Readability counts.
8. Special cases aren't special enough to break the rules.
9. Although practicality beats purity.
10. Errors should never pass silently.
11. Unless explicitly silenced.
12. In the face of ambiguity, refuse the temptation to guess.
13. There should be one-- and preferably only one --obvious way to do it.
14. Although that way may not be obvious at first unless you're Dutch.
15. Now is better than never.
16. Although never is often better than *right* now.
17. If the implementation is hard to explain, it's a bad idea.
18. If the implementation is easy to explain, it may be a good idea.
19. Namespaces are one honking great idea -- let's do more of those!`

##Again, What is Pythonic Error Catching?

`10. Errors should never pass silently`

A few decent rules of error catching from [Joel Spolsky](https://www.joelonsoftware.com/2003/10/13/13/) talking specifically about Java and C++:

1. Never throw an exception of my own
2. Always catch any possible exception that might be thrown by a library I'm using on the same line as it is thrown and deal with it immediately

In my script below, I almost break Joel's rule number one. When checking for positive numbers I was tempted to say something like
```python
if num < 0:
    raise MyException("Positive Integers only...")
``
Obviously, I found I better way!

Although my script has room for improvement in the way of best practices for programming, I do believe I met **Pythonic Code** criteria number 10. 

##Check it out and enjoy!



```python
def factorial(val):
    try:
        f = 1 
        for i in list(range(1,val+1)):
            f = f*i
        return f
    except:
        print("Whoa! Please try again....")

def get_factorial(val):
        try:
            if( val == 0 ):
                return 1
            else:
                return factorial(val)
        except Exception:
            print("Not sure what you did! Please try again....")
def main():
    while True:
        try:
            num = int(input("Enter an integer:"))
            if num >= 0:
                print(get_factorial(num))
            else:
                print("Positive integers only...")
        except Exception:
            print("No valid integer! Please try again....")
main()       
```

>`    Enter an integer:6
    720
    Enter an integer:5
    120
    Enter an integer:-5
    Positive integers only...
    Enter an integer:0
    1
    Enter an integer:er
    No valid integer! Please try again....
`
