Download Link: https://assignmentchef.com/product/solved-cs1xc3-assignment-7-binary-search-trees
<br>
<ul>

 <li>Write a C program that works with binary search trees (BSTs).</li>

</ul>

<h1>Requirements</h1>

As starter code for this assignment, use the C code contained in as7_starter_code.zip file found on Avenue to Learn accompanying this assignment.

This starter code contains the same binary search tree type used in lectures and labs, and the same set of functions for working with binary search trees that we created together in lecture and lab.  The starter code also contains the following function declarations:




<em>// HINT: This function was used as a helper function for array_of_sorted_keys // in the instructor’s solution: </em>

<em>// void build_array(bstNode *node, int *array, int *current_index); int *array_of_sorted_keys(bstNode *node); </em>

<em>  </em>

<em>// HINT: This function was used as a helper function for  </em>

<em>// balanced_tree_from_sorted_array in the instructor’s solution: </em>

<em>// bstNode *construct_tree(int *array, int min, int max); </em>

<em>bstNode *balanced_tree_from_sorted_array(int *sorted_array, int length); </em>

<em>  </em>

<em>bstNode *balanced_tree_copy(bstNode *tree); </em>




At a minimum you will need to implement the <strong>array_of_sorted_keys</strong>,

<strong>balanced_tree_from_sorted_array</strong>, and <strong>balanced_tree_copy</strong> functions.  Two function declarations have been commented out in the starter code, but they were used by the instructor to create their solution to the problems, and so you can implement these as well if you find them helpful (I would recommend implementing them).

The <strong>array_of_sorted_keys</strong> function must accept as an argument the head node of a BST.  It needs to return a pointer to a dynamically allocated array that contains the keys of the BST sorted in ascending order.  In order to do this, you’ll need to dynamically allocate an array large enough to hold all of the keys.  The <strong>num_nodes</strong> function can help you with this.  In the week 9 lab you’ll learn that you can print out the keys of a BST in an ascending sorted order if you do an in-order traversal of the tree.  In this case, instead of printing the nodes, you’ll need to store them in the dynamically allocated array that you’ve created.

In the instructor’s solution, they used a helper function <strong>void build_array(bstNode *node, int *array, int *current_index)</strong> which performed an in-order traversal of the BST, storing the results into array, and using current_index to keep track of the index to place the next element visited into the array. You don’t have to solve the problem exactly this way, but this way is recommended, and whatever you do, do not use a global variable to manage this.

The <strong>balanced_tree_from_sorted_array</strong> function needs to accept as arguments an array of ints stored in ascending sorted order, and the length of that array.  It needs to return a pointer to a newly created <strong><em>balanced </em></strong>binary search tree that contains as keys all of the elements in the array (i.e. you are converting the array contents to a balanced binary search tree).  A balanced binary search tree has the minimum height necessary to contains all of the keys.  If you wanted to create a balanced tree from a sorted array, then the best node for the root node would be the middle element of the array, given that half the array elements will be less than this element and half the array elements will be greater than this element.  If the array contains an even number of elements either of the two ‘middle’ elements will work.  If you recursively applied this logic to each remaining left and right subsection of the array to build the left and right subtrees of this node, you could build a balanced binary search tree.  So a function could work like this:

<ol>

 <li>Is there still a middle to be found? If not, return NULL.</li>

 <li>Get the middle of the array, create a new node with this value as the key.</li>

 <li>Take the left half of the array, call the function recursively and set the left child of the node to the result.</li>

 <li>Take the right half of the array, call the function recursively and set the right child of the node to the result.</li>

 <li>Return the node.</li>

</ol>

In order to do this, the instructor’s solution used a helper function <strong>bstNode *construct_tree(int *array, int min, int max)</strong> where min is the beginning index of the segment of the array being converted, and the max is the ending index of the segment of the array being converted.  By recursively calling <strong>construct_tree </strong>with min and max values that reflect the portion of the array being converted for a given subtree, we can follow the above algorithm.  We detect that there is no longer a “middle” that can be found when the function is called with a min &gt; max.  You do not need to solve the problem exactly this way, but this is the recommended approach.

The <strong>balanced_tree_copy</strong> function should accept as input a binary search tree that is potentially unbalanced.  It should return a copy to a new balanced binary search tree on the heap which contains the same keys.  In order to do this, you can call the <strong>array_of_sorted_keys</strong> function to obtain an array containing the keys of the binary search tree in ascending sorted order.  Then you can call <strong>balanced_tree_from_sorted_array</strong> to obtain a balanced binary search tree from these results.  Don’t forget to free the array you created as there is no need for it after the function is done!




<h1>Test Code</h1>

The main function contains test code to test the 3 functions.  You may want to “comment out” this code by surrounding it with /* … */ multiline comments so that you can work on your functions, as the code assumes that all of the functions have been implemented.  You can use this code to help verify that your functions are working correctly.

The expected test code results are provided after the mark breakdown, and as a plaintext file on Avenue to Learn accompanying the assignment.


