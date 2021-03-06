# Chapter 11. Associative Containers

## Exercise 11.1:
>Describe the differences between a map and a vector.

`map` is an associative container whereas `vector` is a sequence container

## Exercise 11.2
>Give an example of when each of list, vector, deque, map, and set might be most useful.

- list : anytime when a doubly-linked list is required.
- vector : anytime when a dynamic array is required.
- deque : [An answer from Stack Overflow](http://stackoverflow.com/questions/3880254/why-do-we-need-deque-data-structures-in-the-real-world).

1. A nice application of the deque is storing a web browser's history. Recently visited URLs are added to the front of the deque, and the URL at the back of the deque is removed after some specified number of insertions at the front.
2. Another common application of the deque is storing a software application's list of undo operations.
3. One example where a deque can be used is the A-Steal job scheduling algorithm.[5] This algorithm implements task scheduling for several processors. A separate deque with threads to be executed is maintained for each processor. To execute the next thread, the processor gets the first element from the deque (using the "remove first element" deque operation). If the current thread forks, it is put back to the front of the deque ("insert element at front") and a new thread is executed. When one of the processors finishes execution of its own threads (i.e. its deque is empty), it can "steal" a thread from another processor: it gets the last element from the deque of another processor ("remove last element") and executes it. - Courtesy Wikipedia
- map : dictionary.
- set : when to keep elements sorted and unique.

## [Exercise 11.3](ex11_03_04.cc)
>Write your own version of the word-counting program.

## [Exercise 11.4](ex11_03_04.cc)
>Extend your program to ignore case and punctuation. For
example, “example.” “example,” and “Example” should all increment the same
counter.

## Exercise 11.5
>Explain the difference between a map and a set. When might you use one or the other?

[A nice answer on Stack Overflow](http://stackoverflow.com/questions/16286714/advantages-of-stdset-vs-vectors-or-maps)

Both std::set and std::map are associative containers. The difference is that std::sets contain only the key, while in std::map there is an associated value. Choosing one over the other depends mainly on what the task at hand is. If you want to build a dictionary of all the words that appear in a text, you could use a `std::set<std::string>`, but if you also want to count how many times each word appeared (i.e. associate a value to the key) then you would need an `std::map<std::string,int>`. If you don't need to associate that count, it does not make sense to have the int that is unnecessary.

## Exercise 11.6
>Explain the difference between a set and a list. When might you use one or the other?

[list vs set](http://stackoverflow.com/questions/2302681/c-stl-list-vs-set)
**List**

1.Searching (linear time).
2.Inserting, deleting, moving (takes constant time).
3.Elements may be ordered.
4.Elements may be sorted.
5.Elements may be duplicate.

**Set**

1.Searching (logarithmic in size).
2.Insert and delete (logarithimic in general).
3.Elements are un-ordered.
4.Elements are always sorted from lower to higher.
5.Elements are unique.

## [Exercise 11.7](ex11_07.cc)
>Define a map for which the key is the family’s last name and
the value is a vector of the children’s names. Write code to add new
families and to add new children to an existing family.

## [Exercise 11.8](ex11_08.cc)
>Write a program that stores the excluded words in a vector
instead of in a set. What are the advantages to using a set?

[vector vs set](http://stackoverflow.com/questions/8686725/what-is-the-difference-between-stdset-and-stdvector)
1.No matter what elements you add or remove (unless you add
a duplicate, which is not allowed in a set), it will always
be ordered.

2.A vector has exactly and only the ordering you explicitly
give it. Items in a vector are where you put them. If you put
them in out of order, then they're out of order; you now need
to sort the container to put them back in order.

3.However, if you are constantly inserting and removing items
from the container, vector will run into many issues.

4.The time it takes to insert an item into a vector is proportional
to the number of items already in the vector. The time it takes
to insert an item into a set is proportional to the log of the
number of items. If the number of items is large, that's a huge
difference. Log(100, 000) is 17; that's a major speed improvement.
The same goes for removal.

## Exercise 11.9
>Define a map that associates words with a list of line numbers on which the word might occur.

## Exercise 11.10
>Could we define a map from vector<int>::iterator to int? What about from list<int>::iterator to int?
In each case, if not, why not?

## Exercise 11.11
>Redefine bookstore without using decltype.

## Exercise 11.12
>Write a program to read a sequence of strings and ints, storing each into a pair.
Store the pairs in a vector.

## Exercise 11.13
>There are at least three ways to create the pairs in the program for the previous exercise.
Write three versions of that program, creating the pairs in each way. Explain which form you
think is easiest to write and understand, and why.

## Exercise 11.14
>Extend the map of children to their family name that you wrote for the exercises in § 11.2.1 (p. 424)
by having the vector store a pair that holds a child’s name and birthday.

## Exercise 11.15
>What are the mapped_type, key_type, and value_type of a map from int to vector<int>?

## Exercise 11.16
>Using a map iterator write an expression that assigns a value to an element.

## Exercise 11.17
>Assuming c is a multiset of strings and v is a vector of strings, explain the following calls.
Indicate whether each call is legal:
```cpp
copy(v.begin(), v.end(), inserter(c, c.end()));
copy(v.begin(), v.end(), back_inserter(c));
copy(c.begin(), c.end(), inserter(v, v.end()));
copy(c.begin(), c.end(), back_inserter(v));
```

## Exercise 11.18
>Write the type of map_it from the loop on page 430 without using auto or decltype.

## Exercise 11.19
>Define a variable that you initialize by calling begin() on the multiset named bookstore from § 11.2.2 (p. 425).
Write the variable’s type without using auto or decltype.

## Exercise 11.20
>Rewrite the word-counting program from § 11.1 (p. 421) to use insert instead of subscripting.
Which program do you think is easier to write and read? Explain your reasoning.

## Exercise 11.21
>Assuming word_count is a map from string to size_t and word is a string, explain the following loop:
```cpp
while (cin >> word)
	++word_count.insert({word, 0}).first->second;
```

## Exercise 11.22
>Given a map<string, vector<int>>, write the types used as an argument and as the return value for
the version of insert that inserts one element.

## Exercise 11.23
>Rewrite the map that stored vectors of children’s names with a key that is the family last name
for the exercises in § 11.2.1 (p. 424) to use a multimap.

## Exercise 11.24
>What does the following program do?
```cpp
map<int, int> m;
m[0] = 1;
```

## Exercise 11.25
>Contrast the following program with the one in the previous exercise
```cpp
vector<int> v;
v[0] = 1;
```

## Exercise 11.26
>What type can be used to subscript a map? What type does
the subscript operator return? Give a concrete example—that is, define a map
and then write the types that can be used to subscript the map and the type
that would be returned from the subscript operator.

## Exercise 11.27
>What kinds of problems would you use count to solve?
When might you use find instead?

## Exercise 11.28
>Define and initialize a variable to hold the result of calling
find on a map from string to vector of int.

## Exercise 11.29
>What do upper_bound, lower_bound, and equal_range return when you pass
them a key that is not in the container?

## Exercise 11.30
>Explain the meaning of the operand pos.first->second
used in the output expression of the final program in this section.

## Exercise 11.31
>Write a program that defines a multimap of authors and
their works. Use find to find an element in the multimap and erase that
element. Be sure your program works correctly if the element you look for is
not in the map.

## Exercise 11.32
>Using the multimap from the previous exercise, write a
program to print the list of authors and their works alphabetically.

## Exercise 11.33
>Implement your own version of the word-transformation program.

## Exercise 11.34
What would happen if we used the subscript operator instead of find in the transform function?

## Exercise 11.35
>In buildMap, what effect, if any, would there be from rewriting
```
trans_map[key] = value.substr(1);
```
as
```
trans_map.insert({key, value.substr(1)})?
```

## Exercise 11.36
>Our program does no checking on the validity of either
input file. In particular, it assumes that the rules in the transformation file are
all sensible. What would happen if a line in that file has a key, one space,
and then the end of the line? Predict the behavior and then check it against
your version of the program.

## Exercise 11.37
>What are the advantages of an unordered container as
compared to the ordered version of that container? What are the advantages
of the ordered version?

## Exercise 11.38
>Rewrite the word-counting (§ 11.1, p. 421) and wordtransformation (§ 11.3.6, p. 440)
programs to use an unordered_map.
