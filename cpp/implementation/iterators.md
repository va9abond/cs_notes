Iterators are such a great concept. They completely decouple the container holding the data from the algorithms that operate on it. They are a great example of modularity, where two distinct systems operate together via shared auxiliary objects.
___
[cplusplus - iterators](https://cplusplus.com/reference/iterator/)
[ref](https://open-std.org/JTC1/SC22/WG21/docs/papers/2016/p0174r0.html#2.1:~:text=options%20are%20available.-,Recommendations%20for%20Deprecation,-There%20is%20likely)

1. step1 - how iterators works
	- before c++20
	- `std::..._iterator_tag`
	- after c++20
2. step2 - simple iterator implementation 
	- [article1](https://www.internalpointers.com/post/writing-custom-iterators-modern-cpp)
	- [article2](https://anderberg.me/2016/07/04/c-custom-iterators/#fn:2)
3. step3 - `const` and `non-const` iterators
4. step4 - `const` and `non-const` iterators implementation
	- way 1:
		inherit `non-constant` from `const`
	- way 2:
		```c++
		class iterator_base {
			using iterator = iterator_base<Ty>;
			using const_iterator = iterator_base<const Ty>;
			...
		};
		```


[ref](https://www.drdobbs.com/stl-generic-programming-writing-your-ow/184401417)

[ref](https://stackoverflow.com/questions/8054273/how-to-implement-an-stl-style-iterator-and-avoid-common-pitfalls/39767072#39767072)

[ref]()

[ref]()

[ref]()

