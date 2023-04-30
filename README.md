Download Link: https://assignmentchef.com/product/solved-cs-251-project-3-hashtables-and-heap
<br>
<h1>Part 1: Chaining Hashtable (30 points)</h1>




<strong>Hashtable with Separate Chaining: </strong>

Implement a generic Hashtable with ​<strong>Separate Chaining</strong>​. This means our hashtable maintains an ​<strong>array of Lists</strong>​, where the keys are stored by generating a hashvalue, obtained by:

<em> </em>

<strong><em>hashvalue = hashcode(key) % capacity</em></strong>

<em>                         </em>

This hashvalue is used to index the array, and the (key, value) pair is stored in the corresponding List at that index. Keys with same hashvalue are stored at the same index which means the same List.




<strong>Hashcode: </strong>​Hashcode follows the rule: if A and B are equal, then hashcode(A) = hashcode(B). You may use any hash function you like for part 1.




<strong>Functions to implement: </strong>

<ul>

 <li><strong>Hashtable(capacity):</strong>​ Accepts the capacity of the table as a parameter.</li>

</ul>

Initialize an array of length capacity then initialize the table with empty List at each index. Capacity is a prime number.

<strong> </strong>

<ul>

 <li><strong>get(key)</strong>​: Returns the value of the key if found, return null otherwise.</li>

</ul>

<strong> </strong>

<ul>

 <li><strong>put(key, value):</strong>​ Adds the (key, value) pair to the table. If key already present in the hashtable, overwrite the original value. Resize the hashtable if the load factor becomes greater than 0.5 after inserting this (key, value) pair. The new capacity should be the first prime number greater than twice the previous capacity and all the keys in the hashtable would need to be rehashed and stored in this new hashtable. In the provided framework, we hard code a list of prime numbers for you to use. ​<strong>You can assume you will never run out of prime numbers to use. </strong></li>

</ul>

<strong> </strong>

<ul>

 <li><strong>remove(key):</strong>​ Removes the key from the table, if it’s there. Return the value of the key if key exists in the hashtable, return null otherwise.</li>

</ul>




<ul>

 <li><strong>containsKey(key): </strong>​Returns whether the key is in the hashtable.</li>

</ul>




<ul>

 <li><strong>size():</strong>​ Returns the total number of (key, value) pairs in the table.</li>

</ul>




<ul>

 <li><strong>replace(key, value): </strong>​Replaces the value for the specified key only if it is currently mapped to some value. Return the previous value associated with the specified key, or null if there was no mapping for the key.</li>

</ul>




<ul>

 <li><strong>Any other function you like! Those extra functions will not be tested. Functions above are the only functions that will be tested. </strong></li>

</ul>




<strong>(Key, Value) Type: </strong>​Keys have type K and Values have type V.







<h1>Part 2: Hash Anagrams (30 points)</h1>

<strong> </strong>

We then play with anagrams using the hash table in Part 1. Your job is to design a hash function which results in the least collisions for non-anagrams and in all anagrams of the same letters mapping to the same hash index.




<strong>Anagram: </strong>​An anagram is a word or phrase formed by rearranging the letters of a different word or phrase, using all the original letters exactly once. e.g., “name” = “mean”, “debit card” = “bad credit”, etc…




<strong>Hashcode: </strong>​When we query the hash code for two anagrams, we want to ensure they are equal. Also, hash codes for non-anagrams should be distinct. However, we can tolerate some collisions for non-anagrams.




<strong>getCollision(int hashIndex): </strong>​You need to write a method getCollision()  to return the number of collisions (i.e., chain length) of the specified hash table index (0 &lt;= hash index &lt; <em>N </em>).




The input for this part is a sequence of words/phrases. The maximum number of characters for a word/phase is 32. You need to hash those words/phases into a hash table of size <em>N </em>. In a normal well-designed hash table, each hash index chain should have same number of entries. In this case however, a hash index chain should ideally have only anagrams of the same letters or only non-anagrams. It depends on the hash code function with which you accomplish this.




<strong>Competition: </strong>We will run a competition across the whole class of CS251. The program(s)​              producing the least number of collisions for non-anagrams and having no anagrams mixed with non-anagrams in a hash table entry wins!




<strong>Input /output file for part 1 and part 2: </strong>




Input format: Use String as key type and Integer as value type

