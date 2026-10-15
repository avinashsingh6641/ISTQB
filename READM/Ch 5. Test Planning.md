# Ch 5. Test Planning

Test Planning
-
<pre>
  A test plan describes the objectives, resources and processes for a test project.
  The typical content of a test plan includes:
    • Context of testing (e.g., scope, test objectives, constraints, test basis)
    • Assumptions and constraints of the test project
    • Stakeholders (e.g., roles, responsibilities, relevance to testing, hiring and training needs)
    • Communication (e.g., forms and frequency of communication, documentation templates)
    • Risk register (e.g., product risks, project risks)
    • Test approach (e.g., test levels, test types, test techniques, test deliverables, entry criteria and
      exit criteria, independence of testing, metrics to be collected, test data requirements, test
      environment requirements, deviations from the organizational test policy and test strategy)
    • Budget and schedule
</pre>
Tester’s Contribution to Iteration and Release Planning
-
<pre>
  Agile or iterative SDLCs have two main types of planning:
  1) Release Planning – Planning what to deliver in a product release.
      Tester’s responsibilities
        |_ Write testable user stories: Ensure requirements can be tested clearly.
        |_ Define acceptance criteria: Decide the conditions that must be satisfied for a feature to be accepted.
        |_ Participate in risk analysis: Identify risks related to the project and product quality.
        |_ Estimate testing effort: Estimate how much time and work testing each user story will require.
        |_ Determine the test approach: Decide the overall testing strategy, such as test levels, automation, and regression testing.
        |_ Plan testing for the release: Organize testing activities across all iterations.
  2) Iteration Planning – Planning what to develop and test in one iteration (sprint).
      Tester’s responsibilities
        |_ Perform detailed risk analysis: Identify risks associated with the specific user stories selected for the iteration.
        |_ Check testability: Verify that the stories and requirements can be tested.
        |_ Break user stories into tasks: Divide the stories into smaller activities, especially testing tasks.
        |_ Estimate testing effort for each task: Estimate the time needed for activities such as test design, execution, and defect retesting.
        |_ Identify and refine functional and non-functional aspects: Clarify what the system must do and how well it must perform.
  Note :

  User Stories --> Release Planning. --> overall project quality checked. --> product backlog
  specific Task --> Iteration Planning --> particular user stories quality checked. --> iteration backlog
</pre>
Entry Criteria and Exit Criteria
-
<pre>
  1. Entry Criteria — When can testing start?
      Definition: Entry criteria are the preconditions that must be met before a testing activity can begin.
      Typical entry criteria include:
        |_ Resources are available: Testers, tools, environment, budget, and time.
        |_ Testware is available: Requirements, user stories, test cases, and test data.
        |_ Initial quality is acceptable: For example, smoke tests have passed, indicating that the application is stable enough for further testing.
  2. Exit Criteria — When can testing finish?
      Definition: Exit criteria specify what must be achieved before a testing activity can be considered complete.
      Typical exit criteria include two categories:
      |_ A. Measures of thoroughness
            Test coverage achieved: For example, 95% requirement coverage.
            Unresolved defects: For example, no open critical defects.
            Defect density: Number of defects relative to the size of the software.
            Failed test cases: The number of tests that failed.
      |_ B. Completion criteria
            All planned tests have been executed.
            Static testing has been performed.
            All discovered defects have been reported.
            All regression tests have been automated, if this is an agreed requirement.
  What if time or budget runs out?
    Yes. Running out of time or budget can be a valid reason to end testing, even if the other exit criteria have not been met.
   Agile terminology: Definition of Ready and Definition of Done
      Definition of Ready (DoR). --> Entry Criteria
      Definition of Done (DoD).  --> Exit Criteria
