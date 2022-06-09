Information is all around us.

In the world of software, the ways that we choose to organize our information is half the battle. Here’s the thing though: there are so many ways to solve a problem. And when it comes to organizing our data, there are lots of tools that could work for the job. The trick is knowing which tool is the right one to use.

Regardless of which language we start coding in, one of the first things that we encounter are data structures, which are the different ways that we can organize our data; variables, arrays, hashes, and objects are all types of data structures. But these are still just the tip of the iceberg when it comes to data structures; there are a lot more, some of which start to sound super complicated the more that you hear about them.

One of those complicated things for me has always been linked lists. I’ve known about linked lists for a few years now, but I can never quite keep them straight in my head. I only really think about them when I’m preparing for (or sometimes, in the middle of) a technical interview, and someone asks me about them. I’ll do a little research and think that I understand what they’re about, but after a few weeks, I forget them again. The whole thing is pretty inefficient, and it all stems from the fact that I know they exist, but I don’t fundamentally understand them! So, it’s time to change that and answer the question: what on earth is a linked list, anyway?

Linear data structures
If we really want to understand the basics of linked lists, it’s important that we talk about what type of data structure they are.

One characteristic of linked lists is that they are linear data structures, which means that there is a sequence and an order to how they are constructed and traversed. We can think of a linear data structure like a game of hopscotch: in order to get to the end of the list, we have to go through all of the items in the list in order, or sequentially. Linear structures, however, are the opposite of non-linear structures. In non-linear data structures, items don’t have to be arranged in order, which means that we could traverse the data structure non-sequentially.


Linear versus non-linear data structures
We might not always realize it, but we all work with linear and non-linear data structures everyday! When we organize our data into hashes (sometimes called dictionaries), we’re implementing a non-linear data structure. Trees and graphs are also non-linear data structures that we traverse in different ways, but we’ll talk more about them in more depth later in the year.

Similarly, when we use arrays in our code, we’re implementing a linear data structure! It can be helpful to think of arrays and linked lists as being similar in the way that we sequence data. In both of these structures, order matters. But what makes arrays and linked lists different?

Memory management
The biggest differentiator between arrays and linked lists is the way that they use memory in our machines. Those of us who work with dynamically typed languages like Ruby, JavaScript, or Python don’t have to think about how much memory an array uses when we write our code on a day to day basis because there are several layers of abstraction that end up with us not having to worry about memory allocation at all.

But that doesn’t mean that memory allocation isn’t happening! Abstraction isn’t magic, it’s just the simplicity of hiding away things that you don’t need to see or deal with all of the time. Even if we don’t have to think about memory allocation when we write code, if we want to truly understand what’s going on in a linked list and what makes it powerful, we have to get down to the rudimentary level.

We’ve already learned about binary and how data can be broken up into bits and bytes. Just as characters, numbers, words, sentences require bytes of memory to represent them, so do data structures.

When an array is created, it needs a certain amount of memory. If we had 7 letters that we needed to store in an array, we would need 7 bytes of memory to represent that array. But, we’d need all of that memory in one contiguous block. That is to say, our computer would need to locate 7 bytes of memory that was free, one byte next to the another, all together, in one place.

On the other hand, when a linked list is born, it doesn’t need 7 bytes of memory all in one place. One byte could live somewhere, while the next byte could be stored in another place in memory altogether! Linked lists don’t need to take up a single block of memory; instead, the memory that they use can be scattered throughout.


Memory allocation in static versus dynamic data structures
The fundamental difference between arrays and linked lists is that arrays are static data structures, while linked lists are dynamic data structures. A static data structure needs all of its resources to be allocated when the structure is created; this means that even if the structure was to grow or shrink in size and elements were to be added or removed, it still always needs a given size and amount of memory. If more elements needed to be added to a static data structure and it didn’t have enough memory, you’d need to copy the data of that array, for example, and recreate it with more memory, so that you could add elements to it.

On the other hand, a dynamic data structure can shrink and grow in memory. It doesn’t need a set amount of memory to be allocated in order to exist, and its size and shape can change, and the amount of memory it needs can change as well.

By now, we can already begin to see some major differences between arrays and linked lists. But this begs the question: what allows a linked list to have its memory scattered everywhere? To answer this question, we need to look at the way that a linked list is structured.

