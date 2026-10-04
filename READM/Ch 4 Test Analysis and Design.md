# Ch 4 Test Analysis and Design

Test techniques support the tester in
    |_ test analysis (what to test)
    |_ test design (how to test)
techniques also help the tester to define
    |_ test conditions
    |_ identify coverage items
    |_ identify test data during the test analysis and design
Test Techniques
    |_ Black-box test techniques (also known as specification-based techniques)
        are based on an analysis of the specified behavior of the test object
        without reference to its internal structure
        Therefore, the test cases are independent of how the software is implemented
        if the implementation changes, but the required behavior stays the same,
        then the test cases are still useful.
    |_ White-box test techniques (also known as structure-based techniques)
        are based on an analysis of the test object’s internal structure and processing.
        As the test cases are dependent on how the software is designed,
        they can only be created after the design or implementation of the test object.
    |_ Experience-based test techniques
        effectively use the knowledge and experience of testers 
        for the design and implementation of test cases.
        The effectiveness of these techniques depends heavily on the tester’s skills
        Experience-based test techniques can detect defects that may be missed using
        the black-box and white-box test techniques. 
        Hence, experience-based test techniques are complementary to the
        black-box and white-box test techniques.

Black-Box Test Techniques
-
<pre>
  |_ • Equivalence Partitioning
  |_ • Boundary Value Analysis
  |_ • Decision Table Testing
  |_ • State Transition Testing
</pre>
<pre>
  Equivalence Partitioning
    Equivalence Partitioning is a black-box test design technique where 
    we divide possible input values into groups, called equivalence partitions.
    If one value from a group behaves correctly, we assume other values in the same group will behave similarly.
    So, instead of testing every possible value, we test one representative value from each partition.
    e.g 
      Suppose an application accepts an age from 18 to 60.
      We can divide the input into these partitions:
      Partition	   |  Values	| Type	    |  Example test value
    ---------------------------------------------------------------
          P1	     | Age < 18	| Invalid	  |   15
          P2	     | 18–60	  | Valid	    |   30
          P3	     | Age > 60	| Invalid	  |   65
    
    Instead of testing:
      1, 2, 3, 4, ... 100
      we test just:     
      15 → represents P1    
      30 → represents P2      
      65 → represents P3      
      Therefore, only 3 test cases are needed to cover the three partitions.
            
    Why is it called "Equivalence"?
        Values in the same partition are expected to be treated in the same way by the system.
            
    Valid and Invalid Partitions
        Valid
        |_ Contains values that the system is expected to accept/process.
           eg Age: 18–60
        Invalid
        |_ Contains values that the system should reject, ignore, or for which processing
           eg Age < 18 and Age > 60
             
    Partitions must NOT overlap
        Not overlap
        Be non-empty
        Together represent the relevant possible values

    EP can be used for more than just input
    Equivalence partitions can be identified for:
      . Input values      
      . Output values      
      . Configuration values      
      . Internal values     
      . Time-related values      
      . Interface parameters

    EP Coverage
        the coverage item is the equivalence partition.
        Formula:       
        EP Coverage = (Number of partitions tested / Total number of identified partitions) × 100
        eg Suppose we identify 4 partitions: P1,P2,P3,P4
           If our test cases cover P1, P2 and P3:
           Coverage = 3 / 4 × 100 = 75%
           To achieve 100% EP coverage, every identified partition must be tested at least once,
           including invalid partitions.

    Multiple Input Parameters
        Suppose a login form has:

          Username        
          U1 = valid username          
          U2 = invalid username
          
          Password         
          P1 = valid password          
          P2 = invalid password
             
          We now have two sets of partitions.
             so there going to be 4 set of combination
             
        What is Each Choice coverage?
             Every partition from every partition set must be exercised at least once.

    Very important distinction
      Equivalence Partitioning
      Question:
      "What groups of values should I test?"

