---
toc: true
title: "Asymptotic Notation"
date: 2020-11-12T21:57:40+08:00
categories:
  - Blog
tags:
  - Computer Science
  - Data Structures
  - Algorithms

---

You've probably heard people talk about a fast or efficient algorithm for executing your particular task, but what exactly does it mean for an algorithm to be fast or efficient? 
Well, it's not talking about a measurement in real time, like seconds or minutes. This is because computer hardware and software vary drastically. My program might run slower than yours, because I'm running it on an computer with components than yours.
It's like comparing dogs and cats.

So, since we can't directly compare the runtimes of programs in seconds or minutes, how do we compare 2 different algorithms regardless of their hardware or software environment? To create a more uniform way of measuring algorithmic efficiency, computer scientists and mathematicians have devised concepts for measuring the asymptotic complexity of a program and a notation called **'Big Ohnotation'** for describing this.

  ## O(n)

![O(n)](/assets/images/blogs/asymptotic-notation/image1.png)

For example, imagine counting the number of characters in a string the simplest way by walking through the whole string letter-by-letter and adding 1 to a counter for each character. This algorithm is said to run in linear time with respect to the number of characters, 'n' in the string. In short, it runs in **O(n)**. Why is this? Well, using this approach, the time required to traverse the entire string is proportional to the number of characters.

Counting the number of characters in a 20-character string is going to take twice as long as it takes because you have to look at all the characters and each character takes the same amount of time to look at. As you increase the number of characters, the runtime will increase linearly with the input length.

## O(1)

![O(1)](/assets/images/blogs/asymptotic-notation/image2.png)

Now, imagine if you decide that linear time, **O(n)**, just wasn't fast enough for you? Maybe you're storing huge strings, and you can't afford the extra time it would take to traverse all of their characters counting one-by-one. So, you decide to try something different. What if you would happen to already store the number of characters in the string, say, in a variable called 'len,' early on in the program, before you even stored the very first character in your string? Then, all you'd have to do now to find out the string length, is check what the value of the variable is. You wouldn't have to look at the string itself at all, and accessing the value of a variable like len is considered an asymptotically constant time operation, or **O(1)**.

Well, it wouldn't matter how big you make the string, even a million characters long, all you'd have to do to find the string's length with this approach, is to read out the value of the variable len, which you already made.

Of course, there's a drawback. You spend extra memory space on your computer storing the variable and the extra time it takes you to do the actual storage of the variable, but the point still stands, finding out how long your string was doesn't depend on the length of the string at all. So, it runs in **O(1)** or constant time.

## Asymptotic Behavior

![Asymptotic Behavior](/assets/images/blogs/asymptotic-notation/image3.png)

As you can probably guess,there are many different big O runtimes to measure algorithms with. O(n)² algorithms are asymptotically slower than **O(n)** algorithms.That is, as the number of elements (n) grows, eventually **O(n)²** algorithms will take more time than **O(n)** algorithms to run. This doesn't mean **O(n)** algorithms always run fasterthan **O(n)²** algorithms, even in the same environment, on the same hardware. Maybe for small input sizes, the **O(n)²** algorithm might actually work faster, but, eventually, as the input size increases will eventually eclipse the runtime of the **O(n)** algorithm.

Just like any quadratic mathematical function will eventually overtake any linear function, no matter how much of a head start the linear function starts off with. If you're working with large amounts of data, algorithms that run in **O(n)²** time can really end up slowing down your program, but for small input sizes, you probably won't even notice.

  ##  Logarithmic Time "O(log n)"

Another asymptotic complexity is, logarithmic time, O(log n). An example of an algorithm that runs this quickly is the classic binary search algorithm, for finding an element in an already-sorted list of elements.

If you don't know what binary search does,
I'll explain it for you really quickly.

![Binary Search](/assets/images/blogs/asymptotic-notation/image4.png)

Let's say you're looking for the number 3 in this array of integers. It looks at the middle element of the array and asks, "Is the element I want greater than, equal to, or less than this?" If it's equal, then great. You found the element, and you're done. If it's greater, then you know the element has to be in the right side of the array, and you can only look at that in the future, and if it's smaller, then you know it has to be in the left side. This process is then repeated with the smaller-size array until the correct element is found.

![Logarithmic Time](/assets/images/blogs/asymptotic-notation/image5.png)

This powerful algorithm cuts the array size in half with each operation. So, to find an element in a sorted array of size 8, at most (log₂8), or 3 of these operations, checking the middle element, then cutting the array in half will be required, whereas an array of size 16 takes (log₂16), or 4 operations. That's only 1 more operation for a doubled-size array. Doubling the size of the array increases the runtime by only 1 chunk of this code. Again, checking the middle element of the list, then splitting. So, it's said to operate in logarithmic time, O(log n). But wait, you say, doesn't this depend on where in the list the element you're looking for is?

## Average (O) and Best (Ω) Case Scenarios

![Best Case Scenario(Binary Search)](/assets/images/blogs/asymptotic-notation/image6.png)

In the best case for binary search, our element is right there in the middle, and you get it in constant time, no matter how big the rest of the array is. The symbol used for this is Ω. So, this algorithm is said to run in **Ω(1)**. In the best case, it finds the element quickly, no matter how big the array is, but in the worst case, it has to perform (log n) split checks of the array to find the right element. Worst-case upper bounds are referred to with the big "O" that you already know. So, it's **O(log n)**, but **Ω(1)**.

![Best Case Scenario(Linear Search)](/assets/images/blogs/asymptotic-notation/image7.png)

A linear search, by contrast, in which you walk through every element of the array to find the one you want, is at best Ω(1). Again, the first element you want. So, it doesn't matter how big the array is. In the worst case, it's the last element in the array. So, you have to walk through all n elements in the array to find it, like if you were looking for a 3. So, it runs in O(n) time because it's proportional to the number of elements in the array.

![Average Case Scenario O(n)](/assets/images/blogs/asymptotic-notation/image8.png)

## Worst and Best Case Scenarios (Θ)

![Worst and Best Case Scenarios Θ](/assets/images/blogs/asymptotic-notation/image9.png)

One more symbol used is Θ. This can be used to describe algorithms where the best and worst cases are the same. That is, if we store it in a variable before we store the string and access it later in constant time. No matter what number we're storing in that variable, we'll have to look at it. The best case is, we look at it and find the length of the string. So Ω(1) or best-case constant time. The worst case is, we look at it and find the length of the string. So, O(1) or constant time in worst case. So, since the best case and worst cases are the same, this can be said to run in Θ(1) time.