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

Risk Management
-
<pre>
  Risk management is the process of identifying possible problems, understanding their effects, and taking action to reduce them.
    Its benefits include:
      |_ Increasing the chances of achieving objectives.
      |_ Improving product quality.
      |_ Increasing stakeholders' confidence and trust.
  Main risk management activities
  1. Risk Analysis
    Identify possible risks and assess how serious they are.    
      Risk identification: What could go wrong?    
      Risk assessment: How likely is it, and how much damage could it cause?

  2. Risk Control
    Take action to reduce risks and keep checking them.    
      Risk mitigation: What can we do to reduce the risk?    
      Risk monitoring: Is the risk changing? Are our actions working?

  What is Risk-Based Testing?
  Risk-based testing (RBT) is a testing approach in which testing activities are selected, prioritized, and managed based on risk.
  In simple words, test the most risky features first.
  e.g in banking application payemnt feature is at higher risk to test it first
      then login then css based stuff 

  Risk Definition and Risk Attributes
    A risk is a potential event or situation that could cause a negative effect if it occurs.
    Risk has two main attributes:
      A. Risk Likelihood
        Likelihood means the probability that a risk will occur.
        For example:
          A bug has a 10% chance of occurring → low likelihood.
          A bug has an 80% chance of occurring → high likelihood.
      B. Risk Impact
        Impact means the amount of harm or damage caused if the risk occurs.
        For example:      
          A spelling mistake on a webpage → low impact.        
          An incorrect bank balance → high impact.
    so formula for risk level : 
      |_ Risk Level=Likelihood×Impact

  Project Risks vs Product Risks
    A. Project Risks
      Project risks affect the project's ability to meet its objectives, particularly its schedule, budget, or scope.   
      Examples:      
        Organizational issues: Requirements or deliverables are delayed.      
        People issues: Developers lack skills or team members have communication problems.      
        Technical issues: Poor testing tools or uncontrolled changes to project scope.      
        Supplier issues: A third-party company fails to deliver required software.
    B. Product Risks
      Product risks affect the quality of the software product and may cause problems for its users.
      Examples:      
        Missing or incorrect functionality.      
        Incorrect calculations.     
        Runtime errors or application crashes.      
        Poor performance or slow response time.      
        Security vulnerabilities.      
        Poor user experience.
</pre>
Product Risk Analysis
-
<pre>
  Identify what can go wrong in the software, evaluate how serious it is, and plan testing accordingly.
  Product risk analysis is the process of identifying and evaluating risks related to software quality
  so that testing can focus on the areas where failures would matter most.
  What is residual product risk?
    Residual risk is the risk that remains even after risk-reduction activities, including testing, have been performed.
  For example:
    Testers identify a possible money transfer error.
    Developers fix the defect.
    Testers execute tests to verify the fix.
    Some possibility of an undiscovered defect still remains.
    That remaining possibility is residual risk.
  
    The goal is to minimize residual product risk to an acceptable level, not necessarily eliminate every risk.
  Important ISTQB point: 
    Product risk analysis should ideally start early in the Software Development Life Cycle (SDLC), 
    rather than waiting until the software is complete.

  Two Main Activities of Product Risk Analysis
  1. Risk Identification
    Question: What could go wrong?   
    The objective is to create a comprehensive list of possible product risks. 
    Common techniques include:
      Brainstorming: Team members share ideas about possible failures.
      Workshops: Stakeholders discuss risks together.
      Interviews: Ask developers, users, testers, and business experts about possible problems.
      Cause-effect diagrams: Identify possible causes of a problem and their effects.
  2. Risk Assessment
    Question: How serious are these risks?
    After identifying risks, the team evaluates and prioritizes them.   
    Risk assessment includes:    
      Categorizing the identified risks.   
      Determining risk likelihood.   
      Determining risk impact.    
      Evaluating the risk level.   
      Prioritizing risks.  
      Proposing ways to handle them.
  Why do we categorize risks?
    For example, security risks can be grouped together, performance risks can be grouped together, and usability risks can be grouped together.
    This helps because risks in the same category can often be mitigated using similar approaches.
    For instance, several security risks might be addressed through access-control reviews and security testing.
  
  Quantitative vs Qualitative Risk Assessment
    A. Quantitative approach
      In this approach, the risk level is calculated numerically.
      Risk Level=Likelihood×Impact
    B. Qualitative approach
      In this approach,
      the risk level is determined using categories such as Low, Medium, and High, commonly organized in a risk matrix.
      rows can be likelihood and columns can be impact forming 2x2 matrix of high medium low values

  How Does Product Risk Analysis Influence Testing?
  1. Determine the scope of testing
  2. Determine test levels and test types
  3. Determine test techniques and coverage
  4. Estimate test effort
  5. Prioritize testing
  6. Identify additional risk-reduction activities
