# Test Plan

This document describe our test plans for this group project.

**Author**: Team 98

**Log Revision:**  
Version 3 (current) : Updated test cases.

## 1 Testing Strategy

### 1.1 Overall strategy
We will conduct required testing strategies through the entire development process until we finish our job offer comparison application. Given the definition and potential defects all the testing are going to expose, all testing strategies will be carried out at different stages of our development. We will be unit testing once each module is complete, where whomever worked on that particular module is going to test it. Integration testing will also be done by the developers of each module as they are being completed. This means that once modules that communicate with each other are completed, they should be integration tested by each developer. Once an alpha/beta version is established, we will do a system test to see, from end to end, if the component interacts with each other as intended in the specifications. System testing will be done with the entire team running the application on their own basis. If failures showcase during system testing, we will modify the application and do regression testing to see if each module still works as intended. We will loop through the process of unit, integration, system, and regression testing to ensure that the application runs seamlessly and until it satisfies all of the requirements.

In general, all team members will be involved in testing effort. Both black-box and white-box testing will be through out our testing procedure. Please refer to details in next seciton for testing details inlcuding testing techniques used in each level of testing and assigned test owners for different levels of testings.

### 1.2 Test Selection

#### Unit testing    
**Strategy:** Unit testing is intended to test the most basic piece of code in an application which will be each individual function. We will conduct unit testing through out our development effert. Each team member should be responsible for writing up unit testing cases for functions he/she is responsible for. Since each team member should be familiar with functionality of each function he/she is responsible for, so **white-box** testing techniques should be applied in unit testing procedures. 

**Testing owner:** Owner of each function. 

#### Integration testing
**Strategy:** Integration testing is performed when code modules are integrated together and is intended to expose code defects in the interfaces and in the interactions between integrated components/modules. In our development, we will perform integration testing when new module of codes is finished and is ready to be integrated to existing program. Both black-box and white-box testing techniques could be used in integration testing. The developer of the new module, since he/she is familiar with the functionality of the module, he/she should conduct a **white-box** based integration testing strategy when testing the integration of the new module. In addition, other team members who are not directly responsible for and familiar with the new module, when running integration testing for the new module, should use techniques of **black-box** testing frameworks. We will be using *boundary value analysis* and *cause-effect grpahing* techniques to test boundaries cases and cause-effect cases of our application.

**Testing owner:** Owner of each module (white-box) and other team members (black-box). 

#### Regression testing
**Strategy:** Regression testing will be performed when new features will be added to an existing system. The regression testing is needed to guaranteed that the changes newly added will not break the existing system. In this project, each team member will be responsible for development of some specific modules. We will integrate all modules when all development works are done. The regression testing will be needed when we gradually integrate modules to the system.

**Testing owner:** Owner of each module (white-box) and other team members (black-box). 


#### System testing
**Strategy:** System testing will be performed when the development of the application is finished. Black-box testing approach will be used in system testing. The testing will cover all possible use cases of the application including the testing of GUI(graphical user interface). The tester will basically be using the application as if he is a real user. Tester will be testing the application given use cases we proposed for the application.

**Testing owner:** A designated team member who is particularly responsible for testing.


### 1.3 Adequacy Criterion
We will measure the quality of our test cases according to several coverage domain that are defined separately at different test level.

#### Unit testing
For unit testing, the coverage domain is defined as code coverage that measure the ratio of functionalities (functions) accessible by our unit test cases. We target to achieve 80+% plus test coverage rate at this level.

#### Integration testing
Give use cases we proposed and designed for our application, the coverage domain at integration testing level will be defined as a domain that contains all use cases in our use case diagram. We will have check list listing out all use case and we will cover all use cases during integration testing.

#### System testing
We define coverage domain at system testing level as a domain that contains almost all possible ways of using the application.

### 1.4 Bug Tracking
We created a bug tracking list, that could be used to trace back to the functionality and the use case associated.

### 1.5 Technology
We will mainly be using manual (Inspection) approach to testing our application. This means that, as a group, we will be intensely doing a walkthrough of each test cases to ensure the user will be able to use our application without problems.

## 2 Test Cases

We've created use cases for manual testing that includes all the required functionalities and JUnit automated test cases for some of the activities.

#### Unit testing

##### Testing for CurrentJobActivity
  
