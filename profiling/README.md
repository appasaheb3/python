
# **cProfile**

**Python's cProfile module is a built-in profiler that helps you analyze the performance of your Python programs. It provides detailed information about the time spent executing different functions or methods, allowing you to identify bottlenecks and optimize your code.**

```
import time

def add(x,y):
    result=0
    result+=x
    result+=y
    return result

def fact(n):
    result=1
    for i in range(1,n+1):
        result *=i
    return result

def do_stuf():
    result=[]
    for x in range(1000000):
        result.append(x**2)
    return result

def waste_time():
    time.sleep(5)
    print("Hello")
    
if __name__=="__main__":
    r1=add(100,500)
    print(r1)
    r2=fact(70000)
    print(r2)
    r3=do_stuf()
    print(r3)
    waste_time()
```
### Run Above Code
```
python -m cProfile test.py
```

### Result Will like
```
# Output of above code and below are the stats

 1000012 function calls in 19.366 seconds

   Ordered by: standard name

   ncalls  tottime  percall  cumtime  percall filename:lineno(function)
        1    0.000    0.000   19.366   19.366 mytest.py:1(<module>)
        1    0.639    0.639    0.798    0.798 mytest.py:15(do_stuf)
        1    0.000    0.000    5.002    5.002 mytest.py:21(waste_time)
        1    0.000    0.000    0.000    0.000 mytest.py:3(add)
        1    2.226    2.226    2.226    2.226 mytest.py:9(fact)
        1    0.000    0.000   19.366   19.366 {built-in method builtins.exec}
        4   11.340    2.835   11.340    2.835 {built-in method builtins.print}
        1    5.002    5.002    5.002    5.002 {built-in method time.sleep}
  1000000    0.159    0.000    0.159    0.000 {method 'append' of 'list' objects}
        1    0.000    0.000    0.000    0.000 {method 'disable' of '_lsprof.Profiler' objects}
```
