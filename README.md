Download Link: https://assignmentchef.com/product/solved-cpe212-project03-2
<br>
The goal of this is to implement the baseline data storage for a gradebook.  You will implement a <strong>List</strong> data structure to hold different types, and use it in a representation of a <strong>Student </strong>and a <strong>Classroom</strong> object.

As part of this assignment, you will once again practice implementing components that will be integrated to form a larger product.  This time you will write <strong>List class</strong> that will be integrated into a larger software product provided by the instructor.  This <strong>List class</strong> uses is a <strong>Forward List</strong>, and uses a <strong>Template</strong> to use different types within this list.  The list then allows you to <strong>Append</strong> or <strong>Delete</strong> a node based on the data.  The data type implemented must have an <strong>is_equals (==)</strong> operator overload, as well as a <strong>not_equal (!=) </strong>overload.  The list provides access to the list’s internal data stored by the nodes through a series of iteration functions.  <strong>AtEnd </strong>tells the user that the iterator has no more data to access, <strong>IterateItem</strong> returns the current value of the iterator and increments it forward, and <strong>ResetIterator</strong> to reset the iterator position to the start.

This list is used in two different objects, <strong>Student</strong> which holds grades of a student, including their Projects, Exams, and final exam grade.  <strong>This object has been fully implemented and provided by your instructor.</strong>  The second implementation of the list is the <strong>Classroom</strong>.  The classroom will be implemented by the student, and simply holds a list of students.  This object includes <strong>AddStudent</strong> which adds a student to the list as long as this student (checked by UID) are not already stored.  <strong>RemoveStudent</strong> will then remove student (Checked by UID).  Both functions will return false if they fail to perform their designated operation.  Class then has 3 functions to <strong>Add</strong> <strong>Projects, Exams, </strong>and<strong> FinalExam</strong> grades to the students stored.  These functions take a List of assignments as the input, will iterate through this list, and if the UID matches a student, that type of grade is added to the Student.  If the UID of the assignment is not found in the list, it is simply not added.  It is not guaranteed that a student has completed / turned in an assignment (Much like this class) and its not guaranteed that a student will be found that matches an assignment’s UID.

<ul>

 <li><strong>Do not modify </strong><strong>cpp,</strong> <strong>list.hpp, classroom.hpp, student.hpp, or student.cpp. </strong></li>

</ul>

<strong>There are also a few functions provided in classroom.cpp.  <u>DO NOT MODIFY</u> <u>THOSE EITHER</u></strong>

<strong>     </strong><strong><em>You will write </em></strong><strong><em><u>list_impl.hpp</u></em></strong><strong><em> and <u>classroom.hpp</u></em></strong> <strong><em>!!!</em></strong>

<ul>

 <li><strong>All program output is performed by the code in the </strong><strong>cpp</strong><strong> file – do not include any output statements in the files you write!!! </strong></li>

</ul>

<strong> </strong>

<strong> </strong>

<strong><em>The interfaces to each of these functions you must write are described in detail on subsequent pages and in the files provided </em></strong>

<strong><em>Hint:</em></strong><strong><em>   </em></strong><strong><em>Match</em></strong> <strong><em>the output of your program to that of the sample solution!!!</em></strong>

<strong><em>          Directions for running the sample solution appear on the following page.</em></strong>




<strong><u>Running the Sample Solution on </u></strong><strong><u>blackhawk</u></strong>

<strong><em>The best description of what your code should do is the Sample Solution for the project.   </em></strong>

Run the sample solution by typing the following at <strong>blackhawk</strong> terminal window command prompt

<strong>/home/facstaff/taf0004/CPE212SP20/Project03/Solution/P3 inputfilename </strong>where <strong>inputfilename</strong> is the name of one of the provided input files (for example, <strong><em>P3input1.txt</em></strong>).  <strong><em>Your current working directory must contain the input files for this to work.</em></strong>




<strong><u>Running the Preview Script on </u></strong><strong><u>blackhawk</u></strong>

Run the preview script by typing the following in a <strong>blackhawk</strong> terminal window command prompt

<h2>/home/facstaff/taf0004/CPE212SP20/Project03/preview03.bash</h2>

<strong>This script will run both the </strong><strong>Sample Solution</strong><strong> AND </strong><strong>your project03</strong><strong> executable program on the complete set of input files, and it compares the outputs of the two programs line by line to identify errors in your program’s outputs.  Make sure that the output of your program exactly matches the output of the Sample Solution. </strong>

<strong> </strong>

<h1>&lt;Project03 Include File Constraints&gt;</h1>




<strong><em>You are not allowed to modify the include files within any file.  All of the includes needed are already included.  </em></strong><strong><em>Failure to follow these directions will result in zero (0) credit on this assignment. </em></strong>

<strong> </strong>

<h1>&lt;Project03 Object Description and Hints&gt;</h1>

You should take the list implementation that we discussed in class.  The following functions need to be implemented within the <strong><em>list_impl.hpp</em></strong>:




void AppendItem(const Type &amp;data);     bool DeleteItem(const Type &amp;data);     unsigned int Count() const;