|Test cases|Purpose| Steps <img width=1500/> |Expected results|Actual results|pass/fail
|----|----|----|----|----|----|
|Save Current Job| To test if current job information entered by user on the UI screen is saved into app database.| 1.Select "Current Job" from the main menu.<br> 2. Enter the job details for all the fields shown in the UI. <br>3. press "Save job" button. | DB table "jobdetails" should have a new record matching the details entered by user on screen and the current job flag is set to 1 ("currjobflag = 1").| As expected| Pass|
|Display Current Job| To test whether current job information if already exists in app database is retrieved and displayed on the UI screen.| Select "Current Job" from the main menu.| Current job UI screen should be populated with current job information retrieved from database.| As expected| Pass |
|Update Current Job| To test if updates for current job done by user on the UI screen is updated in the app database. | 1.Select "Current Job" from the main menu.<br> 2. Current Job UI screen should be loaded with current job information.<br> 3. Update any job details on the UI screen. <br>3. press "Save job" button. | DB table "jobdetails" should have the existing current job record updated with the new job information provided by user on screen.| As expected| Pass|
|Exit Current Job| To test if the user is able to go back to main menu on pressing Exit button on UI screen. | 1.Select "Current Job" from the main menu.<br> 2. Current Job UI screen should be loaded.<br> 3. Press "Exit" button on the screen. | User should see the main menu screen.| As expected| Pass |


##### Testing for JobOfferActivity and SavedJobofferActivity
|Test cases|Purpose| Steps <img width=1500/> |Expected results|Actual results|pass/fail
|----|----|----|----|----|----|
|Save job offer| To test if job offer information entered by user on the UI screen is saved into app database.| 1.Select "Job offer" from the main menu.<br> 2. Enter the job details for all the fields shown in the UI. <br>3. press "Save job" button. | DB table "jobdetails" should have a new record matching the details entered by user on screen and the current job flag is set to 0 ("currjobflag = 0").| As expected| Pass |
|Add another job offer| To test if user is able to add another job offer from the UI screen.| 1.Select "Job offer" from the main menu.<br> 2. Enter the job details for all the fields shown in the UI.<br> 3. press "Save job" button. | User should see a screen with the information 'Job offer saved' and be provided with a button to "Add another job offer", on click of which "Job offer" UI should be shown back to add another job offer.| As expected| Pass|
|Compare saved job offer 1| To test if user is able to compare saved job offer with current job if exists.| 1.Select "Job offer" from the main menu.<br> 2. Enter the job details for all the fields shown in the UI.<br> 3. press "Save job" button. | User should see a screen with the information 'Job offer saved' and be provided with a button to "Compare saved job offer with current job", on click of which "Job comparison results" UI should be shown with a table comparing the job offer saved with current job information.| As expected| Pass|
|Compare saved job offer 2| To test whether job offer comparison option is disabled when current job doesn't exist.| 1.Select "Job offer" from the main menu.<br> 2. Enter the job details for all the fields shown in the UI.<br> 3. press "Save job" button. | User should see a screen with the information 'Job offer saved' and the "Compare saved job offer with current job" button is disabled.| As expected| Pass|
|Exit job offer| To test if the user is able to go back to main menu on pressing Exit button on UI screen. | 1.Select "Job offer" from the main menu.<br> 2. Job offer UI screen should be loaded.<br> 3. Press "Exit" button on the screen. | User should see the main menu screen.| As expected| Pass|

##### Testing for ComparisonsettingsActivity
|Test cases|Purpose| Steps <img width=1500/> |Expected results|Actual results|pass/fail
|----|----|----|----|----|----|
|Save settings| To test if comparison settings information entered by user on the UI screen is saved into app database.| 1.Select "Job Settings" from the main menu.<br> 2. Enter the settings value for all the fields shown in the UI. <br>3. press "Save settings" button. | DB table "jobsettings" should have a new record matching the details entered by user on screen.| As expected| Pass |
|Update settings| To test if multiple activity of save settings will result in override or update of existing settings value in the app database. | 1.Select "Job Settings" from the main menu.<br> 2. Enter the settings value for all the fields shown in the UI.<br> 3. press "Save settings" button.| The "jobsettings" db table should have only one record and the values should be the latest values entered by user on screen.| As expected|Pass|
|Exit settings| To test if the user is able to go back to main menu on pressing Exit button on UI screen. | 1.Select "Job settings" from the main menu.<br> 2. Job settings UI screen should be loaded.<br> 3. Press "Exit" button on the screen. | User should see the main menu screen.| As expected|Pass|