</pre>
Estimation Techniques
-
<pre>
    Test Effort Estimation means predicting how much work is required to complete testing.
    The effort can be measured in person-hours or person-days.
    For example, if one tester works for 5 days, 8 hours per day, the effort is:
    5×8=40 person-hours.
    1. Estimation Based on Ratios
        Type: Metrics-based technique
        This technique uses historical data from previous projects to estimate the testing effort for a new project.
        The organization calculates a standard ratio between development effort and testing effort, then uses that ratio for future projects.
        Example
          In a previous project:
          Development effort = 300 person-days
          Testing effort = 200 person-days
          Development-to-test ratio = 3:2
          Now, a new project is expected to require 600 person-days for development.
          The ratio is still 3:2, so:
          Test effort = 600×2/3 = 400 person-days
  
    2. Extrapolation
        Type: Metrics-based technique
        Extrapolation uses measurements collected from the current project to predict the effort required for the remaining work.
        It is particularly useful in iterative and Agile SDLCs, where the team can use results from completed iterations to estimate future iterations.
        Example
          A team records its testing effort over the last three iterations:
          Iteration 1: 40 hours
          Iteration 2: 50 hours
          Iteration 3: 60 hours
          Average effort:
            40+50+60/3=50 hours

    3. Wideband Delphi
        Type: Expert-based technique
        Wideband Delphi collects estimates from multiple experts.
        Each expert estimates independently, discusses differences when needed, and estimates again until the team reaches a consensus.
        Note:
          Planning Poker
          Planning Poker is a variant of Wideband Delphi, commonly used in Agile development.

    4. Three-Point Estimation
        Type: Expert-based technique
        This technique uses three estimates to account for uncertainty.
        a : optimistic
        m : most likely
        b : pessimistic
        formula :
            E = (a + 4*m + b) / 6.
            SD = (b – a) / 6
​

</pre>
Test Case Prioritization
-
<pre>
  Once the test cases and test procedures are specified and assembled into test suites,
  these test suites
    |_ can be arranged in a test execution schedule that defines the order in which they are to be run. 
  types:
    1). Risk-based prioritization -> Test cases covering the most important risks are executed first.
    2) Coverage-based prioritization -> the test case achieving the highest coverage is executed first;
          each subsequent test case is the one that achieves the highest additional coverage.
    3) Requirements-based prioritization -> Requirement priorities are defined by stakeholders.
          Test cases related to the most important requirements are executed first.
    Note 
      However, this practice may not work if the test cases or the
      features being tested have dependencies. If a test case with a higher priority is dependent on a test case
      with a lower priority, the lower priority test case must be executed first.
  
</pre>
Test Pyramid
-
<pre>
                        /         \
                        
                      / E2E Testcase \

                  /  Integration Test    \
                        Mid size
  
              /        Unit Test              \
                      Small and Isolated

  1) Bottom layer: Unit tests (Component tests)
      These tests check a small, individual piece of software, such as a function or method.
      Granularity: Very fine; tests a small piece of functionality.
      Isolation: High; dependencies are often replaced with mocks or stubs.
      Speed: Very fast.
      Quantity: Many tests are usually needed.
  2) Middle layer: Integration tests
      These tests check whether different components or services work correctly together.
      Granularity: Larger than unit tests.
      Isolation: Lower because multiple components interact.
      Speed: Generally slower than unit tests.
      Quantity: Usually fewer than unit tests.
  3) Top layer: End-to-end (E2E) tests
      These tests check complete workflows through the system, often through the user interface.
      Granularity: Coarse; covers a large piece of functionality.
      Isolation: Lower; multiple components and dependencies are involved.
      Speed: Generally slower.
      Quantity: Usually only a few are needed for reasonable coverage.
  As you move up the pyramid:
    |_ Test granularity decreases (tests cover larger areas).
    |_ Test isolation decreases.
    |_ Execution time generally increases.
    |_ Fewer tests are typically needed.


</pre>
Testing Quadrants
-
<pre>
  The model has four quadrants: Q1, Q2, Q3, and Q4.
  Understand the two dimensions
  The quadrants are formed using two questions:
    - Who or what is the focus?
        |_ Business-facing: Focuses on business requirements and user needs.
        |_ Technology-facing: Focuses on technical aspects of the system.

    - What is the purpose of the test?
        |_ Supports the team: Helps guide development and provides feedback.
        |_ Critiques the product: Evaluates the product's behavior against expectations.

  Q1 = technical tests that guide development.
    Technology-facing
    Supports the team
    Component tests
    Component integration tests
    Usually automated
  Q2 = business requirements that guide development.
    Business-facing
    Supports the team
    Functional tests
    User story tests, examples, API tests, simulations
    Manual or automated
  Q3 = user experience and business validation.
    Business-facing
    Critiques the product
    Exploratory testing
    Usability testing, user acceptance testing(UAT)
    Often manual
  Q4 = technical quality and system behavior.
    Technology-facing
    Critiques the product
    Smoke tests
    Non-functional tests except usability
    Often automated
</pre>




