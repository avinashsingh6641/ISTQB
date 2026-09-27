25-09-2026
# Ch 2 : Testing Throughout the Software Development Lifecycle
<pre>
acceptance test-driven development(ATDD),
behavior-driven development (BDD), 
domain-driven design (DDD), 
extreme programming (XP),
feature-driven development (FDD),
Kanban, Lean IT, Scrum,
test-driven development (TDD).
</pre>
Impact of Software Development Lifecycle on Testing
-
<pre>
  Testing must be adapted to the SDLC to succeed
  . Scope and timing of test activities (e.g., test levels and test types)
  • Level of detail of test documentation
  • Choice of test techniques and test approach
  • Extent of test automation
  • Role and responsibilities of a tester
  In sequential development model
    |_tester participate in requirement review ,test analysis and test design
    |_ executable code created in later phase of SDLC, Dynamic testing cannot be perform in early phase of SDLC
  In Some iterative and Incremental Development Model
    |_ each iteration deliver working prototype
    |_ in each iteration both static and dynamic testing need to perform
  In Agile
    |_ assumes changes make occure throughout the projects
    |_ therefore lightweight work product documentation and extensive test automation to make regression testing easier
</pre>
Good testing practices, independent of the chosen SDLC model
-
<pre>
  . For every software development activity, there is a corresponding test activity
  . Different test levels , have specific and different test objectives
  . Test analysis and design for a given test level begins during the corresponding development
    phase of the SDLC
  . Testers are involved in reviewing work products as soon as drafts of this documentation are
    available
</pre>
Testing as a Driver for Software Development
-
<pre>
  . Testing is implemented first , then development done to satisfy testcase to pass
  . TDD, ATDD and BDD are similar development approaches, where tests are defined as a means of
    directing development
  . Each of these approaches implements the principle of early testing and follows a shift-left approach
  Test-Driven Development (TDD):
    • Directs the coding through test cases (instead of extensive software design)
    • Tests are written first, then the code is written to satisfy the tests, and then the tests and code are
      refactored
  Acceptance Test-Driven Development (ATDD):
    • Derives tests from acceptance criteria as part of the system design process
    • Tests are written before the part of the application is developed to satisfy the tests
  Behavior-Driven Development (BDD):
    • Expresses the desired behavior of an application with test cases written in a simple form of
      natural language, which is easy to understand by stakeholders – usually using the
      Given/When/Then format.
    • Test cases are then automatically translated into executable tests
</pre>
DevOps and Testing
-
<pre>
  DevOps is an organizational approach aiming to create synergy by getting development (including
  testing) and operations to work together to achieve a set of common goals
  Benefits:
    • Fast feedback on the code quality, and whether changes adversely affect existing code
    • CI promotes a shift-left approach in testing by encouraging developers to
      submit high quality code accompanied by component tests and static analysis
    • Promotes automated processes like CI/CD that facilitate establishing stable test environments
    • Increases the view on non-functional quality characteristics (e.g., performance, reliability)
    • Automation through a delivery pipeline reduces the need for repetitive manual testing
    • The risk in regression is minimized due to the scale and range of automated regression tests
</pre>
Shift-Left Approach
-
<pre>
  The principle of early testing is sometimes referred to as shift-left because it is an
  approach where testing is performed earlier in the SDLC.
  (e.g., not waiting for code to be implemented or for components to be integrated)
  A shift-left approach might result in extra training, effort and/or costs earlier in the process but is expected
  to save efforts and/or costs later in the process.
  
</pre>
Retrospectives and Process Improvement
-
<pre>
  Retrospectives (also known as “post-project meetings” and project retrospectives) are often held at the
  end of a project or an iteration, at a release milestone, or can be held when needed.
  In these meetings the participants (not only testers, but also e.g., developers, architects,
  product owner, business analysts)
  |_ • What was successful, and should be retained?
  |_ • What was not successful and could be improved?
  |_ • How to incorporate the improvements and retain the successes in the future?
  