##### Testing for JobComparisonActivity and JobComparisonResultsActivity
|Test cases|Purpose| Steps <img width=1500/> |Expected results|Actual results|pass/fail
|----|----|----|----|----|----|
|Display Jobs for comparison| To test if all job information (current and job offers) saved in database is displayed on the UI screen. | 1.Select "Job Compare" from the main menu.<br> 2. Job comparison UI screen should be populated with job information (current job and job offers) retrieved from database.| The job information displayed on UI screen should match the corresponding job information present in "jobdetails" db table.| As expected| Pass|
|Job ranking| To test if job information displayed on the UI screen are from best to worst based on jobscore. | 1.Select "Job Compare" from the main menu.<br> 2. Job comparison UI screen should be populated with list of jobs.| Jobs listed in the UI should be sorted based on the job score (high to low). Verify it by checking the corresponding job score from "jobdetails" db table.| As expected| Pass|  
|Job comparison 1| To test if two jobs can be selected for comparison from the UI screen. | 1.Select "Job Compare" from the main menu.<br> 2. Job comparison UI screen should be populated with list of jobs.<br> 3. Select the check boxes against two jobs to compare.<br> 4. Press "Compare" button. | 1. The selected job IDs needs to displayed on the text boxes shown on the screen for comparison.<br> 2. User should see a new screen with the job comparison results displayed in table.<br> 3. The job details should match the corresponding job details in the app database.| As expected| Pass|
|Job comparison 2| To test if job comparison is disabled when there is only one job entry in the system database. | 1.Select "Job Compare" from the main menu.| 1. Job comparison UI screen should have only one job listed.<br> 2. Compare button should be disabled.| As expected| Pass|
|Current job indication| To test whether Current job can be easily identified from the list of jobs displayed on the comparison UI screen. | 1.Select "Job Compare" from the main menu.<br> 2. Job comparison UI screen should be populated with list of jobs.| Current job details highlighted in yellow and mentioned clearly for identification. The current job detail information should match the current job record in "jobdetails" db table identified through the attribute "currjobflag = 1").| As expected| Pass|
|Job comparison results| To test if the job details of the jobs selected for comparison are displayed properly. | 1.Select "Job Compare" from the main menu.<br> 2. Job comparison UI screen should be populated with list of jobs.<br> 3. Select the check boxes against two jobs to compare.<br> 4. Press "Compare" button.  | 1. User should see a new screen with the job comparison results displayed in table for the jobs selected for comparison.<br> 2. The job details should match the corresponding job details from "jobdetails" dbtable in the database.<br> 3. Yearly salary, Signing bonus and Yearly bonus values should be adjusted as per cost of living.| As expected| Pass|
|Exit comparison| To test if the user is able to go back to main menu on pressing Exit button on UI screen. | 1.Select "Job compare" from the main menu.<br> 2. Job comparison UI screen should be loaded.<br> 3. Press "Exit" button on the screen. | User should see the main menu screen.| As expected| Pass|

##### Testing for CurrentJobActivity (<strong>JUnit</strong>)
|Test cases|Purpose| Steps <img width=1500/> |Expected results|Actual results|pass/fail
|----|----|----|----|----|----|
|Save current job| To test if the current job information entered by user can be saved to the app database. | 1. Initialize testing current job values. <br> 2. Save to the database. <br> 3. Retrieve the latest record from database. <br> 4. Compare| We should expect that the values retrieved from the database should match with initialized current job values.| As expected | Pass |
|Incorrect data type| To test if the data format of input does not follow our setup, the exception can correctly captured by our code. | 1. Initialize values with wrong data type. <br> 2. Save to the database. <br> 3. Retrieve the latest record from database. <br> 4. Compare | We should expect to see an androidx.test.espresso.PerformException exception being captured by this test.| As expected | Pass |  
|Update current job| To test if multiple updates of current job information will not result in multiple records of current job in the database. | 1. Initialize values. <br> 2. Save to the database. <br> 3. Repeat steps 1 and 2 several times. <br> 4. Retrieve the latest record from database. <br> 5. Compare | We should expect to see the same number of records before and after saving multiple recoreds for current job.| As expected | Pass|

