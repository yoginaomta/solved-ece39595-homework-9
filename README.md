Download Link: https://assignmentchef.com/product/solved-ece39595-homework-9
<br>
In this homework we’ll convert a sequential program to a program that executes items in a work queue in parallel.

<strong>What you need to do: </strong>

<ol>

 <li>Have the QuickSort function inherit from the Command abstract class, and implement the pure virtual functions declared in Command.</li>

 <li>Write a DotProduct class that also inherits from the Command abstract class and implements its pure virtual functions. DotProduct will have two constructors, a zero arg and a constructor that takes an int that is the length of the <em>a</em> and <em>b</em> arrays whose dot product will be taken.  DotProduct also needs to implement operator&lt;&lt;(…). I’ll include sample output that will make it clear what the output should be.</li>

 <li>A WorkerQueue class that implements a work queue, where work items are shared_ptr&lt;Command&gt; objects. The queue should be implemented using a C++ std::vector.</li>

</ol>

In addition to any needed constructors (I used a single zero-arg constructor) you will need to implement a <em>get()</em> function that returns a shared_ptr&lt;Command&gt; of some entry in the queue, and removes that entry from the queue.  Removing the entry from the queue should be properly synchronized using a std::mutex and a std::lock_guard.

You will also need to implement a <em>put()</em> function, that takes a std::shared_ptr&lt;Command&gt; as an argument and returns a void, that adds the std::shared_ptr&lt;Command&gt; to the work queue. The add of the shared pointer to the queue should be properly synchronized.

<ol start="4">

 <li>In the file main.cpp, the worker function should be uncommented and the write that is done with identify( ) should be called. You should hold a lock different than the lock used for WorkQueue when calling identify so that there is not a race on std::ostream.</li>

</ol>

In the main function, we will time the time it takes to

<ol>

 <li>add eight std::shared_ptr&lt;Command&gt; objects to the work queue. Four will point to dot products and four will point to quick sorts.</li>

 <li>Start four threads that run the worker function, passing your work queue as an argument.</li>

 <li>Wait until all four threads have finished.</li>

</ol>

<ol start="5">

 <li>Print out the execution time, the number of threads, etc., as shown in the sample output.</li>

</ol>

When compiling, use the -pthread option at the end of your list of files or you will get linker errors. You will need the following include files:  &lt;vector&gt; for std:vector, &lt;chrono&gt; for timing (you will also need to put “using namespace std:chrono” after the includes and any defines in your main.cpp file), &lt;memory&gt; for std::share_ptr, &lt;mutex&gt; for locks, plus the normal stuff.