<ul>

 <li>The first integer 1 or 2 indicates this is the input file for part 1 or 2;</li>

 <li>The second integer n implies that there are n lines below;</li>

 <li>The character ‘p’ (for put) followed by: key value. Call put(key, value). put this key, value pair to hashtable. Print previous value of the specified key in this hashtable, or null if it did not have one</li>

 <li>The character ‘g’ (for get) followed by a key. Call get(key) and print the value and value of the returned element separated by a space. Print “null” if key is not found.</li>

 <li>The character ‘r’ (for replace) followed by: key value. Call replace(key, value); Print previous value associated with the key. Print “null” if there was no mapping for the key;</li>

 <li>The character ‘d’ (for remove) followed by a key. Call remove(key). Print previous value associated with the key. Print “null” if there was no mapping for the key;</li>

 <li>The character ‘s’ (for size). Call size(). Print hashtable size()</li>

 <li>The character ‘c’ (for containsKey) followed by a key. Call containsKey(key). Print 1 if true, 0 if false.</li>

 <li>The character ‘m’ (for getCollision) followed by a integer index i. Print the chain length at that hash index — if empty, then print 0.</li>

</ul>




<table width="615">

 <tbody>

  <tr>

   <td width="268">Input</td>

   <td width="117"> </td>

   <td width="231">Expected output</td>

  </tr>

  <tr>

   <td width="268">1 9 p key1 5 g key1 g key2 r key2 7 r key1 7 sc key1 c key2 p key1 6 m 2</td>

   <td width="117">null 5 null null 511071</td>

   <td width="231"> </td>

  </tr>

 </tbody>

</table>

<strong>Note: the parameter 2 for m (getCollision) is a made-up number which happens to be hash index for key1 in this case. </strong>

<strong> </strong>

<h1>Part 3: Heap (40 points)</h1>

<strong> </strong>

A ​<strong><em>heap</em></strong>​ is a binary tree ​<em>T </em>​that stores a collection of elements with their associated keys at its nodes and that satisfies two properties:

<ul>

 <li><strong><em>Heap-Order Property</em></strong>​: In a heap ​<em>T </em>​, for every node ​<em>v </em>​other than the root, the key associated with <em>v </em>​ ​is greater than or equal to the key associated with ​<em>v</em>​’s parent;</li>

 <li><strong><em>Complete Binary Tree Property</em></strong>​<strong>: </strong>​A heap ​<em>T </em>​with height ​<em>h </em>​is a ​<strong><em>complete </em></strong>​binary tree, that is, levels 0,1,2,…,​<em>h</em>​−1 of ​<em>T </em>​have the maximum number of nodes possible (namely, level ​<em>i </em>has 2^i​ ​nodes, for 0 ≤ ​<em>i </em>​≤ ​<em>h </em>​− 1) and the nodes at level ​<em>h </em>​fill this level from left to right.</li>

</ul>




In this section you need to

<ul>

 <li>implement priority queue with an array-based heap.</li>

 <li>implement heap sort.</li>

</ul>

<strong> </strong>

<strong>(a) Implement priority queue </strong>

<strong> </strong>

The array-based binary tree representation is especially suitable for a complete binary tree <em>T </em>​ ​. We recall that in this implementation, the nodes of <em>T </em>​ ​are stored in an array <em>A </em>​ ​such that node <em>v </em>​ ​in <em>T </em>​is the element of ​<em>A </em>​with index equal to the level number ​<em>f </em>​(​<em>v</em>​) defined as follows:

<ul>

 <li>If ​<em>v </em>​is the root of ​<em>T</em>​, then ​<em>f</em>​(​<em>v</em>​)=1</li>

 <li>If <em>v </em>​ ​is the left child of node ​<em>u</em>​, then ​<em>f</em>​(​<em>v</em>​) = 2<em>f</em>​​(<em>u</em>​ ​)</li>

 <li>If <em>v </em>​ ​is the right child of node ​<em>u</em>​, then ​<em>f</em>​(​<em>v</em>​) = 2<em>f</em>​​(​<em>u</em>​)+1</li>

</ul>




With this implementation, the nodes of ​<em>T </em>​have contiguous indices in the range [1, ​<em>n</em>​] and the last node of <em>T </em>​ ​is always at index <em>n</em>​ ​, where <em>n </em>​ ​is the number of nodes of <em>T </em>​ ​.




Here is the ADT of a priority queue P:







Your implementation should include functionalities listed above.




(b) ​<strong>Implement heap sort </strong>




Heap sort include two phrases: construct a heap which takes O(n log n) operations, and destruct that heap which takes O(n log n) operations. To construct a heap, you need to iteratively read an entry ​<em>e</em>​ from the input file and use ​<em>insert(e)</em>​ to extend the heap. To destruct a heap, you need to iteratively call ​<em>removeMin() </em>​until the heap is empty. Sorted items should be ascending order.