</pre>
Product Risk Control
-
<pre>
  After identifying and assessing product risks, take action to reduce them and continuously check whether those actions are working.
  1. Risk Mitigation
    Take action to reduce the risk.
  2. Risk Monitoring
    Keep checking the risk and whether mitigation is effective.

  What are the different risk response options?
    Mitigation: Reduce the risk.
    Acceptance: Live with the risk.   --> low level risk whih dont have any effect in functionality,
    Transfer: Shift certain risk responsibilities or consequences.  --> Transfer responsibility for handling certain consequences of a risk
                to another party through an arrangement or contract
    Contingency plan: Prepare what to do if the risk happens.  --> If the payment gateway goes down,
                  automatically switch to a backup gateway or provide another safe payment option.

  How can testing help mitigate product risks?
    1. Select testers with the right experience and skills
        Why? Skilled testers are more likely to discover defects related to their area of expertise.
    2. Apply an appropriate level of independence of testing
        Testing should be independent enough to provide an effective, unbiased examination.
        Why? People may miss mistakes in their own work because they are familiar with their assumptions.
    3. Conduct reviews and perform static analysis
        Examine work products or analyze code without executing the software.
        Example: A code review identifies a missing authorization check before the application is released.
    4. Apply appropriate test techniques and coverage levels
        Why? Appropriate techniques help discover defects in high-risk scenarios.
    5. Apply appropriate test types for the affected quality characteristics
        Why? Different risks require different types of testing.
    6. Perform dynamic testing, including regression testing
        
</pre>
Test Monitoring, Test Control and Test Completion
-
<pre>
  1. Test Monitoring — Are we on track?
    The test manager compares the actual progress with the planned progress and identifies that testing is behind schedule.
  2. Test Control — What should we do now?
    In simple words, after identifying a problem, you decide what action to take.
    since we are behind on schedule
    Possible actions:
      Add another tester.
      Reprioritizing tests when an identified risk becomes an issue
      Prioritize high-risk test cases.
      Adjust the test schedule.
      Investigate delays in the test environment.
  3. Test Completion — What do we do after testing?
      Test completion involves collecting and consolidating information from completed test activities,
      including testware, lessons learned and other relevant information.
      When does Test Completion happen?
        |_ When a test level is completed, such as system testing.
        |_ When an Agile iteration ends.
        |_ When a test project is completed or cancelled.
        |_ When a software system is released.
        |_ When a maintenance release is completed.
</pre>
<pre>
  Metrics Used in Testing
  Test metrics are measurements used to understand how testing is progressing,
  how good the software is, and how effective the testing activities are.
  • Project progress metrics (e.g., task completion, resource usage, test effort)
  • Test progress metrics (e.g., test case implementation progress, test environment preparation
    progress, number of test cases run/not run, passed/failed, test execution time)
  • Product quality metrics (e.g., availability, response time, mean time to failure)
  • Defect metrics (e.g., number and priorities of defects found/fixed, defect density, defect detection
    percentage)
  • Risk metrics (e.g., residual risk level)
  • Coverage metrics (e.g., requirements coverage, code coverage)
  • Cost metrics (e.g., cost of testing, organizational cost of quality)

  how to identify the correct metric
    The question mentions tasks, resources or effort → Project progress metrics.
    The question mentions test cases executed, passed, failed or the test environment → Test progress metrics.   
    The question mentions response time, availability or MTTF → Product quality metrics.    
    The question mentions defects found, fixed, density or detection → Defect metrics.    
    The question mentions remaining risk after mitigation → Risk metrics.    
    The question mentions requirements or code exercised → Coverage metrics.    
    The question mentions testing expenditure or cost of quality → Cost metrics.
