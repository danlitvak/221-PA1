Due: Feb 06, 22:00
Goals and Overview
In this PA (Programming Assignment) you will:

learn about the course programming environment
learn about vectors
learn about pointers
learn about linked lists
learn about management of dynamic memory
The Assignment
Problem Specification
A Linked List is a dynamic linear structure designed to hold any type of data. In this exercise, we develop and use a linked list to manipulate blocks of pixels from an image.

 

We have broken the image below into 12 square regions called Blocks.


 

Each Block is placed in a Node of a Chain, row-by-row as shown here:


The Chain can be rearranged so that the nodes are linked column-by-column as shown below:


We can also perform a transpose of the image across a diagonal. For example, transposing the row-by-row Chain above will produce the following Chain:


We have provided a starting point for achieving this functionality. It is your task to complete and expand on our implementation.

The second diagram above illustrates the infrastructure of the chain. Most notably, it is a null-terminated singly-linked list, with a head pointer to the first node. Each node in a singly-linked list contains a pointer to the next node next. The next pointer of the last node is NULL.

Specifications for each function you write are contained in the given code. The list of functions here should serve as a checklist for completing the exercise.

In block.cpp
int Dimension() const: Return the dimension along a single axis of the current block. Note that all blocks are square.
void Build(PNG & im, int x, int y, int dimension): From the PNG image im, grab the square region of pixels whose upper left corner is at position (x,y), and whose dimensions are dimension by dimension in the image im.
void Render(PNG & im, int x, int y, int scale) const: Draw the current block at position (x,y) in im, magnified by a factor of scale using nearest-neighbour scaling (no colour blending).
void Transpose() const: Rearrange the Block's pixel contents so that it appears transposed over a diagonal line when rendered.
In chain.cpp
Chain(PNG& imIn, int numCols): Constructor builds the linked list by dividing the input image into square blocks such that the divided image has numCols columns.
~Chain(): Destructor.
Node* InsertAfter(Node* p, const Block & ndata): Insert a new node after the node pointed to by p in the Chain.
void Clear(): Helper function for destructor and assignment operator. Deallocates all dynamic memory associated with this Chain object.
void Copy(const Chain & other): Helper function for copy constructor and assignment operator.
PNG Render(int scale): Renders the pixel data of the chain to an appropriately-sized PNG image. The output image will be enlarged using nearest-neighbour scaling (no colour blending).
void ToRowOrder(): Rearranges the links in the list so that each node's next pointer moves horizontally across an image, respecting the list's number of columns and rows.
void ToColumnOrder(): Rearranges the links in the list so that each node's next pointer moves vertically across an image, respecting the list's number of columns and rows.
void Transpose(): Rearranges links in the list and each Node's Block data so that the rendered image appears transposed over the NW-SE diagonal.
Implementation Constraints and Advice
We will be grading your work on functionality, efficiency, and memory use. All Chain functionality, aside from the insert and the copy functions, can be achieved by moving existing nodes, rather than by allocating new ones and/or making copies. If you are tempted to use the new function when you are manipulating the Chain, ask yourself if you can achieve your goal by reassigning pointers, instead.

Finally, you'll note that we are asking you to implement special memory management functions (constructor, destructor, assignment) for the Chain class. You should ask yourself why we have not made similar requests for the Block class. Why doesn't it need a destructor, copy constructor, or assignment operator?

Getting the Given Code
Download the source files here pa1-20260118-1611.zip and follow the procedures you learned in lab to move them to your home directory on the remote linux machines.

Handing in your code
Submit the required files to this page before the deadline. If you wish to work in a partnership, one partner must first create the group, and then the second partner can join the created group. As this is the first PrairieLearn groupwork assignment of the term, some errors are to be anticipated. If you accidentally create a group, please write a private post to Piazza, or e-mail the instructor. We may look at your prior activity on this assessment before helping you with your group management.

Submit your files for PA1 grading here! These are the only files used for grading.