Parts of a linked list
A linked list can be small or huge, but no matter the size, the parts that make it up are actually fairly simple. A linked list is made up of a series of nodes, which are the elements of the list.

The starting point of the list is a reference to the first node, which is referred to as the head. Nearly all linked lists must have a head, because this is effectively the only entry point to the list and all of its elements, and without it, you wouldn’t know where to start! The end of the list isn’t a node, but rather a node that points to null, or an empty value.


Parts of a linked list: it’s all just a bunch of nodes, really.
A single node is also pretty simple. It has just two parts: data, or the information that the node contains, and a reference to the next node.

If we can wrap our heads around this, then we’re halfway there. The way that nodes work is super important, and super powerful, and could be summarized as this:

A node only knows about what data it contains, and who its neighbor is.

A single node doesn’t know how long the linked list is, and it may not necessarily even know where it starts, or where it ends. All a node is concerned with is the data it contains, and which node its pointer references to — the next node in the list.

And this is the very reason why a linked list doesn’t need a contiguous block of memory. Because a single node has the “address” or a reference to the next node, they don’t need to live right next to one another, the way that the elements have to in an array. Instead, we can just rely on the fact that we can traverse our list by leaning on the pointer references to the next node, which means that our machines don’t need to block off a single chunk of memory in order to represent our list.

This is also the explanation for why linked lists can grow and shrink dynamically during a program’s execution. Adding or removing a node with a linked list becomes as simple as rearranging some pointers, rather than copying over the elements of an array! However, there are also some drawbacks to linked lists that I’m not mentioning to you just yet — but more on those next week.

For now, we’ll just bask in the glory of how cool linked lists are!

Lists for all shapes and sizes
Even though the parts of a linked list don’t change, the way that we structure our linked lists can be quite different. Like most things in software, depending on the problem that we’re trying to solve, one type of linked lists might be a better tool for the job than another.

Singly linked lists are the simplest type of linked list, based solely on the fact that they only go in one direction. There is a single track that we can traverse the list in; we start at the head node, and traverse from the root until the last node, which will end at an empty null value.

But just as a node can reference its subsequent neighbor node, it can also have a reference pointer to its preceding node, too! This is what we call a doubly linked list, because there are two references contained within each node: a reference to the next node, as well as the previous node. This can be helpful if we wanted to be able to traverse our data structure not just in a single track or direction, but also backwards, too.

For example, if we wanted to be able to hop between one node and the node previous without having to go back to the very beginning of the list, a doubly linked list would be a better data structure than a singly linked list. However, everything requires space and memory, so if our node had to store two reference pointers instead of just one, that would be another thing to consider.


Different types of linked lists
A circular linked list is a little odd in that it doesn’t end with a node pointing to a null value. Instead, it has a node that acts as the tail of the list (rather than the conventional head node), and the node after the tail node is the beginning of the list. This organization structure makes it really easy to add something to the end of the list, because you can begin traversing it at the tail node, as the first element and last element point to one another. Circular linked lists can start to get really crazy because we can turn both a singly linked list and a doubly linked list into a circular linked list!

But no matter how complicated a linked list is, if we can remember the fundamentals of a node and how it works and how the different pointer references in our list are structured, there’s no linked list we can’t tackle!

Next week, in part 2 of this series, we’ll sink our teeth into the space time complexity of linked lists, and how they compare to their cousin, the array. I promise that it’s actually a lot more fun than it sounds!

Resources
If you think linked lists are super cool, check out these helpful resources.

Differences between Arrays and Linked Lists, Damien Wintour
Data Structures: Arrays vs Linked Lists, mycodeschool
Linked Lists: The Basics, Dr. Edward Gehringer
Introduction to Linked Lists, Dr. Victor Adamchik
Data Structures & Implementations, Dr. Jennifer Welch
Static Data Structures vs. Dynamic Data Structures, Ayoma Gayan Wijethunga

What’s a Linked List, Anyway? [Part 2]
This is the second installment in a two-part series on Linked Lists. If you haven’t read Part 1 of this series, I recommend checking that out first!

