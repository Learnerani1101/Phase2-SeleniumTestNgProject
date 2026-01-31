Pizza Hut Automation Framework
🎓 Phase 2 - Course End ProjectThis project focuses on automating the end-to-end user journey of the pizzahut.co.in e-commerce platform. Utilizing Selenium WebDriver with Java and TestNG, the framework implements a robust Test-Driven Development (TDD) approach combined with the Page Object Model (POM) to ensure scalability, maintainability, and alignment with business requirements.
📚 Table of Contents
Project OverviewTechnical Architecture & DesignTech StackProject StructureTest Data ManagementTest Scenarios & DeliverablesReporting & Results
1. Project Overview
The goal of this project is to automate critical functionalities of the Pizza Hut website, including location services, menu navigation (Sides/Drinks), and complex basket validation logic. By separating test logic from browser interaction, the suite minimizes maintenance efforts and enhances script reliability.
2. Technical Architecture & DesignThe framework follows a modular architecture based on the following patterns:
    TDD with TestNG: Drives the testing process through structured test cases and assertions.
    Page Object Model (POM): Each web page is represented as a distinct Java class, encapsulating elements and behaviors.Page Factory: An extension of POM used to initialize web elements dynamically using the @FindBy annotation for better performance and readability.
3. Tech StackComponent 
    Technology Language Java
    Automation ToolSelenium WebDriver
    Test Framework TestNG
    Build Tool Maven
    Data Handling Apache POI (Excel), Properties File
    Reporting Extent Reports4. 
    
4. Project Structure
Plaintext
phase2-selenium-automation-with-testng-project2
├── src/main/java
│   ├── base
│   │   └── BaseTest.java               # Driver initialization & teardown
│   ├── pages
│   │   ├── HomePage.java               # Location & Pop-up handling
│   │   ├── OrderDealPage.java          # Deals validation
│   │   ├── SidesMenuPage.java          # Adding sides to basket
│   │   ├── DrinkMenuPage.java          # Adding drinks to basket
│   │   ├── BasketMenuPage.java         # Cart validation
│   │   └── CheckOutPage.java           # Checkout & Voucher logic
│   └── utilities
│       ├── ExtentReportUtil.java       # Report generation
│       ├── ExcelUtility.java           # Data reading logic
│       ├── ScreenshotUtil.java         # Capturing failure shots
│       ├── TestConfigurationReader.java # Reading config.properties
│       └── WebDriverFactory.java       # Browser management
├── src/test/java
│   └── testcases
│       └── E2E_OrderItem_PizzaHut_DemoTest.java
├── src/test/resources
│   ├── config.properties               # URL and global settings
│   └── TestData.xlsx                   # External test data
├── Reports
│   └── Report_2026.01.31.html          # Execution reports
├── Screenshots                         # Failure screenshots
├── E2E_OrderItem_PizzaHut_Demo_testng.xml
└── pom.xml                             # Project dependencies
5. Test Data Management
Theframework manages data through three distinct layers:
Configuration File: Global details like the Application URL are stored in config.properties.
TestNG Parameters: Environment and browser details are configured and passed via testng.xml.
External Excel: Complex test data is stored in .xlsx files and accessed via Apache POI.
6. Test Scenarios & Deliverables
The automated suite executes the following end-to-end flow:Initialization: 
Launch URL via @BeforeClass.
Location Services: 
Close auto-popups and set delivery location to Lulu Mall, Bangalore.
Navigation: Validate URL contains deals upon entering the menu.
Basket Logic (Sides): Add an item < 200 and validate the checkout button remains inactive.
Basket Logic (Drinks): Navigate to Drinks, add items to exceed a total of 200.Checkout Flow:
    Navigate to Checkout.Validate "Online Payment" is default.
    Change payment to "Cash".
    Validate "I agree" checkbox is checked by default.
    Voucher Validation: Enter a dummy voucher (12345) and validate the error message
Teardown: 
    Close driver session via @AfterClass.
7. Reporting & Results
The framework integrates Extent Reports to provide a visual representation of the test execution.Each step is logged as PASS or FAIL.
Screenshots are automatically captured and attached to the report upon test failure.Reports are timestamped (e.g., Report_2026.01.31.14.50.09.html).

8.How to Run
Clone the repository.
Update config.properties with your local settings.
Right-click E2E_OrderItem_PizzaHut_Demo_testng.xml and select Run As > TestNG Suite.Alternatively, use Maven: mvn clean test.