Type&amp; Front();

Type Front() const;

Type&amp; Back();

Type Back() const;




Type* IterateItems() const;     bool AtEnd() const;

void ResetIterator() const;




Since this is a template version of the list, you shouldn’t worry about any specific implementation requirements other than verifying that the data searched for DeleteItem is equal.

For the iterators you should follow the same description we had in class about iterators, but remember you should return a pointer to the data in question, rather than a copy of the data.  This is because we will need to use IterateItems() to modify the underlying data.

Another note is the mutable iterator node.  Remember this is a key word that means it ignores the const-ness of the functions that use it.







Your other file to modify is classroom.cpp. You are given two functions already implemented:

void PrintClassroomInformation() const;

Student* find_student(unsigned int UID, bool &amp;found);




find_student is an important function, which will search your list for the required student based on the UID of the student (think your student ID). This provides you a pointer to the underlying data of Student, rather than anything involving the node.  <strong><u>In order for</u> <u>this to work properly your list has to function correctly.  </u></strong>If no student is found, the Boolean reference will return false, and true if a student is found.




You then have 5 functions in the Classroom object to implement

bool AddStudent(const std::string &amp;firstName, const std::string &amp;lastName,                      unsigned int UID);

bool RemoveStudent(unsigned int UID);







void AddProjects(const List&lt;Assignment&gt; &amp;projects);     void AddExams(const List&lt;Assignment&gt; &amp;exams);     void SetFinalExams(const List&lt;Assignment&gt; &amp;finals);




AddStudent should construct a student (on the stack) and append it to the _classList.

<strong>IF THE STUDENT ALREADY EXISTS, THIS SHOULD FAIL AND RETURN FALSE.  </strong>

RemoveStudent should remove a student based on the UID.  Students are compared SOLELY on their UID, so use this for comparing if the student exists and for deleting.  <strong>For both of these functions put more work on the List object, and not on your specific class implementation. </strong>




For the AddAssignment functions, you will get a list of assignments, these have a score and a UID attached to them.  You should search for the student with a UID equal to the UID of the assignment.  <strong><u>It is not guaranteed that a student has completed / turned</u> <u>in an assignment (Much like this class) and its not guaranteed that a student will</u> <u>be found that matches an assignment’s UID.</u> </strong>

<strong> </strong>

<strong><u>A SPECIAL NOTE ABOUT CORRECTNESS: </u></strong>The test script will run your code using valgrind.  Please read any notes about valgrind in the canvas -&gt; modules -&gt; tutorials -&gt; valgrind.  This will verify that you are cleaning up all memory correctly.  <strong><u>The valgrind</u> <u>check must pass in order for your code to be considered correct</u></strong>.  <strong><u>FAILURE TO</u> <u>DO THIS WILL RESULT IN A 0 FOR THAT TEST</u></strong>.

<strong> </strong>

<h1>&lt;Important Project03 Submission Instructions&gt;</h1>

<ul>

 <li><strong>Follow all submission instructions provided on Canvas.</strong></li>

 <li><strong>Below is a list of the files you must submit. It is very important that you use the correct file names: [lowercase letters, no spaces, no underscores] in order for your program to compile and execute.</strong></li>

</ul>

<strong>List_impl.hpp          </strong><strong>(</strong><strong>write</strong><strong> and </strong><strong>submit</strong><strong> this file using the information from </strong><strong>list.h</strong><strong>)</strong>

<strong>Classroom.cpp  </strong><strong>(</strong><strong>write</strong><strong> and </strong><strong>submit</strong><strong> this file using the information from </strong><strong>classroom.h</strong><strong>)</strong>

<strong>A </strong><strong>COMPLETE SUBMISSION</strong> <strong>is one that includes </strong><strong>the specified file as an attachment to the your submission</strong><strong>.   All other submissions will be considered to be incomplete.</strong>

<strong><em>INCOMPLETE SUBMISSIONS will receive zero credit (</em></strong><strong><em>0 points</em></strong><strong><em>) on this assignment.</em></strong> <strong>DO NOT USE A FILE COMPRESSION PROGRAM     (.zip, .tar, etc. are not allowed) </strong>

<strong><em>Failure to satisfy this requirement will result in zero credit (</em></strong><strong><em>0 points</em></strong><strong><em>) on this assignment.</em></strong>

<ul>

 <li><strong><em>Do not modify or submit the file named </em></strong><strong><em>cpp, classroom.hpp, student.cpp, student.hpp </em></strong><strong><em>or </em></strong><strong><em>list.hpp</em></strong><strong><em> !!! </em></strong></li>

</ul>

<strong><em>Failure to satisfy this requirement will result in </em></strong><strong><em>zero credit</em></strong><strong><em> (</em></strong><strong><em>0 points</em></strong><strong><em>) on this assignment.</em></strong>

<ul>

 <li><strong><em>All output to the monitor (stdout) will be performed by the code provided in </em></strong><strong><em>cpp and the provided functions in your objects.</em></strong></li>

</ul>

<strong><em> </em></strong>




<strong><em> </em></strong>




<strong> </strong>