</pre>
<pre>
  Purpose, Content and Audience for Test Reports
  
  Remember this simple trick:
    Progress Report = What is happening now?
    Completion Report = What happened after testing finished?
  1. What is test reporting?
    Test reporting means summarizing and communicating information about testing to stakeholders.
  
  Test Progress Report
    To communicate the current status of testing so that stakeholders can monitor progress and take corrective action when needed.
    What does a Test Progress Report contain?

    1. Test period -> The period covered by the report, such as Monday to Friday.

    2. Test progress  -> Whether testing is ahead of or behind schedule, including deviations.

    3. Impediments and workarounds -> Problems affecting testing and how the team is dealing with them.

    4. Test metrics -> Numbers such as tests passed, failed, executed and coverage achieved.

    5. New and changed risks -> Risks that appeared or changed during the reporting period.

    6. Next period's plan -> Testing activities planned for the upcoming period.

  Test Completion Report
    To summarize a completed stage of testing, evaluate the results against the original plan 
    and provide information useful for future testing or release decisions.


    1. Test summary -> Overall summary of the testing performed and its results.

    2. Testing and product quality evaluation -> Evaluation against the original test plan, objectives and exit criteria.

    3. Deviations from the test plan -> Differences in planned versus actual schedule, duration or effort.

    4. Impediments and workarounds -> Problems encountered and how they were handled.

    5. Test metrics -> Metrics collected from test progress reports.

    6. Unmitigated risks and unfixed defects -> Remaining risks and defects that were not resolved.

    7. Lessons learned -> What worked well, what went wrong and what can improve future testing.

</pre>
<pre>
  Audience of test reports
  Different stakeholders need different information. The audience affects the content, formality and frequency of reporting.
  For example:
    Testers within the same team: Usually need frequent, informal updates about execution, blockers and immediate tasks.
    Test managers and project managers: Need progress, schedule deviations, resources, metrics and risks to control testing.
    Senior management or clients: Often need concise summaries, significant risks, product quality and information supporting decisions.
    Stakeholders reviewing a completed project or test level: Need a completion summary, evaluation against objectives, outstanding defects and           lessons learned.
  Formality and frequency
    Reports shared within the same team are often frequent and informal.
    A final report for a completed project generally follows an agreed template and is usually prepared once for that completion milestone.
</pre>
<pre>
  Communicating the Status of Testing
    Communicating the status of testing means sharing information about 
    testing progress, problems, risks and results with the relevant people.
  Ways of Communicating
    1. Verbal communication
      Communicating through face-to-face meetings, daily stand-ups or discussions.
      Best for: Quick updates, clarifications and immediate problem-solving.
    2. Dashboards
      Visual displays of testing information, often updated regularly or automatically.
      Best for: Quickly understanding progress, trends and bottlenecks.
    3. Electronic communication channels
      Sharing testing updates through email, chat or other electronic messaging tools.
      Best for: Quick updates, notifications and communication across locations.
    4. Online documentation
      Recording testing information in shared online documents, wikis or project spaces.
      Best for: Information that people need to access and refer to later.
    5. Formal test reports
      Structured reports that communicate testing progress or completion.
      Best for: Formal stakeholder communication, traceability and projects requiring documented evidence.
</pre>
Configuration Management (CM)
-
<pre>
  Configuration Management (CM) is the process of identifying, controlling, tracking, and managing changes to
  testing documents, software, and test environments.
  A. Configuration Item (CI)
      A Configuration Item is any work product that needs to be identified and controlled.
      eg. test plans, test strategies, test conditions, test cases, test scripts, test results, test
          logs, and test reports as configuration items.
  B. Version Control
      Version control means keeping track of different versions of a configuration item.
  C. Baseline
      A baseline is an approved version of a configuration item or a set of configuration items
      that can only be changed through a formal change control process.
  D. Change Control
      Change control is the formal process for requesting, evaluating, approving or rejecting, and implementing changes to a baseline.
  E. Reverting to a Previous Baseline
      CM maintains records of previous baselines, so a team can restore an earlier configuration when necessary.

  The two main purposes of CM in testing
      1. Unique identification, version control, and traceability
          Every configuration item must be uniquely identified, version-controlled, tracked for changes, and related to other configuration items.
          Example: Link a requirement to its test case, test script, and test result so the team can trace them throughout testing.
      2. Unambiguous references
          Test documentation must clearly identify the exact software and document versions being used.
          Example: Instead of writing “Tested the latest build,” write “Tested application Build 11 using Test Cases V1.2.”

  How CM relates to DevOps
    Automated CM is normally included in an automated DevOps pipeline.


</pre>




