---
layout: post
title:  "Elegance of Unix Tools"
category: p_learning
---

Unix command line tools are fascinating to me always. I love the simplicty and power of the tools that help us to do text processing and to see the resource usage in the OS - be it disk, memory or CPU. Ability to pipe the output of one command to the other as input is powerful to the extent that we can do large data anlaysis with command line tools itself.

One of the design principles from Unix is <i>"Make each program do one thing well. To do a new job, build afresh rather than complicate old programs by adding new features"</i>. For example, if we look at the <i>uniq</i> command it does one thing well - take a sorted input and remove the duplicates from the input. This can be useful when we combine with the <i>sort</i> command.

Let's look at a more concrete use case. Suppose you want to find out the most frequently used word in a document. we can do the following. 

<pre>
$grep -oe "[a-zA-Z]\+" input.txt | 
   sort | 
   uniq -c | 
   sort -rnk 1 |
   head -n 1
</pre>

In the above example, here is what we do.
1. search for and extract the words from input.txt file using grep
2. sort the words by consuming the words from the previous step
3. print the count and unique words by consuming sorted words from the previous step. (count word) pair will be printed every line
4. Perform numerical sort (using the -n option) on the data from step 3
5. output only the first line from step 4

In my opinion, we should teach these tools during our early years of software development itself. Not everyone will have to use these tools because many GUI tools are available to perform the same task. However, in a production envirionment these tools come in handy. 





