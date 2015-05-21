# Sorting Networks
My C++11 solution to [/r/dailyprogrammer's intermediate problem #215](http://www.reddit.com/r/dailyprogrammer/comments/36m83a/20150520_challenge_215_intermediate_validating/?sort=new).

## [What are sorting networks?](http://en.wikipedia.org/wiki/Sorting_network)

## What does this program do?
Basically, this program verifies the sorting network given by the comparators in the text file. It does this by generating every binary string from 1 to 2<sup>number of wires</sup> ([zero-one principle](http://en.wikipedia.org/wiki/Sorting_network#Zero-one_principle)). Then, according to the configuration in the text file, we sort each string by swapping. Then we do another run to make sure the swaps did their jobs. If we find that there are still bits out of order, then we know we have an invalid sorting network. 

## Simple Explanation
Still don't grasp it quite yet? No problem. Let's take a look at our `sample1.txt`:
```
4 5
0 2
1 3
0 1
2 3
1 2
```
The first line of every text file contains: number of wires in network and the total number of comparators, respectively. The rest of the lines are just configuration of the comparators.
Given the configuration, the sorting network is laid out like this, with the left column being the wire numbers:

![Image](http://i.imgur.com/UfElsg6.png)

Now, a sorting network has input on the left hand side. Let's look at an example:

* Wire 0 has input number `4`.
* Wire 1 has input number `3`.
* Wire 2 has input number `1`.
* Wire 3 has input number `2`.

We'll start with wire 0. So as `4` traverse its path, it runs into the comparator. Wire 0 has a connection between itself and wire 2. That means we must **swap** the values if and only if the "top" wire is **greater** than the "bottom" wire. In this specific case it does and we swap `4` and `2` from their respective wires. If we continue this process, we will see that this specific sorting network is valid for any arbitrary input. 

Play around with the sample file. Maybe draw up another sorting network and create the corresponding text file and see how things work.

To get more detail about how a sorting network works, check out this video from Udacity: https://www.youtube.com/watch?v=UzdwAyfvcfY

## Usage
```shell-session
g++ -std=c++11 sort_network.cpp
./a.out <file>
```
## Sample Runs

```shell-session
$ time ./a.out challenge1.txt 
Invalid

real	0m0.012s
user	0m0.008s
sys	0m0.004s
$ time ./a.out challenge2.txt 
Valid

real	0m0.290s
user	0m0.286s
sys	0m0.004s
$ 
```
