# MobileAutomation
Test Driven Framework developed using Java with TestNG, Extent Reports.

Can work on both android, ios including physical devices, emulators.

## Technologies/Tools used in building the framework</br>
- Eclipse - IDE</br>
- Appium - Mobile Automation library</br>
- Maven - Build automation tool</br>
- Java - Programming language</br>
- TestNG - Test Management library</br>
- Log4J - Logging framework</br>
- Extent Reports - Reporting framework</br>
- JSON/Excel - Test Data</br>
- XML - Static text</br>
- GitHub - Version control</br>
- Gitlab - CI/CD</br>

## Framework implements below best practices</br>
- Code reusability</br>
- Code readability</br>
- Scalable automation (demonstrated using multiple test classes)</br>
- Uses explicit waits</br>
- Abstraction layer for UI commands like click, sendkeys, etc.</br>
- Parameterization using TestNG XML and config.properties</br>
- Alternate Design approach [Without using inheritance]</br>
- Exception handling [using Try/Catch and TestNG Listener]</br>
- Abstraction layer for test data</br>
- Abstraction layer for static text</br>
- Supports iOS and Android</br>
- Demonstrates how to define UI elements that are common across pages (e.g. menu bar, side bar, etc.)</br>
- How to recover from test failure/ how to write fail safe test cases</br>
- Scrolling for both Android and iOS (using touchaction, uiScrollable, mobile:scroll)</br>
- Demonstrates how to effectively capture Screenshots/Videos</br>
- Supports parallel execution on multiple real Android and iOS devices</br>
- Integrated with Log4J2 Logging framework (supports basic as well as parallel logging)</br>
- Integrated with Extent Reporting framework (supports parallel, screenshots, logging test steps)</br>

## Prequisites:

- Appium server installed on the machine. In case not, install it by running command npm install -g appium. For more details visit: https://appium.io/docs/en/about-appium/getting-started/?lang=en

- iOS Simulator or Android Emulator or real device to execute tests.

- Install Maven in your machine. Maven is a build tool (can be downloaded from here). pom.xml file is present in base directory which has all the required dependencies and code to invoke testng.xml file when executed from command line.

###### How to use this framework?

- Clone the repository to your workspace.
- Open the testdata.xlsx under the src/test/resources folder
- In the RunManager sheet -->Choose the test cases you want to run by choosing yes
- In the testdata sheet --->Choose the test data you want to pass to the testcase from excel sheet.
- The data from the excel sheet will be passed to the test method as a hashtable.
- Run the testng.xml file. You can even run as mvn test which will trigger the testng.xml

###### How the framework works?

AnnotationTransformer class which implements IAnnotationTransformer is reponsible for reading the data from RunManager sheet in testdata.xlsx It sets the annotation of the test methods like description,enabled, priority, dataprovider values read from the excel.

**Things to note** : Test name in the first column of the excel sheet should match with atleast an @Test available in test classes mentioned in the testng.xml

All the tests will have the same dataprovider in the TestUtils class. For example the loginTest in RunManager sheet of testdata.xlsx will take the data from TestData sheet which have row where the testname is loginTest. If there are multiple rows with loginTest as test name , framework will consider it as this as multiple iterations for a test case.

###### How to run on different mobile devices or emulators?

Type adb devices in the cmd(Make sure adb is installed and path set correctly) and update the values generated in the udid column of TestData sheet in testdata.xlsx</br>
Device name can be anything but not null(Used to denote the device where you are running the test like MyS9Device)</br>
Port is used for parallel execution. If there are two different ports used and testng threadcount is two ,then two tests will be run in parallel.</br>
You can use more ports if you want to increase the parallel execution count.</br>

**Other tips:**

TestCase description given in the excel sheet will be displayed in the extent reports.</br>
Reusable methods are placed in BasePage.java and can be utilised in your tests.</br>
Data from excel sheet will be available as Hashtable parameter to your tests. You can fetch the value using data.get("columnnameinexcel") Refer the already existing tests for more details.</br>
Make sure that your appium server is up and running before starting the tests.</br>
Please feel to report any issue or PR for any improvements. Reach me at tushar.dhage95@gmail.com</br>

#AppiumTutorials #PageObjectModel #TestNG
