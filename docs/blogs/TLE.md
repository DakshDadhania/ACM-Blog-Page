# Make your I/O fast(est)

C++ developers usually get accustomed to using  _std::cin_  and  _std::cout_  for standard I/O operations, but they aren’t the fastest ones out there. If you are feeling lazy to change your code, you can just add the statements given below and enjoy the speed boost.

The first statement disables the sync between C and C++ style I/O, so this may cause unknown errors if you combine them. For competitive coding, it’s usually not required to use both so you can use it without any worries.

The second statement unties  _std::cin_  with  _std::cout_. Whenever one of the streams is used, the other is flushed, but when you untie them, they no longer flush each other, which results in better performance. Of course, you can always use your old C friends,  _scanf_, and  _printf_. They are faster than  _std::cin_  and  _std::cout_  by about three times, but when compared to unsynchronized  _std::cin_  and  _std::cout_  they don’t give much of a performance boost.

Want it to be even more fast? Are you taking integer input? Oh, then you are in luck! Just copy this function, and you can take integer inputs in the fastest, thread-safe way.

The function given above reads each character and converts them into an integer. This method is free from a lot of system calls that  _scanf_  has to make, like deducing the type of input.

You must be wondering why I wrote “the fastest, thread-safe way.” Well, because there is a faster way, but that makes it thread-unsafe. Want to use it? Replace  _getchar()_  with  _getchar_unlocked()_  and experience the beast. In competitive programming environments, you don’t need to worry about being thread-safe unless you are doing concurrency related tasks, so go ahead with it!