</pre>
Test Levels and Test Types
-
<pre>
  Each test level is an
  instance of the test process, performed in relation to software at a given stage of development, from
  individual components to complete systems or, where applicable, systems of systems.
  Test Levels:
     • Component testing (also known as unit testing):
        focuses on testing components in isolation. 
        It often requires specific support, such as test harnesses or unit test frameworks.
        Component testing is normally performed by developers in their development environments.
  
     • Component integration testing (also known as unit integration testing):
        focuses on testing the interfaces and interactions between components.
        Component integration testing is heavily dependent on the integration strategy approaches
        like bottom-up, top-down or big-bang.
  
     • System testing :
        focuses on the overall behavior and capabilities of an entire system or product,
        often including functional testing of end-to-end tasks and the non-functional testing of quality
        characteristics. 
        System testing may be performed by an independent test team, and is
        related to specifications for the system.
  
      • System integration testing:
        focuses on testing the interfaces of the system under test and other systems and external services .
        System integration testing requires suitable test environments
        preferably similar to the operational environment.

      • Acceptance testing: 
        focuses on validation and on demonstrating readiness for deployment,
        which means that the system fulfills the user’s business needs. Ideally, acceptance testing should
        be performed by the intended users.
        The main forms of acceptance testing are:
        user acceptance testing (UAT), operational acceptance testing, contractual and regulatory acceptance testing,
        alpha testing and beta testing.

      Points to remeber :
            Component testing	 One component
            Component integration	Component ↔ Component
            System testing	Complete system
            System integration	System ↔ Other system/external service
            Acceptance	Business/user needs
  Test Types:
      . Functional Testing
          Examples: User should be able to reset their password.
          Functional testing focuses on what the system does.
      . Non Functional Testing
          How well does the system perform?
          Examples:Performance,Usability,Security,Reliability,Compatibility,Scalability
                    Can 10,000 users log in simultaneously?
      . Black-box Testing
          You care about:
          Input → Expected result
          You don't need to know how the code works internally.
  
               INPUT
                 ↓
           ┌─────────────┐
           │ Application │
           └─────────────┘
                 ↓
               OUTPUT
          Types:
            |_ Equivalence partitioning
            |_ Boundary value analysis
            |_ Decision table testing
            |_ State transition testing

      . White Box Testing
          White-box testing considers the internal structure/code of the software.
  
</pre>
Confirmation Testing and Regression Testing
-
<pre>
  Changes are typically made to a component or system to either enhance it by adding a new feature or to
  fix it by removing a defect
  1) Conformation Testing:
      confirms that an original defect has been successfully fixed. Depending on the risk,
      one can test the fixed version of the software in several ways, including:
      • executing all test cases that previously have failed due to the defect, or, also by
      • adding new tests to cover any changes that were needed to fix the defect
      it can be done by re producing the steps and checking failure does not occure
  2) Regression Testing:
      confirms that no adverse consequences have been caused by a change, including a
      fix that has already been confirmation tested.
      regression testing is a strong candidate for automation.
      Automation of these tests should start early in the project.
</pre>
Maintenance Testing
-
<pre>
  The software is already in use → something changes → we need testing.
  can be done when , hot fixes, or migration of environment from one system to another, or retirement of application
  involves
  |_ planned release/deployments
  |_ unplanned release/deployments (hot fixes)
  The scope of maintenance testing typically depends on:
    • The degree of risk of the change
    • The size of the existing system
    • The size of the change
</pre>

Quick Summary to remember for paper
-
<pre>
  What are you testing?
        │
        ├── One component
        │       → Component testing
        │
        ├── Components interacting
        │       → Component integration testing
        │
        ├── Complete application
        │       → System testing
        │
        ├── Application + external system
        │       → System integration testing
        │
        └── Business/user acceptance
                → Acceptance testing

  A defect was fixed
       │
       ├── Is the defect fixed?
       │       → Confirmation testing
       │
       └── Did the change break something else?
               → Regression testing

  Existing system changed
        ↓
  Maintenance testing
</pre>