Linked lists are super simple, but they seem to have this reputation of being fairly complicated. Their reputation, as they say, precedes them.

But the more that I’ve read about this specific data structure, the more I’ve realized that it’s not actually linked lists that are confusing, but rather, it’s the logic that goes into deciding when and whether or not to use them that’s hard to wrap your head around.

If you’ve never worked with space time complexity (or if you’re like me, and still struggle to understand it sometimes), an interview question like, “Please tell me the how you’d implement X as a linked list, and what the possible drawbacks of that implementation are?” seems pretty…well, daunting, terrifying, near-impossible are all adjectives that come to mind.

So, let’s deconstruct that scary reputation that linked lists seem to always have. Instead of being intimidated, we’ll break them down and figure out what makes them useful, and when we might want to consider implementing them.

Hey, so, what even is Big O?
Most of us have probably heard the term “Big O Notation”, even if we had no idea what it meant the first time that we heard someone use it. My personal experience with it has always been in the context of designing algorithms (or being asked to evaluate the efficiency of an algorithm). But Big O is really all over and omnipresent within computer science.

The reason for this is that computer science — and effectively, anything that we code — is all about efficiency and tradeoffs. Whether you’re building software as a service, choosing a front end framework, or just trying to make your code DRY and more elegant, that’s what all of us are striving towards: being efficient with our software, and choosing things that are important to what we’re building, all while being aware of the tradeoffs that we’ll ultimately have to make.

The same goes for Big O Notation, but on a much lower level. Big O Notation is a way of evaluating the performance of an algorithm.

There are two major points to consider when thinking about how an algorithm performs: how much time it requires at runtime given how much time and memory it needs.

One way to think about Big O notation is a way to express the amount of time that a function, action, or algorithm takes to run based on how many elements we pass to that function.

For example, if we have a list of the number 1–10, and we wanted to write an algorithm that multiplied each number by 10, we’d think about how much time that algorithm would take to multiply ten numbers. But what if instead of ten numbers, we had ten thousand? Or a million? Or tens of millions? That’s exactly what Big O Notation takes into account: the speed and efficiency with which something functions when its input grows to be any (crazy big!) size.

I really love the way that Parker Phinney describes what Big O notation is used for in his awesome Interview Cake blog post. The way that he explains it, Big O Notation is all about the way an algorithm grows when it runs:

Some external factors affect the time it takes for a function to run: the speed of the processor, what else the computer is running, etc. So it’s hard to make strong statements about the exact runtime of an algorithm. Instead we use big O notation to express how quickly its runtime grows.

If you do a little bit of research on Big O Notation, you’ll quickly find that there are a ton of different equations used to define the space and time complexity of an algorithm, and most of them involve an O (referred to as just “O” or sometimes as “order”), and a variable n, where n is the size of the input (think back to our our ten, thousands, or millions of numbers).

As far as linked lists go, however, the two types of Big O equations to remember are O(1) and O(n).


Basic Big O Notation Equations
An O(1) function takes constant time, which is to say that it doesn’t matter how many elements we have, or how huge our input is: it’ll always take the same amount of time and memory to run our algorithm. An O(n) function is linear, which means that as our input grows (from ten numbers, to ten thousand, to ten million), the space and time that we need to run that algorithm grows linearly.

For a little contrast, we can also compare these two functions to something starkly different: an O(n²) function, which clearly takes exponentially more time and memory the more elements that you have. It’s pretty safe to say that we want to avoid O(n²) algorithms, just from looking at that crazy red line!

Growing a linked list
We already know what linked lists are made of, and how their non-contiguous memory allocation makes them uniquely different from their seemingly more popular cousin, the array.

So how do they work, exactly? Well, just like with an array, we can add elements and remove elements from a linked list. But unlike arrays, we don’t need to allocate memory in advance or copy and re-create our linked list, since we won’t “run out of space” the way we might with a pre-allocated array.

Instead, all we really need to do is rearrange our pointers. We know that a linked list is made up a single node, and a node always contains some data and, most importantly, a pointer to the next node or null. So, all we need to do in order to add something to our linked list is figure out which pointer needs to point to where.

For simplicity’s sake, we’ll work with a singly linked list in these examples. We’ll start with the simplest place we can insert an element into a linked list: at the very beginning. This is fairly easy to do, since we don’t need to go through our entire list; instead we just start at the beginning.