Input format:

<ul>

 <li>The first integer 3 indicates this is the input file for part 3;</li>

 <li>The second integer n implies that there are n lines to follow;</li>

 <li>The character ‘i’ (for insert) followed by 1 integer. Insert this value into the heap;</li>

 <li>The character ‘m’ (for minimum). Call min() and print the value of the returned element. Print “empty” if heap is empty;</li>

 <li>The character ‘r’ (for delete). Call removeMin(); Print “empty” if heap is empty; The character ‘s’ (for sorted). Print the sorted contents of current heap.</li>

</ul>




<table width="615">

 <tbody>

  <tr>

   <td width="48"> </td>

   <td width="221">Input</td>

   <td width="117"> </td>

   <td width="231">Expected output</td>

  </tr>

  <tr>

   <td width="48">35i 7 i 5  i 3 rm</td>

   <td width="221"> </td>

   <td width="117">5</td>

   <td width="231"> </td>

  </tr>

  <tr>

   <td width="48">37mi 5 i 4 i 3 i 2 i 1 s</td>

   <td width="221"> </td>

   <td width="117">empty12345</td>

   <td width="231"> </td>

  </tr>

 </tbody>

</table>




<h1>Part 4: Programming Environment and Grading</h1>

<strong> </strong>

Assignments will be tested in a Linux environment. You will be able to work on the assignments using the Linux workstations in HAAS and LAWSON (use your username and password).




<strong>4A: Java </strong>

<ul>

 <li>Compiler we use: javac (v10.0.2)</li>

 <li>File to submit: HashTable.java, Heap.java</li>

</ul>




Your project must compile using the javac compiler (v10.0.2) on data.cs.purdue.edu. Main.java is provided to you so that you can generate output file on your own to see if your code works correctly, you may change it as your wish. We will run JUnit tests which looks like test/TestHashTable.java to grade your work. However, not all grading test cases are provided. You may write your own JUnit test cases.




<strong>Compiling process</strong>​: ​<strong>Following commands assume you are at project root and you have NOT changed project file structure! </strong>●    To compile Main:

javac src/*

<ul>

 <li>To run Main: java -cp src/ Main InputFilePath OutputFilePath</li>

</ul>

Note: You should replace InputFilePath OutputFilePath with actual file path in the above command.




<ul>

 <li>To compile JUnit Tests: javac -cp src/:lib/* test/*</li>

 <li>To run All JUnit Tests: You can choose one of two commands below

  <ol>

   <li>java -cp src/:lib/*:test/ TestRunner</li>

   <li>java -cp src/:lib/*:test/ org.junit.runner.JUnitCore TestSuite ● To run Single JUnit Test: java -cp src/:lib/*:test/ org.junit.runner.JUnitCore TestHashTable java -cp src/:lib/*:test/ org.junit.runner.JUnitCore TestHeap</li>

  </ol></li>

</ul>




<strong>Grading process: </strong>

<ol>

 <li>Compiling your program with JUnit test files using javac v10.0.2.</li>

 <li>Running JUnit tests. It read input files and manipulates data structures implemented by you and see if it works as expected. Any forms of difference between you output and expected output will cause points deduction.</li>

 <li>Inspecting your source code.</li>

</ol>




<strong>4B: C++ </strong>

Compilation will be done using g++ and makefiles. You <u>​must submit</u>​ all the source code as well as the Makefile that compiles your provided source code into an executable named “program”.




Your project must compile using the standard g++ compiler (v 4.9.2) on data.cs.purdue.edu.  For convenience, you are provided with a template Makefile and C++ source file. You are allowed to modify such file at your convenience as long as it follows the I/O specification. Note some latest features from C++14 are not available in g++ 4.9.




The grading process consists of:




<ol>

 <li>Compiling and building your program using your supplied makefile.</li>

 <li>The name of produced executable program must be “program” (must be lowercase)</li>

 <li>Running your program automatically with several test input files we have pre-made according to the strict input file format of the project and verifying correct output files thus follow the above instruction for output precisely – do not “embellish” the output with additional characters or formatting – if your program produces different output such as extra prompt and space, points will be deducted.</li>

 <li>Inspecting your source code.</li>

</ol>




Input to the programming projects will be via the command line:

<strong>program input-test1.txt output-test1.txt </strong>




The file output-test1.txt will be tested for proper output.