How do you believe what I say without any proof? Well, here it is. The different methods were benchmarked, and the results are presented below. If you want to look at the code used in the benchmark, I have uploaded it to a GitHub repository, which you can find  [here](https://github.com/sudo-panda/bm-stdin).

![cin vs. cin_wo_sync vs. scanf vs. fastscan vs. fastscan_unlocked](https://miro.medium.com/max/1050/1*yqyJZLmkFnqmhx3im7pBfA.png)

Comparison of std::cin vs. other input methods

# Faster Vectors

While vectors are fantastic because of their expandability, but the same attribute makes them slow too.  _std::vector_  is implemented as a dynamic array, which means that each time it needs to increase the size of the array, it creates another array double the size and then copy the elements from the previous array. If you know the size of the vector before you add items, reserving the space eliminates the overhead required to copy the elements because it creates an array at least as big as the reserved size.

Where max is the number of elements you are going to store in the vector.

Adding a reserve makes your code about 1.2x faster.

![Time taken with reserve vs. without](https://miro.medium.com/max/1050/1*PyeZf006H6c0BbtuCc-kdg.png)

Comparison between  [the time taken with and without reserve](https://quick-bench.com/q/TB1uVdxd47R0NHYnhi5UYkbRc8U)

Again C style arrays or  _std::array_  is faster than using a vector any day, but its size has to be known at compile-time and thus isn’t always feasible to use. So vectors are your best bet, and it’s better to reserve the space beforehand.

Another surprising thing about  _std::vector_  is the  _at()_  function. It seems to do the same thing as subscript operator  _[]_  but when the performance is measured it is actually 3.1 times slower.

![at() vs. []](https://miro.medium.com/max/1050/1*nY183v5ijwCe29Mpn6fF5A.png)

Comparison between  [using at() function and subscript operator []](https://quick-bench.com/q/S_P0ZC7SDtlhywn8U1reCBzKoH8)

That can do a lot of damage to the time taken by your program. The reason being is that the at operator has builtin checks for out of range values that the subscript operator doesn’t, so if you give a value that is out of range it might give you a segmentation fault or cause unknown errors without telling you what has gone wrong while at will throw an exception.

One final thing that you should know about  _std::vector_  is that you should never copy an  _std::vector_  to another manually using a loop and  _push_back()_, rather you should use assignment operator  _=_. The difference in speed is huge as apparent by the chart below.

![Loop with push_back() vs. =](https://miro.medium.com/max/1050/1*YTl9oshtSTENXYTIh_vgfg.png)

Comparison between  [using a loop and push_back() vs. assignment operator =](https://quick-bench.com/q/E59edUiE8xtSB1HT6tUQei9nCc8)

This difference in performance is caused because when you are doing assignment it knows the size of the vector it is copying, and needs to call the memory manager only once to create the assigned vector’s space and copy all the elements unlike the  _push_back()_  operation which makes a call to the manager for every element.

# Don’t just add, append

The fastest way to work with strings in C++ would be to use C style strings, i.e. character arrays, equivalent performance to character arrays, but one mistake programmers frequently make is to use the  _+_  operator to append to a string. The reason it is not suitable to use is that it creates another character array of the total size of both the operand strings and copies the first one to the array while concatenating the other to the newly created array. What you should do instead is use the  _append()_  function, or it’s equivalent  _+=_  operator:

OR

Using the  _+=_  operator instead of + operator is better for any class that supports it. This helps in reducing the time taken and memory to create a new object and copy the first and then add the second object to it.

![= + vs. +=](https://miro.medium.com/max/1050/1*fJCo9ydqrK-NTaUFFXemfA.png)

Comparison between  [using + operator and += operator](https://quick-bench.com/q/mPKfyqvMfbAGwpxoikYPVq23yXQ)

Also, when using  _std::string_  or any other class, it’s best to initialize it using the constructor than using the assignment operator.

# You don’t need std::list

If you don’t know about  _std::list_, we are done here, but if you do and you are thinking about using it, then think again.  _std::list_  is a doubly-linked list, so the advantage it gives over  _std::vector_  is that it can remove and insert at any position in constant time. That can seem great when you need it, but vectors can be cached by the processor so sequential access is faster than when using  _std::list_.

If you have to remove several elements from the middle of a vector, you can use  _erase_if()_.  _erase_if()_  was introduced in C++ 20, but you can combine  _remove_if()_  and  _erase()_  together to create your custom  _erase_if()_  for previous versions of C++.

You might see there is a variable called predicate. The predicate is a function that takes in an element from the vector and returns a bool. Typically, each time you erase an item from a vector, the ones after it are shifted forward, but if you use an  _erase_if()_  construct, the shifting is done after all the elements have been deleted, so it is great for removing multiple elements. An example predicate is given below.

If you use the above function in the  _erase_if()_  expression:

It will remove all the zeros from the vector v.

If you want to see a comprehensive benchmark between  _std::vector_  and  _std::list_  you can take a look at this beautiful post by Baptiste Wicht  [here](https://baptiste-wicht.com/posts/2012/11/cpp-benchmark-vector-vs-list.html). After reading the post, you might have a question in mind, “If  _std::list_  is worse than using  _std::vector_, then why is it even there in the standard library?” It’s because there are a few places where lists are better, i.e., when the elements being stored in the list are huge and not a lot of them can be fit in the cache, lists can dominate over vectors.

# Befriend unordered_map

_std::map_  is maintained as a binary search tree, and the main advantage of using map over unordered_map is that it sorts the elements according to the key. One other benefit of using  _std::map_  over  _std::unordered_map_  is that it supports pairs out of the box. However, the difference between O(log n) and O(1) can be the difference between a TLE and an AC solution. So let’s look at how you can create your hash function for a pair of integers.

This structure tries to return a unique integer for every pair it gets. You just need to plug this struct into your unordered_map and voila! Your hash table now supports  _std::pair<int, int>_.

You can Google many more hash functions suited for different needs and choose your flavor.

_std::map_  should be only used when sorting of elements is required other than that  _std::unordered_map_  is your friend. The same goes for  _std::set_  and  _std::unordered_set_.

Also, you can use reserve with  _std::unordered_map_  too. In my benchmarks, it sped up the process of adding elements to the hash table 1.3x times.

![With reserve vs. without](https://miro.medium.com/max/1050/1*gymB-gusgnVxMgF3Vs9b-g.png)

Comparison between  [creating a hash table with and without reserve](https://quick-bench.com/q/jXUkHzaxTqgtfawX4enHFvIlE9E)

If you want a faster hash table than unordered_map and you or your CP platform uses g++, there is excellent news. You can use  [___gnu_pbds::gp_hash_table_](https://gcc.gnu.org/onlinedocs/libstdc++/ext/pb_ds/gp_hash_table.html)! It isn’t part of the standard library but has almost the same interface as std::unordered_map but is much faster.

![unordered_map vs. gp_hash_table](https://miro.medium.com/max/1050/1*wn9Rk_4cJnPeEcAlOYCD3g.png)

Comparison between  [unordered_map and gp_hash_table](https://quick-bench.com/q/niMmYdpamgXT82k_2-P9TjL34hs)

___gnu_pbds::gp_hash_table_  is faster than  _std::unordered_map_  because it drops a lot of many unnecessary features that STL has to retain. If you want a better explanation, you can look at the comment  [here](https://codeforces.com/blog/entry/60737?#comment-446357), and if you want more insight, you can see this post  [here](https://codeforces.com/blog/entry/60737).

There is one more optimization that you can do for  _std::unordered_map_  that is setting its  _max_load_factor_  to 0.25. The load factor is defined as the ratio of the number of elements in the hash table to the number of buckets. Keeping  _max_load_factor_  at 0.25 means at least ¾ of the buckets will be empty. This reduces collisions in the hash table; therefore, the lookup time but also increases the space taken by your hash table. I couldn’t find much of a performance gain when using it, but you can try it if  _std::unordered_map_  seems to perform worse than you expected, and you can’t switch to  _gp_hash_table_.

# Conclusion

To summarize:

1.  Use  _fastscan()_  for the fastest integer input and  _std::cin_  without sync for the rest.
2.  Use reserve with  _std::vector_  and  _std::unordered_map_  as much as possible.
3.  Use assignment operator to copy vectors and operator  _[]_  instead of  _at()_  function
4.  Use addition assignment operator instead of addition and then assignment for strings as well as other classes that support it.
5.  Don’t use  _std::list_  use  _std::vector_  instead.
6.  Use  _std::map_  and  _std::set_  when the keys need to be sorted otherwise use  _std::unordered_map_  or  _std::unordered_se_t, respectively.

There are a lot more optimizations that you can achieve in C++. An example of a small one would be to use bit shift operators instead of multiplying or dividing by powers of 2, as shown  [here](https://quick-bench.com/q/JzsL5BgA-4bIXIfDDEh98ATD4Zg).

I would encourage you to explore more on your own, benchmark any such tips you may find, and maybe comment them down below. I had fun making this post and hope you had fun reading it too and learned something new.

**_P.S._:**  I have assumed that the code is compiled without any compiler optimization because the primary target audience of this article is competitive coders.

# References

Apart from the ones linked in the article here are some sites and books that I referred from:

-   [Fast IO Optimization in C++](https://www.hackerearth.com/practice/notes/fast-io-optimization-in-c/)  _by Arun Prasad_
-   [6 Tips to supercharge C++11 vector performance](https://www.acodersjourney.com/6-tips-supercharge-cpp-11-vector-performance/)  by  _Deb Haldar_
-   [CPP Optimizations Diary](https://github.com/facontidavide/CPP_Optimizations_Diary)  _by Davide Faconti_
-   Optimized C++: Proven Techniques for Heightened Performance  _by Kurt Guntheroth_
-   C++ Reference
-   And of course loads and loads of Stack Overflow searches
