24/09/2026
# Ch 1 : Fundamentals of Testing:

Testing is a major from of QC(Quality control), other methods of QC is (model checking and proof of correctness), simulation and prototyping.
QC is Product Oriented, corrective approach.  ---> detect Defects and failure.            ---> is the product right?
QA is process Oriented , preventive approach.  ---> improve process and prevent problem.    ---> is the process right?

errors,defects,failures,root cause
--
    Human beings make errors (mistakes), which produce defects (faults, bugs), which in turn may result in failures.
Testing Priciples:
--
  1. Testing shows the presence, not the absence of defects
  2. Exhaustive testing is impossible.
  3. Early testing saves time and money.
  4. Defects cluster together.
  5. Tests wear out.
  6. Testing is context dependent.
  7. Absence-of-defects fallacy.

Test Activities
--
'''
   1) test planning              ---> consists of defining the test objectives and then selecting an approach that best achieves
                                      the objectives within the constraints imposed by the overall context.
   2) test monitor and control   ---> Test control involves taking the actions necessary to
                                      meet the objectives of testing.
   3) test analysis.             ---> “what to test?”
                                      |_ identify testable features and to define and prioritize associated test conditions
                                      |_ related risks and risk levels
                                      |_ The test basis and the test objects are also evaluated
   5) test design                ---> “how to test?”
                                      |_ includes elaborating the test conditions into test cases and other testware (e.g., test charters).
                                      |_ involves the identification of coverage items, which serve as a guide to specify test case inputs.
                                      |_ includes defining the test data requirements
                                      |_ designing the test environment
                                      |_ identifying any other required infrastructure and tools
   7) test implementation.       ---> include creating or acquiring testware necessary for test execution
                                      |_  testdata organized into testsuits
                                      |_  manual and automation testscript are created
                                      |_  test procedure are prioritized and arranged for efficient test execution
                                      |_. test env are build and verified to be setup correctly
   8) test execution.            ---> includes running test in accordance with test running schedules
                                      |_ can be automated or manual
                                      |_ have multiple form , continuous testing or pair testing
                                      |_ actual test results are compared with expected
                                      |_ results are logged
                                      |_ anomalies are analyzed to identify their likely causes
   9) test completion            ---> activities usually occur at project milestones (e.g., release, end of iteration, test level completion)
                                      |_ for any unresolved defects, change requests or product backlog items created.
                                      |_ Any testware that may be useful in the future is identified
                                      |_ The test activities are analyzed to identify lessons learned and improvements for future iterations, releases, or projects
                                      |_ A test completion report is created and communicated to the stakeholders.

Testing is based on Context:
--
->testing is carried out will depend on a number of contextual factors including:
    . Stakeholders (needs, expectations, requirements, willingness to cooperate, etc.)
    • Team members (skills, knowledge, level of experience, availability, training needs, etc.)
    • Business domain (criticality of the test object, identified risks, market needs, specific legal
    regulations, etc.)
    • Technical factors (type of software, product architecture, technology used, etc.)
    • Project constraints (scope, time, budget, resources, etc.)
    • Organizational factors (organizational structure, existing policies, practices used, etc.)
    • Software development lifecycle (engineering practices, development methods, etc.)
    • Tools (availability, usability, compliance, etc.)

Testware
--
  --> Testware is created as output work products from the test activities
  • Test planning work products include:
      |_ test plan, test schedule, risk register, and entry and exit criteria 
      |_ Risk register is a list of risks together with risk likelihood, risk impact and information about risk mitigation 
      |_ Test schedule, risk register and entry and exit criteria are often a part of the test plan.
  • Test monitoring and control work products include: 
      |_ test progress reports, documentation of control directives and risk information.
  • Test analysis work products include: 
      |_ (prioritized) test conditions (e.g., acceptance criteria), and defect reports regarding defects in the test basis (if not fixed directly).
  • Test design work products include: 
      |_ (prioritized) test cases, test charters, coverage items, test data requirements and test environment requirements.
  • Test implementation work products include:
      |_ test procedures, automated test scripts, test suites, test data, test execution schedule, and test environment elements.
      |_ Examples of test environment elements include: stubs, drivers, simulators, and service virtualizations.
  • Test execution work products include:
      |_ test logs, and defect reports.
  • Test completion work products include:
      |_ test completion report, action items for improvement of subsequent projects or iterations, documented lessons learned, and change
         requests (e.g., as product backlog items).

Roles in Testing
-
Two Roles : 1) test management role 2) testing role
. Test management Role:
     |_ The test management role takes overall responsibility for the test process, test team and leadership of the test activities.
     |_ activity include --> test planning, test monitoring and control and test completion.
. Testing Role :
     |_ The testing role takes overall responsibility for the engineering (technical) aspect of testing.
     |_activities include --->  test analysis, test design, test implementation and test execution.
who get what role is purely based on project and product context, the skills of the people in the roles, and the organization.
    Different people may take on these roles at different times. For example, the test management role can
    be performed by a team leader, by a test manager, by a development manager, etc. It is also possible for
    one person to take on the roles of testing and test management at the same time.

Essential Skills and Good Practice in Testing
-
Generic Skills Required for Testing:
    • Testing knowledge (to increase effectiveness of testing, e.g., by using test techniques)
    • Thoroughness, carefulness, curiosity, attention to details, being methodical (to identify defects,
    especially the ones that are difficult to find)
    • Good communication skills, active listening, being a team player (to interact effectively with all
    stakeholders, to convey information to others, to be understood, and to report and discuss
    defects)
    • Analytical thinking, critical thinking, creativity (to increase effectiveness of testing)
    • Technical knowledge (to increase efficiency of testing, e.g., by using appropriate test tools)
    • Domain knowledge (to be able to understand and to communicate with end users/business
    representatives)
Whole Team Approach:
    In the whole-team approach any team member with the necessary knowledge and skills can perform any
    task, and everyone is responsible for quality.
Independence of Testing:
    |_ Work products can be tested by their author (no independence),
    |_by the author's peers from the same team (some independence),
    |_by testers from outside the author's team but within the organization (high independence),
    |_ or by testers from outside the organization (very high independence).
     For most projects, it is usually best to carry out testing with multiple levels of independence 
         |_ developers performing component and component integration testing,
         |_ test team performing system and system integration testing,
         |_ and business representatives performing acceptance testing.
