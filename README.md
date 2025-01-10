# Software-Testing

**COMPANY NAME**: CODTECH IT SOLUTION PVT.LTD

**NAME**: OM JOSHI

**INTER ID**: CT6WKCL.

**DOMAIN**: SOFTWARE TESTING.

**BATCH DURATION**: January 5th,2025 to February 20TH,2025.

**MENTOR NAME**: NEELA SANTHOSH

**DESCRIPTION**: AUTOMATE THE TESTING OF A SAMPLE WEB APPLICATION’S LOGIN

Automating the Testing of a Sample Web Application’s Login
Automated testing is an essential practice for ensuring the reliability and performance of a web application. In this case, we will walk through the process of automating the testing of a sample web application’s login feature using Selenium WebDriver, a popular tool for automating web browsers.

Prerequisites
To automate the testing of the login functionality, the following tools and libraries are required:

Selenium WebDriver: For automating browser actions.
JUnit or TestNG: To run and structure tests.
Maven (or Gradle): For managing dependencies.
Java: Programming language for writing the test scripts.
Browser Driver (e.g., ChromeDriver): Needed to interface Selenium with the browser.
Step 1: Setting Up the Project
To begin, set up a Java Maven project in your favorite Integrated Development Environment (IDE) such as IntelliJ IDEA or Eclipse.

Add Maven dependencies: In your pom.xml file, include the following dependencies for Selenium and JUnit.
xml
Copy code
<dependencies>
    <!-- Selenium WebDriver -->
    <dependency>
        <groupId>org.seleniumhq.selenium</groupId>
        <artifactId>selenium-java</artifactId>
        <version>4.0.0</version>
    </dependency>
    
    <!-- JUnit (for running the tests) -->
    <dependency>
        <groupId>org.junit.jupiter</groupId>
        <artifactId>junit-jupiter-api</artifactId>
        <version>5.7.0</version>
        <scope>test</scope>
    </dependency>
</dependencies>
Download Browser Driver: Depending on the browser you intend to use (e.g., Chrome, Firefox), download the respective WebDriver (e.g., ChromeDriver) and add it to your project’s src/main/resources folder or system path.
Step 2: Writing the Test Script
Create a test class for the login functionality. The script will open the browser, navigate to the login page, enter credentials, submit the form, and verify the result.

java
Copy code
import org.junit.jupiter.api.*;
import org.openqa.selenium.*;
import org.openqa.selenium.chrome.ChromeDriver;
import static org.junit.jupiter.api.Assertions.*;

public class LoginTest // {

    WebDriver driver;

    @BeforeEach
    public void setUp() {
        // Set the path for ChromeDriver
        System.setProperty("webdriver.chrome.driver", "path/to/chromedriver");
        driver = new ChromeDriver();
    }

    @Test
    public void testValidLogin() {
        // Navigate to the login page
        driver.get("https://example.com/login");

        // Find the username, password fields, and submit button
        WebElement usernameField = driver.findElement(By.id("username"));
        WebElement passwordField = driver.findElement(By.id("password"));
        WebElement loginButton = driver.findElement(By.id("loginButton"));

        // Input valid credentials
        usernameField.sendKeys("testuser");
        passwordField.sendKeys("password123");

        // Click the login button
        loginButton.click();

        // Assert that the user is logged in (assuming redirection to a dashboard page)
        assertEquals("https://example.com/dashboard", driver.getCurrentUrl());
    }

    @Test
    public void testInvalidLogin() {
        // Navigate to the login page
        driver.get("https://example.com/login");

        // Find the username, password fields, and submit button
        WebElement usernameField = driver.findElement(By.id("username"));
        WebElement passwordField = driver.findElement(By.id("password"));
        WebElement loginButton = driver.findElement(By.id("loginButton"));

        // Input invalid credentials
        usernameField.sendKeys("invalidUser");
        passwordField.sendKeys("wrongPassword");

        // Click the login button
        loginButton.click();

        // Assert that an error message is displayed (assuming an error element is present)
        WebElement errorMessage = driver.findElement(By.id("errorMessage"));
        assertTrue(errorMessage.isDisplayed());
    }

    @AfterEach
    public void tearDown() {
        // Close the browser
        driver.quit();
    }
}
Step 3: Test Explanation
Setup (@BeforeEach): This method initializes the WebDriver and opens a new instance of the browser before each test.
Test for Valid Login: In the testValidLogin method, the script:
Navigates to the login page.
Locates the username, password input fields, and login button using their HTML attributes (such as id).
Enters valid credentials and clicks the login button.
Verifies that the user is redirected to the dashboard page.
Test for Invalid Login: In the testInvalidLogin method, the script performs similar steps but enters invalid credentials and checks that an error message appears.
Teardown (@AfterEach): This method closes the browser after each test to ensure no browser instances remain open.
Step 4: Running the Test
To execute the test, simply run the JUnit test in your IDE or use the Maven command:

bash
Copy code
mvn test
This will run both the valid and invalid login tests.

Step 5: Enhancing the Test
Add Assertions: You can enhance the tests by adding more detailed assertions. For example, checking for specific elements (e.g., login success message or error text) or verifying the presence of certain UI elements after login.
Parameterized Testing: You can use JUnit’s @ParameterizedTest to test different sets of login credentials (valid and invalid).
Handling Waits: Use WebDriverWait to handle dynamic elements or situations where page loading time may vary.
Conclusion
Automating the testing of a web application's login functionality with Selenium WebDriver improves efficiency, consistency, and test coverage. This simple approach to automation ensures that the login page behaves as expected under different conditions. The above steps guide you in setting up the necessary environment, writing effective test scripts, and running them for both valid and invalid login cases.