##### Testing for ComparisonsettingsActivity (<strong>JUnit</strong>)
|Test cases|Purpose| Steps <img width=1500/> |Expected results|Actual results|pass/fail
|----|----|----|----|----|----|
|Save settings|To test if job settings information entered by user can be saved into app database.|1. Initialize job settings values. <br> 2. Save to the database. <br> 3. Retrieve the latest record from database. <br> 4. Compare | We should expect that the values retrieved from the database should match with initialized job setting values. | As expected. | Pass |
|Incorrect data type|To test if exception can be captured by inputing values of non-numbers.|1. Initialize values with wrong format. <br> 2. Save to the database. <br> 3. Retrieve the latest record from database. <br> 4. Compare | An exception of androidx.test.espresso.PerformException should be captured by the test. | As expected. | Pass |

##### Testing for JobOfferActivity class (<strong>JUnit</strong>)
|Test cases|Purpose| Steps <img width=1500/> |Expected results|Actual results|pass/fail
|----|----|----|----|----|----|
|Save job offer| To test if correct job offer information can be saved to the app database. | 1. Initialize values. <br> 2. Save to the database. <br> 3. Retrieve the latest record from database. <br> 4. Compare | We should expect that the values retrieved from the database should match with initialized job offer values. | As expected| Pass |
|Incorrect data type| To test if the data format of input does not follow our setup, the exception can correctly captured by our code. | 1. Initialize values of wrong format. <br> 2. Save to the database. <br> 3. Retrieve the latest record from database. <br> 4. Compare | We should expect to see an androidx.test.espresso.PerformException exception being captured by this test. | As expected| Pass |  
|Add job offers| To test if multiple insertion of job offer information will result in multiple records of job offers in the database. | 1. Initialize values. <br> 2. Save to the database. <br> 3. Repeat step 1 and 2 several times. <br> 4. Retrieve the latest record from database. <br> 5. Compare | The nubmer of records should match the exptected values | As expected| Pass|


#### System Integration & regression testing
In our development workflow, we plan to perform System integration and regression testing together. Because at the time when we test new changes, it make sense to make sure the existing system is also perform as it was. All tests below are designed to meet the requirement.

| Test cases|  Purpose  | Steps <img width=1500/> | Expected results |  Actual results  |pass/fail
|----|----|----|----|----|----|
|Current Job|To test if current job details are persistent and can be used by any activity in the application.|1.Select "Current Job" from the main menu.<br> 2. Enter the job details for all the fields shown in the UI.<br> 3. press "Save job" button.<br> 4. press "Exit" button.<br> 5. Select "Job Compare" from main menu |The current job details entered by user on "Current Job" screen should be listed on the "Job Comparison" screen when loaded.|As expected.| Pass
|Job offer|To test if job offer details are persistent and can be used by any activity in the application.|1.Select "Job offer" from the main menu.<br> 2. Enter the job details for all the fields shown in the UI.<br> 3. press "Save job" button.<br> 4. press "Exit" button.<br> 5. Select "Job Compare" from main menu |The job offer details entered by user on "Job offer" screen should be listed on the "Job Comparison" screen when loaded.|As expected.| Pass
|Comparison settings|To test if comparison settings are applied in calculating the job score.|1.Select "Job Settings" from the main menu.<br> 2. Enter the settings value for all the fields shown in the UI. <br>3. press "Save settings" button.<br> 4. press "Exit" button<br> 5. Select "Job offer" from main menu and enter new job offer information and save the job details |The new job offer details saved in the "jobdetails" db table should have the jobscore calculated using the weights.|As expected.| Pass
|Job comparison| To test if two jobs selected for comparison are displayed in the results screen accordingly. | 1.Select "Job Compare" from the main menu.<br> 2. Job comparison UI screen should be populated with list of jobs.<br> 3. Select the check boxes against two jobs to compare.<br> 4. Press "Compare" button. | 1. User should see a new screen with the job comparison results displayed in table for the jobs selected for comparison.<br> 2. The job details should match the corresponding job details in the app database.| As expected| Pass|