First, we find the head node of the linked list.
Next, we’ll make our new node, and set its pointer to the current first node of the list.
Lastly, we rearrange our head node’s pointer to point at our new node.
That’s it, we’re done! Well, almost. This looks easy, and it is — just as long as we do those three steps in the right order. If we accidentally end up doing step 3 before step 2, we end up in a bit of a mess. The reason being that if we point our head node to the new node before connecting the new, still-to-be-inserted, node to the rest of the list that comes afterwards, we’d end up in a cyclical structure, with only two nodes, and we’d effectively lose all of our other data in the list. Talk about a bad day!

Still, that process isn’t too hard to implement (and hopefully shouldn’t be too difficult to code) once you can remember those three steps.

Inserting an element at the beginning of a linked list is particularly nice and efficient because it takes the same amount of time, no matter how long our list is, which is to say it has a space time complexity that is constant, or O(1).


Inserting elements at the beginning and end of a linked list
But inserting an element at the end of a linked list is a different story. The interesting thing here is that the steps you take to actually do the inserting are the exact same:

Find the node we want to change the pointer of (in this case, the last node)
Create the new node we want to insert and set its pointer (in this case, to null)
Direct the preceding node’s pointer to our new node
However, there’s an added complexity here: we’re not adding something to the beginning of the list, at the head node. Nope — instead, we’re adding something after the last node. So we will need to find the last node. Which means that we’ll need to traverse through the entire linked list to find it. And we know that linked lists are distributed, non-contiguous in memory, which means that each node will live at a totally different “address” in memory! So traversing is going to take time — it’s going to take more time with the more nodes we have.

Hopefully, we can start to see what kind of space time complexity this type of inserting will leave us with: a linear O(n). If we had a linked list of 100 nodes, that might not actually take that long. Even a 1000 might be pretty fast. But imagine if we wanted to add an element to the end of a linked list with a billion items! This insert algorithm would take as much time as the number of elements in our list, which, depending on our list, could be a very bad day for us.

To list or not to list?
No human is perfect, and neither is a linked list. Here’s the thing: sometimes, a linked list can be really awesome — for example, when you want to insert or remove something at the beginning of the list. But, as we’ve learned, they can sometimes be…less than ideal (imagine having a million nodes and just wanting to delete the last one!)

Even if you don’t have to work with them every day, it’s useful to know just enough about data structures like linked lists so that you can both recognize them when you see them, and know when to reach for them when the time is right.

A good rule of thumb for remember the characteristics of linked lists is this:

a linked list is usually efficient when it comes to adding and removing most elements, but can be very slow to search and find a single element.

If you ever find yourself having to do something that requires a lot of traversal, iteration, or quick index-level access, a linked list could be your worst enemy. In those situations, an array might be a better solution, since you can find things quickly (a single chunk of allocated memory), and you can use an index to quickly retrieve a random element in the middle or end of the list without having to take the time to traverse through the whole entire thing.


When to use an array versus a linked list
However, if you find yourself wanting to add a bunch of elements to a list and aren’t worried about finding elements again later, or if you know that you won’t need to traverse through the entirety of the list, a linked list could be your new best friend.

For the longest time, I never knew what linked lists were. And when I finally did learn about them, I didn’t know what on earth they would ever be used for. Now that I realize what they do well, I can see both their benefits and drawbacks. And if the time ever comes, I’ll know when to reach for them to help me out.

Hopefully, you’re with me on this and feel the same way about linked lists, too!

Resources
If you think that space time complexity and linked lists are dope, you might think that the below links are, also, quite dope. And perhaps even helpful! Some of these links were recommended in Part 1 of this series, but you’ll find that they apply to Part 2, as well.

Happy listing!

A Beginner’s Guide To Big O Notation, Rob Bell
Big O Cheat Sheet, Eric Rowell
Ruby’s Missing Data Structure, Pat Shaughnessy
When to use a linked list over an array/array list?, StackOverflow
Data Structures: Arrays vs Linked Lists, mycodeschool
Static Data Structures vs. Dynamic Data Structures, Ayoma Gayan Wijethunga
