28-09-2026
# Ch 3 Static Testing

Static Testing Basics
-
<pre>
In static testing the software under test does not need to be executed.
  Static Testing	                    |              Dynamic Testing
_______________________________________________________________________________________
Software is not executed              |     Software is executed
Examine work products                 |     Execute test cases
Can be manual or tool-based           |     Usually involves executing software
Finds defects early                   |     Finds defects during execution
Reviews, inspections, static analysis	|     Functional, regression, system testing
No test execution required.           |    	Test execution required

Static = Stop and Inspect
Dynamic = Run and Observe
Testers, business representatives and developers work together during 
  |_  example mappings, collaborative user story writing and backlog refinement sessions 
      to ensure that user stories and related work products meet defined criteria
      e.g., the Definition of Ready
</pre>
Work Products Examinable by Static Testing
-
<pre>
  Almost any work product can be examined using static testing.
  A work product simply means anything produced during software development.

      Examples:
          Requirements documents 
          Source code
          Test plans
          Test cases
          Product backlog items / user stories
          Test charters
          Project documentation
          Contracts
          Models
  Simple idea
      If someone creates something as part of the project, you can often review it without executing the software.
  . Anything that can be read and understood" → Review
      |_ Any work product that can be read and understood can be the subject of a review.
      |_ The reviewers can look for:
            Missing information
            Ambiguity     
            Incorrect information           
            Inconsistencies           
            Poor readability           
            Lack of testability
  . Static Analysis
      |_ A tool needs a structure/rules that allow it to analyze the work product.
      |_ A static analysis tool understands the structure of the programming language and can check things like:
              . Syntax-related issues
              . Coding-rule violations
              . Security problems
              . Maintainability issues
      |_ Why can't everything be analyzed by tools?
          |_ "For static analysis, work products need a structure against which they can be checked."
          |_ The tool needs rules/patterns to compare the work product against.
          |_ If text follows a defined syntax/structure, a tool may be able to analyze it.
  
  . Important exception: Third-party executable code
      |_ You may not be legally allowed to analyze/decompile/inspect the executable code.


</pre>
Importance of Static Testing
-
<pre>
  . Finds defects early
    Requirements
       ↓
    Static Testing ← Find defect here
       ↓
    Design
       ↓
    Coding
       ↓
    Dynamic Testing
  . Static Testing can find defects Dynamic Testing can't
    Some defects cannot be found simply by executing the software.
    1) Unreachable code
        if (age > 1000) {
            calculateSomething();
        }
        If the system can never have an age greater than 1000, this code may never execute.
        Static analysis can identify that the code is unreachable.
    2) Incorrect design pattern
        A design might use a particular architecture/design pattern, but the implementation doesn't follow it as intended.
    3) Non-executable work products
  
  . Static Testing builds confidence
      Static testing helps stakeholders answer:
      "Can we trust this work product?"
  . Requirements can be checked against actual needs
      Suppose the business says:
        "Customers need to download their invoices."
      The requirement document says:
        "Customers can view invoices."
  
      Those aren't necessarily the same thing.
      A review involving the stakeholders can catch this difference before development.
  . Creates shared understanding 
      Because static testing happens early, different stakeholders can discuss the work product together.
          Business
             ↕
          Tester
             ↕
          Developer
             ↕
          Product Owner
  . Static Analysis is efficient for code defects
      Static analysis tools can detect certain code defects efficiently.
         
</pre>
Differences between Static Testing and Dynamic Testing
-
<pre>
  Static Testing	                                                  |            Dynamic Testing
  ---------------------------------------------------------------------------------------------------------------------------------------------------
Software is not executed                                            |  	Software is executed
Examines work products without running them	                        |   Tests the software by running it
Can be applied to executable and non-executable work products       |  	Can only be applied to executable work products
Finds defects directly                                              |	  Usually causes a failure, then the failure is analyzed to identify the defect
Can find defects in requirements, designs, code, etc.               |	  Mainly finds defects through actual execution/behavior
Can more easily find defects on rarely executed or                  |	  May have difficulty reaching rarely executed paths
  hard-to-reach paths                                               |
Can detect defects in requirements and documentation                | 	Cannot dynamically execute a requirement document
Can measure quality characteristics independent of execution        |	  Measures quality characteristics dependent on execution
Example: Maintainability                                            |	  Example: Performance efficiency
Often finds certain defects earlier                                 |	  Defects may be found later, during execution
Reviews and static analysis are common techniques                   |   Test execution is the main activity
Example: code review, requirement review, static analysis           |	  Example: functional testing, performance testing
  
</pre>
Typical defects that are easier and/or cheaper to find through static testing include:
-
  • Defects in requirements (e.g., inconsistencies, ambiguities, contradictions, omissions,
      inaccuracies, duplications)
  • Design defects (e.g., inefficient database structures, poor modularization)
  • Certain types of coding defects (e.g., variables with undefined values, undeclared variables,
      unreachable or duplicated code, excessive code complexity)
  • Deviations from standards (e.g., lack of adherence to naming conventions in coding standards)
  • Incorrect interface specifications (e.g., mismatched number, type or order of parameters)
  • Specific types of security vulnerabilities (e.g., buffer overflows)
  • Gaps or inaccuracies in test basis coverage (e.g., missing tests for an acceptance criterion)
  
  How defects are found
  -
  <pre>
    Static Testing
      |_ Static finds defects directly.
      |_ A static analysis tool may directly identify a code vulnearability , check code statically : 
        Work Product
             ↓
        Examine it
             ↓
        DEFECT FOUND
    
    Dynamic Testing
      |_ Dynamic produces failures, then defects are identified through analysis.
        Execute Software
               ↓
           FAILURE
               ↓
        Analyze failure
               ↓
           DEFECT FOUND
  </pre>
  Feedback and review Process
  -
  <pre>
    Early feedback helps identify problems before too much work has been done.
    Frequent feedback helps the team understand requirement changes earlier.
    Feedback prevents misunderstandings
    Regular feedback gives developers and testers a better understanding of:
      |_ What does the stakeholder actually need?
    Stakeholder feedback means getting their input about the product, requirements, features, and progress.
  </pre>
