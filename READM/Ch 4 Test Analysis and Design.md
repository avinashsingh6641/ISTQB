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
      Conditions / Rules  |  Rule 1 | Rule 2   |Rule 3   |	Rule 4
      --------------------------------------------------------------
      Premium member?	  |   T	     | T	   | F	     | F
      Order ≥ ₹500?	      |   T	     | F	   | T	     | F
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
    State Transition Testing is a black-box test design technique used when a system's behavior depends on 
    its current state and an event that occurs.
    The main idea is:
        The same event can produce different results depending on the current state of the system.
        1. What is a State?
            A state describes the current condition or situation of a system.
            For example, consider a login system: Logged Out , Logged In , Account Locked
        2. What is a Transition?
            A transition is the movement from one state to another because of an event.
            Logged Out
                |
                | Correct username + password
                ↓
            Logged In
            Here:
                Current state = Logged Out           
                Event = Correct username + password            
                Next state = Logged In          
                That movement is called a transition.
        3. State Transition Diagram
            A state transition diagram visually represents: States, Events, Transitions, Sometimes conditions and actions
                    Correct Login
               ┌────────────────────┐
               │                    ↓
            [Logged Out] ───────→ [Logged In]
               ↑                     │
               │                     │ Logout
               └─────────────────────┘
        4. Event, Guard Condition and Action
            event [guard condition] / action
            Event -> Something that causes a transition. e.g login
            Guard condition -> A condition that must be true for the transition to happen. e.g valid login id and password
            Action -> Something the system does as a result. e.g show user dashboard
            summary:
                Login [password correct] / Display dashboard
        6. State Table
            The same model can be represented as a state table instead of a diagram.
            Current State	     Insert Card	     Enter PIN	         Logout
            Card Not Inserted	 Card Inserted	        —	                —
            Card Inserted	     —	                 PIN Verification	    —
            PIN Verification	 —	                 Authenticated	        —
            Authenticated	     —	                 —	                  Card Not Inserted
            Here:
                Rows = states             
                Columns = events              
                Cells = resulting transitions
    
            A state table explicitly shows invalid transitions.
            The empty cells indicate that the transition is invalid/not defined.
        7. Test Case = Sequence of Events

        Note : One test case can cover multiple transitions.

        8. Three Important Coverage Types
            |_ All States Coverage
            |_ Valid Transitions Coverage (0-switch)          
            |_ All Transitions Coverage

            1) all state coverage
                Here we only care about visiting every state.
                Coverage item = State
                suppose A → B → C → D
                To achieve 100% all-states coverage: you must visit A,B,C,D for 100% coverage
            2) valid transitions coverage
                this is stronger approach then all state coverage
                also called as 0-switch coverage
                Here we care about every valid transition.
                Coverage item = Valid transition
            3) all transitions coverage
                This is the strongest of the three.
                It requires testing:
                    |_ All valid transitions          
                    |_ Attempting all invalid transitions
                Why Test Invalid Transitions?
                    Because invalid behaviour can contain defects too.
                    For example: A locked account should reject a login attempt.
        9. Fault Masking
            important istqb question
            Suppose we want to test two invalid transitions:
            If we put both into the same test case and the first defect causes the test to stop,
            we might never reach the second invalid transition.
            That's called fault masking.
            therefore, Test only one invalid transition in a single test case to help avoid fault masking.

</pre>
White-Box Test Techniques
-
<pre>
    two code-related white-box test techniques:
        • Statement testing
        • Branch testing
    1) Statement Testing & Statement Coverage
        “Have my tests executed every line of executable code at least once?”
        1. What is a statement?
            A statement is an executable instruction in the program.    
        example:
            1. read age
            2. if age >= 18
            3.     print "Adult"
            4. else
            5.     print "Minor"
            6. end
        2. What is Statement Testing?
            In statement testing, we create test cases so that the program executes as many statements as possible.
        3. What is Statement Coverage?
            The formula is:
            
            Statement Coverage = (Number of statements executed/Total executable statements) * 100
           
        4. What does 100% statement coverage mean?
            Every executable statement has been executed at least once by your test cases.
            Note : 100% statement coverage does NOT mean the software is defect-free.
            Because simply executing a statement doesn't guarantee that you've
            tested all possible situations involving that statement.
            example divisible by zero problem if your code contain number divisbility ,and you executed that statement by >0 number,
            you didint check for potential bug what will happen for 0 and code have potential bug
    
    2) Branch Testing & Branch Coverage
        “Have my tests taken every possible route through the decisions in the code?”
        1. What is a branch?
            A branch is a possible transfer of control from one part of the program to another.
        example:
            if (age >= 18)
                print("Adult");
            else
                print("Minor");
        There are two possible branches:
            True branch → age >= 18 → print "Adult"         
            False branch → age < 18 → print "Minor"      
            So we need tests for both outcomes.
        2. What is Branch Testing?
            In branch testing, we design test cases to execute the different branches of the code.
            Branch Coverage = (Number of branches exercised /Total number of branches) * 100
        3. What does 100% Branch Coverage mean?
            Every branch in the code has been exercised by at least one test case.
            This includes:
                |_ Conditional branches — True/False outcomes of decisions
                |_ Unconditional branches — normal/straight-line transfers of control

    Note important:
        Branch coverage subsumes statement coverage.
        means -> 100% branch coverage automatically gives you 100% statement coverage.
        But even 100% Branch Coverage is NOT enough
            Even if you achieve 100% branch coverage, you may still miss defects
            that require a specific path through the code.

