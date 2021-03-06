# Time complexity of an Algorithm

When you have written some logic, you normally would not worry about its runtime. You assume that it runs efficiently as it was promised
by the underlying programming language. But sometimes it makes sense to dig a bit deeper and to understand how well your
algorithm might function in a certain environment. 

To calculate the time complexity, let us first make some assumptions! They are:

1. Your alg. runs on a single processor and it runs seuqentially
2. It could be a 32 bit machine or a 64 bit machine

So it is safe to assume that your **time complexity just depends solely on the input** that you give to your alg.

With this in mind, let us now define a hypothetical, made up model and here is how I would define it:

1. It takes 1 second to execute / run any arithmetic or logical operation
2. It takes 1 second to do assignments and 1 second to return from a function

Now we have to fit this hypothetical model into some sample programs so that we can calculate the total amount of time it takes, or
rather to put it in other words, we need to find the rate at which the time grows with respect to different inputs to a program!

Since I love and live Scala, I will give some Scala examples and fit my hypothetical model to it. Let us start simple - A function
to calculate the sum of two numbers:

```
def sum(a: Int, b: Int) = a + b
```

So by applying our hypothetical model to the sum function, we get the following total time to run the sum function:

| Operation     | Time         |
| ------------- | ------------- |
| Add a and b              | 1  |
| Return from the function | 1 |
| Total Time Taken | 2  |

So from the above table, we see the time coplexity of the sum function is 2. Never mind what the input is going to be, our sum algorithm
will have a **constant time complexity**!

Let us now proceed to another function that takes a List of elements and sums them up! 

```
def sumOfList(l: List[Int]): Int = l match {
  case x :: tail => x + sumOfList(tail) // if there is an element, add it to the sum of the tail
  case Nil => 0 // if there are no elements, then the sum is 0
}
```

I know there is a much simpler way to sum a List[Int] in Scala, but let us not get into confrontation mode and assume that this is
the best algorithm available to sum a List of Int's in Scala. Now let us apply our hypothetical time model to this sumOfList function!

Here we assume that the List is not empty and has atleast 2 elements in it!

| Operation     | Description  | Time taken for one run   | Number of executions |
| ------------- | ------------- | ------------- | ------------- |
| x + sum(tail)    | There is one addition and one return, so we need 2 seconds for one run | 2 | list.size times |
| case Nil     | If in case the List is empty, we return | 1 | |

So the total time taken can be derived as:

Total time is proportional to 2n where n is the number of times the execution happens, so mathematically we can write this as a linear function

```
T = an + b
```

Where a represents the number of times the execution happens and b is some constant that brings our proportionality into an equality!

So this is a classical linear function what we have just dereived for our sumOfList. Good so far! So these are our equations fo far:

```
Tsum = k                    ---- eq 1

TsumOfList = an + b         ---- eq 2

TsumOfMatric = an2 + bn + c ---- eq 3
```

eq 1 is a contstant

eq 2 is a linear function

eq 3 is a quadriatic function

If we now plot all this in a graph Input vs Time, we see the following:

![time-input-plot](https://github.com/joesan/random-documentation/blob/master/time-complexity-of-a-running-algorithm/time-input-plot.png
)

So in Asymptotic notation, this would mean the following:

```
eq 1 is O(1) - A constant time

eq 2 is O(n) - A linear time

eq 3 is O(n to the power 2) - A quariatic time
```

Hope this is clear enough!