</pre>
<pre>
  Boundary Value Analysis
    Boundary Value Analysis (BVA) is a black-box test design technique 
    that focuses on the edges/boundaries of equivalence partitions.
    Errors are more likely to occur at the boundaries, so test the values at and around the boundary.
  1. Why do we test boundaries?
      Developers commonly make mistakes such as:
      Boundary placed one value too high
      Boundary placed one value too low
      Boundary completely forgotten
      Incorrect condition such as = instead of <=
        
  BVA works only with ordered partitions
      eg
        Age < 18
        18–60
        Age > 60
      These are ordered, so BVA can be used.
      But something like:
        Color = Red
        Color = Blue
        Color = Green
      has no natural "next to" relationship, so normal BVA does not apply.
  2-Value BVA
      The boundary + its closest neighbor in the adjacent partition
      eg
          For the boundary 18:
            17 → neighbor
            18 → boundary
  3-Value BVA
      Boundary + value immediately below + value immediately above
      For boundary 18:
        17, 18, 19


</pre>
<pre>
  EP and BVA work together in Black-Box Testing
  EP asks:
    "What are the groups?"

  BVA asks:
    "What happens at the edges of those groups?"
    BVA can only be applied to ordered equivalence partitions.
  
  So they are often used together.
</pre>
<pre>
  Decision Table Testing 
    Decision Table Testing is a black-box test design technique used when the system's behavior depends on
    different combinations of conditions.
    Different combinations of conditions can produce different actions/outcomes,
    so create a table containing those combinations and test them systematically.
    It is especially useful for business rules and complex logic.
  eg
    Give free delivery if:
      Customer is a premium member, AND   
      Order amount is ₹500 or more.
    We can create a decision table:
      Conditions / Rules  |  	Rule 1 |	Rule 2 |	Rule 3 |	Rule 4
      ------------------------------------------------------
      Premium member?	    |   T	     | T	     | F	     | F
      Order ≥ ₹500?	      |   T	     | F	     | T	     | F
      Free delivery       |   X      |         |         | 
  
    Now we have 4 possible combinations.
    So we can create at least one test case for each feasible rule.

  A decision table has:

    Rows
    Rows contain:    
      Conditions      
      Actions/results
    
    Columns
      Each column represents a decision rule.

  Symbol	Meaning
    T	       True — condition is satisfied
    F	       False — condition is not satisfied
    –	       Irrelevant — condition doesn't affect the outcome
    N/A	     Not applicable/infeasible for this rule
    X	       Action should occur
    Blank	   Action should NOT occur

  Limited-Entry Decision Table
    In a limited-entry decision table, conditions and actions generally use: True and False
  Extended-Entry Decision Table
    In an extended-entry decision table, conditions/actions can have multiple values.
    ' < ₹500
    ' ₹500–₹999
    ' ≥ ₹1000
  Full Decision Table
      Suppose there are 2 conditions: and each condition can be True or False
      so total 4 combination
      similary for 3 conditions and 2 possible values
      possible combonation will be 2^3 = 8
      hence for boolean combination, possible value ^ condition = 2 ^ n 
      This is why decision table testing can become large very quickly.
        
  Infeasible Combinations
      Sometimes a combination of conditions is impossible.
      A system has:
        User is logged in = True        
        User is logged in = False
      You cannot have both simultaneously.

      So an impossible combination can be marked:
        N/A
      Such infeasible columns can be removed from the table.
      A full decision table initially contains all possible combinations.
      Then we can remove combinations that are infeasible.
  Decision Table Minimization
      Sometimes a condition doesn't affect the result.
      output remains the same , for diff combinations of decision , so keep only one combination for that result

  Decision Table Coverage
      Coverage item = Column
      Each feasible column represents a decision rule.
      To achieve 100% decision table coverage:
        Every feasible column must be exercised by at least one test case.
      formula
        Number of exercised feasible columns ÷ Total number of feasible columns × 100
      Example
        Suppose there are 8 feasible rules.   
          You test 6 of them.        
          Coverage:        
          6 / 8 × 100 = 75%       
          For 100% coverage:       
          8 / 8 × 100 = 100%
      
</pre>
<pre>
  Why Decision Tables Are Useful
    Decision tables are particularly good for finding:
    
      . Missing requirements
      Maybe a particular combination has no defined outcome.
      
      . Contradictory requirements
      Two rules might specify conflicting actions for the same conditions.
      
      . Forgotten combinations
      A developer/tester might naturally think about:
  
  The Main Problem: Exponential Growth
    suggests approaches such as:
      . Minimized decision tables
      . Risk-based testing

  Decision Table Testing	--> "What happens with different combinations of conditions?"

</pre>
<pre>
  State Transition Testing
</pre>
