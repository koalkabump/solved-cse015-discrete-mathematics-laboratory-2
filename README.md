Download Link: https://assignmentchef.com/product/solved-cse015-discrete-mathematics-laboratory-2
<br>
<h1>Introduction</h1>

This lab gives you further practice with the Python language on problems related to truth tables in propositional logic. Please complete the following exercises and upload your .py files under the appropriate CatCourses assignments.

Even for the simplest programs we write, we make use of code written by others. For this lab you are provided with code that generates truth tables, which you can use for other exercises. To start, download the file logic.py from CatCourses and place it in your working directory. Among other things, the file defines a TruthTable object. Start a new project and import the TruthTable object from logic.py, using the following command:

from logic import TruthTable

You can now generate truth tables for any proposition. All you need to specify is the list of variables that appear in your propositions, and the propositions themselves.

<strong>Example             </strong>Generate a truth table for the proposition <em>p∨q</em>.

<strong>Solution </strong>We first note that there are two variables, <em>p </em>and <em>q</em>, which will be represented in Python as the list [’p’, ’q’]. We also need to represent the proposition itself, which is the Python string ’p or q’. Since the TruthTable object can generate a truth table with multiple expressions, we will provide the proposition as a list with a single element in it, [’p or q’]. We are now ready to generate the truth table:

myTable = TruthTable([’p’, ’q’], [’p or q’])

We can now display the truth table generated above:

myTable.display()

The command above produces the following text:

p                  q                    p or q

———————–

0                  0                  0

<ul>

 <li>1 1</li>

 <li>0 1</li>

</ul>

1                  1                  1

You can also generate L<sup>A</sup>TEX code for representing the table:

myTable.latex()

The above command produces the following text:

begin{tabular}{|c|c|c|}

hline

$p$ &amp; $q$ &amp; $p lor q$ \

hline

0 &amp; 0 &amp; 0 \

<ul>

 <li>&amp; 1 &amp; 1 \</li>

 <li>&amp; 0 &amp; 1 \</li>

</ul>

1 &amp; 1 &amp; 1 \

hline

end{tabular}

The TruthTable object can also be called with multiple propositions. myTable = TruthTable([’p’, ’q’], [’p or q’, ’p and q’])

The command above generates one truth table with both propositions side by side:

p                  q                    p or q           p and q

——————————–

<table width="199">

 <tbody>

  <tr>

   <td width="191">0                  0                  0</td>

   <td width="8">0</td>

  </tr>

  <tr>

   <td width="191">0                  1                  1</td>

   <td width="8">0</td>

  </tr>

  <tr>

   <td width="191">1                  0                  1</td>

   <td width="8">0</td>

  </tr>

  <tr>

   <td width="191">1                  1                  1</td>

   <td width="8">1</td>

  </tr>

 </tbody>

</table>

When using TruthTable, we need to specify all propositions and propositional variables as Python strings, as illustrated in the examples here. The TruthTable object supports the following logical connectives: or (<em>∨</em>), and (<em>∧</em>), – (<em>¬</em>), -&gt; (<em>→</em>), &lt;-&gt; (<em>&#x2194;</em>).

<h1>Basic Truth Tables</h1>

Write a Python program that prints out the truth tables for all logical connectives studied in class. There should be a separate truth table for the following:

<em>¬a a∧b a∨b a→b a&#x2194;b</em>

<h1>Equivalence in Propositional Logic</h1>

As discussed in class, one way to prove whether two propositions are equivalent, is to generate truth tables for both propositions and check to see if all the rows match, in which case the propositions are equivalent, otherwise they are not.

In this exercise you are required to write a Python program that asks the user to enter two propositions, where both propositions the variables p and q. Your program should then determine whether or not the two propositions are equivalent, and report the result.

Here is an example of how a user might interact with your program:

Enter proposition 1: p and q

Enter proposition 2: q and p

The propositions are equivalent

In order to complete this exercise, you should study the structure of the table property of TruthTable. You can access it by saying:

print myTable.table

For example, here is the table of the proposition <em>p∧q</em>.

[[[0, 0], [0]], [[0, 1], [0]], [[1, 0], [0]], [[1, 1], [1]]]

As you can see, it is one big list, made up of exactly 4 smaller lists. Each one of the smaller lists represents a row of the truth table. Each row in turn is made up of exactly 2 lists. The first one is a list of truth values of the propositional variables, and the second one is the overall truth value of the proposition(s), given the truth values in the last list.

If we take the above table and consider the first row, that is the list [[0, 0], [0]]. Bearing in mind that this is for the formula <em>p∧q</em>, the way to interpret this list is that when the variables <em>p </em>and <em>q </em>are [0, 0], respectively, then the proposition <em>p∧q </em>has a truth value of [0], or simply 0. Remember, this is represented as a list with a single element in it because the truth table may have more than one proposition being evaluated.

This brings us to the following example. Let us generate a single truth table for both <em>p∧q </em>and <em>q∧p</em>. Now we have the following table:

[[[0, 0], [0, 0]], [[0, 1], [0, 0]], [[1, 0], [0, 0]], [[1, 1], [1, 1]]]

It is still made up of 4 lists, each of which represents a row of the truth table. Each row is still made up of two lists, as before. The first of these lists is still a specific combination of truth values, and the second list is the overall truth value of each proposition. Since we generated a truth table for 2 propositions, the list has 2 results in it. This time, taking the second row, which is [[0, 1], [0, 0]], we can see that when <em>p </em>= 0 and <em>q </em>= 1 then <em>p∧q </em>evaluates to false, and <em>q∧p </em>also evaluates to false, hence both 0 values in the list. Examining the whole table, we can see that the two propositions are indeed equivalent because, for every row, the result part always contains the same two values, meaning that for any possible combination of truth values, both propositions evaluate to the same result.