Download Link: https://assignmentchef.com/product/solved-csis3280-assignment-2-using-objects-for-random-algebraic-expression-generator
<br>
You are asked to refactor (re-write) your assignment1 using class and objects. You are given the solution to assignment1 as attached to this assignment. There are some minor deviations (changes) in assignment 1. That’s why you are supposed to modify the provided source codes of assignemnt1 and not your submitted assignement1.

<strong>Requirement: </strong>

<ol>

 <li>You must display a form to the user to enter the degree of the expression. <strong>Only for the first time</strong>, loading the page, the form is displayed alone as you can see in the picture on the left. When the user enters a value for the degree and press Generate button, <strong>from then</strong>, the page looks like the picture on the right. A default value of 2 is displayed in the input box for the degree, but the user can change it to any value greater than 0.</li>

</ol>

Read the slides for <strong>Lecture8-Web Forms </strong>to learn how to use an if-else and checking for $_SERVER[‘REQUEST_METHOD’] to decide if it is the first time the page is loading, or not.




<ol start="2">

 <li>To display the form, define a function This function has one input parameter <strong>degree</strong>, it does not return any value. It displays the label for <strong>Degree:</strong> and an input box and submit button. The input parameter degree is used to set the value for input (i.e., &lt;input value=”$degree” ……. /&gt;) . use HEREdoc to print the HTML code.</li>

 <li>Define a class called <strong>Term</strong>.

  <ol>

   <li>This call has only two properties:<strong> coefficient </strong>and<strong> exponent</strong>. This class is going to represent each single term of an expression.</li>

  </ol></li>

 <li>Define another class

  <ol>

   <li>This class has two <u>const</u> called <strong>coefficient_min</strong> and these two consts define the lower and upper limit range of random values for coefficients of the expression. Set it to -20 and 20 respectively.</li>

   <li>This class has three properties: <strong>terms</strong>, <strong>degree, </strong>and

    <ol>

     <li><strong>terms </strong>property is a single-dimension array of<strong> Term </strong><strong> NOTE: </strong>it is not a two-dimensional array as in assignment1.<strong> It is an array of objects </strong>(i.e., an array of Term objects)</li>

     <li><strong>degree </strong>and<strong> num_of_terms </strong>are integer variables</li>

    </ol></li>

   <li>This class has 4 methods:<strong> generate(), stringify(), meets_requirements(), simplify(). </strong></li>

  </ol></li>

</ol>

Note, in the code provided to you the name of functions is, for example, generate_expression(), but as we will use the name of an object with the method, it is simpler in the new edition of the code to change the name from generate_expression to generate. Because, if the name of an object is $expr then it is simpler to write $expr-&gt;generate() than $expr-&gt;generate_expression() (we do not need to repeat expr and expression!)

<ol start="5">

 <li>Create a constructor for the class <strong>Expression</strong>. The constructor has 1 input parameter:<strong> degree</strong>. When we create an Expression object, we pass a value for the degree. For example:</li>

</ol>

<strong>$expr = new Expression(2);</strong>       // to create an expression of degree 2

Inside the constructor, set the initial value for the <strong>degree</strong> property to the input value to the constructor, also set <strong>num_of_terms</strong> based on the same formula given in assignemnt1, also set <strong>terms</strong> property to an empty array. You know that in a constructor of a class, we initialize the properties of an object.

<ol start="6">

 <li>The generate() method of the class does not have any input parameter as we did in the assignment1. Because, the degree is a property for the class now, no need to get the degree as an input parameter to the method. Use <strong>$this-&gt;degree</strong> to refer to the degree property.</li>

</ol>

Inside the do-while loop, first set <strong>$this-&gt;terms</strong> to <strong>null</strong>, to ensure the terms array is empty, then for every term you must create an object from <strong>Term</strong> class, set the <strong>coefficient</strong> and <strong>exponent</strong> properties of the object to randomly generated values and then assign this newly created object from the class Term to the array <strong>terms</strong>. Like:

<strong>$this-&gt;terms[] = $term;  </strong>// $term is an object of the class Term. $this-&gt;terms is an array, a property of the class Expression

<strong>NOTE:</strong> <u>terms</u> is not a two-dimensional array, as we did in assignement1, <strong><u>terms</u> is an array of objects </strong>in this assignment.

generate() returns the property terms (the array of objects representing the terms of the expression)

<ol start="7">

 <li><strong>meets_requirements() </strong>does not have any input, because both of inputs that we assigned to it in assignemnt1 are the properties of the class now and we do not need to get them as input. We refer to $degree as <strong>$this-&gt;degree</strong>, also <strong>$this&gt;num_of_terms</strong>, and to refer to an exponent of a term we use <strong>$this-&gt;terms[$i]-&gt;exponent </strong>instead of<strong> $terms[1][$i] </strong></li>

</ol>

in this function, only reference to the variables (degree, num_of_terms, and exponent of a term) changes and the rest of the body of the function remains unchanged.

<ol start="8">

 <li><strong>stringify() </strong>method has no input and returns a string. Variables must be changed. For example, <strong>$terms[0][0]</strong> is going to be<strong> $this-&gt;terms[0]-&gt;coefficient</strong>, also <strong>$terms[1][0]</strong> is changed to<strong> $this-&gt;terms[0]-&gt;exponent</strong>. Also<strong> count($terms[0]) </strong>is changed to<strong> count($this-&gt;terms)</strong>. Apply any other changes required. <u>No need to make stringify_term() function a method of the class.</u></li>

 <li>You must write a new function called <strong>simplify</strong> which is a method of the class Expression. This method gets an object of Expression and simplify it. This method is This method has 1 input which is an object of the class Expression, and it returns an object of the same type (i.e., simplified version of the input expression which is an object of the class Expression).</li>

</ol>

In this function, first, we create a new object of Expression. Then by a nested loop, we repeat for all degrees to sum up all the coefficients of the terms that have the same exponent. Follow this algorithm:




<em>Create a new object of the class Expression </em>

<em>For-loop (repeat $degree times) {  // if the degree is 3, then 3,2,1,0 </em>

<em>               Sum = 0 </em>

<em>               For-loop(repeat for the length of the array terms of input expression){ </em>

<em>                              If (exponent of a term is equal to the $degree) </em>

<em>                                             Sum += coefficient_of_the_term </em>

<em>               } </em>

<em>               If (sum is not zero) </em>

<em>                                Create a new term from the class Term </em>

<em>                              </em><em>Set exponent to $degree</em>

<em>                              Set coefficient to sum </em>

<em>                              Assign this new Term object to the array <strong>terms</strong> of the new simplified Expression object Set num_of_terms for this new simplified object to the size of its <strong>terms</strong> array Return the simplified expression object<strong>  </strong></em>

<em>                </em>