</pre>
<pre>
    The Value of White-box Testing
    1. What is White-box Testing?
        Testing based on the internal structure and implementation of the software.
        You look at the code, logic, conditions, branches, statements, paths, etc., and design tests based on them.
    2. Main Strength of White-box Testing
        The entire software implementation is taken into account during testing.
        In simple words: White-box testing looks inside the code.
        Therefore, even if the requirements/specification are:
            |_ unclear
            |_ incomplete
            |_ outdated
            |_ poorly documented
        you can still find some defects by examining and testing the actual implementation of code.
    3. Main Weakness of White-box Testing
        White-box testing may miss defects of omission.
        Something that should have been implemented is completely missing from the software.
        e.g 
        The system should allow customers to pay using:
            Credit card
            Debit card
            UPI
        But the developer only implements:
            Credit card
            Debit card
        That's a defect of omission.
        White-box is good at finding what's wrong inside the code, but it can miss what's completely missing from the code.
    4. White-box Testing Can Also Be Used in Static Testing
        White-box techniques don't necessarily require the code to execute.
        For example, a developer or tester can inspect: source code, pseudocode, algorithms, control flow, logic
        without actually running the program.
    5. What is a Control Flow Graph?
        A control flow graph (CFG) represents the possible flow of execution through the code.
                Start
                  ↓
             age >= 18?
               ↙     ↘
            True     False
             ↓         ↓
          Adult      Minor
               ↘     ↙
                 End7
    6. White-box Coverage Gives an Objective Measurement
        White-box techniques provide measurable coverage such as:
            |_ Statement coverage
            |_ Branch coverage
        This gives you an objective indication of how much of the executable code has been exercised.
    
</pre>
Experience-based Test Techniques
-
<pre>
    • Error guessing
    • Exploratory testing
    • Checklist-based testing

    1) error guessing
        1. How does Error Guessing work?
            A tester uses knowledge such as:           
            |_ How this application behaved in the past          
            |_ What mistakes the developers commonly make           
            |_ What defects have occurred in similar applications            
            |_ Common reasons why software fails
        2. What types of problems can Error Guessing target?
            A. Input errors -> Examples: Correct input is rejected, Required parameter is missing, Wrong parameter is supplied,
                                        Empty input, Very large input, Invalid characters
            B. Output errors -> Examples: Wrong result, Wrong format, Missing output, Incorrect rounding
            C. Logic errors -> The developer may implement the wrong logic.
            D. Computation errors -> The calculation itself may be wrong.
            E. Interface errors -> Problems can occur when two components communicate.
            F. Data errors -> Problems with data can also be guessed. -> Incorrect initialization, Wrong data type,
                                                                         Incorrect default value, Data stored incorrectly
    
        3. Fault Attack:
            A more systematic/methodical form of error guessing.
            Fault Attack = “Let's make a list of those mistakes and systematically test for them.”
            The tester creates or obtains a list of possible errors, defects, and failures,
            and then designs tests specifically to expose them.
            From previous experience, you create a fault list:
            Then you deliberately create tests for these possible faults.
    
    2) Exploratory Testing
        Exploratory testing means the tester learns, designs tests, executes tests, and evaluates results at the same time.
        Exploratory testing = “Explore the software while testing it.”
        Learn → Design → Execute → Evaluate → Learn more → Design next test...
        Why is it called "Exploratory"?
            Because the tester is exploring the test object.
            |_ The tester may discover:        
            |_ New functionality         
            |_ Unexpected behavior          
            |_ Potential defects           
            |_ Areas that need deeper testing           
            |_ Areas that haven't been tested yet        
            |_ The new knowledge then influences the next tests.
        1. Session-Based Exploratory Testing
            A session is performed within a defined time-box.
            What is a time-box?
            A fixed amount of time.
            The tester doesn't necessarily have a complete list of detailed test cases.
            Instead, they have a test charter.
        2. What is a Test Charter?
            A test charter provides the objectives/direction for the exploratory session.
            Test charter = Where/what should I explore?
            Tester = How exactly will I explore it?
        3. What happens after the session?
            Usually, there is a debriefing.
            The tester discusses the session with interested stakeholders.
        4. Test Session Sheets
            The tester may use a test session sheet to record:
                Steps performed
                Areas explored              
                Important observations             
                Defects discovered             
                Questions            
                Ideas for further testing
        5. When is Exploratory Testing Useful?
            A. Few or inadequate specifications  -> Suppose the requirements are incomplete:
            B. Significant time pressure. -> Suppose you have only one day to test a new feature.
            C. Complementing formal testing. -> Exploratory testing doesn't have to replace other techniques.
        6. Tester Skill Matters -> Experience, Domain knowledge, Analytical skills, Curiosity, Creativity
        7. Exploratory Testing Doesn't Mean "Random Testing"
            With session-based exploratory testing, you have even more structure:
            Test Charter → Time-box → Explore → Record discoveries → Debrief



    
</pre>

