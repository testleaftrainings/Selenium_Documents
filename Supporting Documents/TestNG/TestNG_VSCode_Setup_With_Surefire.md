# TestNG Project Setup and Execution in VS Code (Step-by-Step Guide)

------------------------------------------------------------------------

## Step 1: Create Maven Project

-   Open VS Code\
-   Press `Ctrl + Shift + P`
-   Type → `Maven: New Project`
-   Press Enter → Provide GroupId and ArtifactId
-   Project will be created

------------------------------------------------------------------------

## Step 2: Add TestNG Dependency and Maven Surefire Plugin in `pom.xml`

-   Open `pom.xml`\
-   Verify TestNG dependency inside `<dependencies>`. If not, add the
    following dependency

``` xml
<dependency>
  <groupId>org.testng</groupId>
  <artifactId>testng</artifactId>
  <version>7.9.0</version>
  <scope>test</scope>
</dependency>
```

-   Verify Maven Surefire Plugin inside `pom.xml`. If not, add the
    following plugin

``` xml
<build>
    <plugins>

        <!-- Compiler -->
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-compiler-plugin</artifactId>
            <version>3.11.0</version>
            <configuration>
                <source>17</source>
                <target>17</target>
            </configuration>
        </plugin>

        <!-- Test Execution -->
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-surefire-plugin</artifactId>
            <version>3.2.5</version>
            <configuration>
                <suiteXmlFiles>
                    <suiteXmlFile>testng.xml</suiteXmlFile>
                </suiteXmlFiles>
            </configuration>
        </plugin>

    </plugins>
</build>
```

------------------------------------------------------------------------

## Step 3: Project Structure Setup

Navigate to:\
`src/test/java` → for Test Classes

------------------------------------------------------------------------

## Step 4: Create Test Class

-   Go to `src/test/java`
-   Right click → New Package → `testcases`
-   Right click package → New Class → `SampleTest.java`

------------------------------------------------------------------------

## Step 5: Convert Main Method to Normal Method

Remove main method syntax:
- Remove `static`\
- Remove `String[] args`
- Remove `main` keyword\
- Give meaningful method name

``` java
public void loginTest() {
    System.out.println("Test executed");
}
```

------------------------------------------------------------------------

## Step 6: Add `@Test` Annotation

-   Add `@Test` Annotation at top of the method
-   Click on the `@Test` Annotation and press `Ctrl + .`
-   Import TestNG annotation

``` java
import org.testng.annotations.Test;

@Test
public void loginTest() {
    System.out.println("Test executed");
}
// Output: TestNG will treat this as a test case
```

------------------------------------------------------------------------

## Step 7: Create `testng.xml` File

-   Right click project → New File → `testng.xml`

------------------------------------------------------------------------

## Step 8: Add Test Cases in XML

``` xml
<suite name="TestSuite">
  <test name="TestCases">
    <classes>
      <class name="testcases.SampleTest"/>
    </classes>
  </test>
</suite>
```

------------------------------------------------------------------------

## Step 9: Configure XML Snippet in VS Code

### Steps:

-   Press `Ctrl + Shift + P`
-   Type → `Snippets: Configure Snippets`
-   Press Enter
-   Select → New Global Snippets file
-   Enter file name → `testing`
-   Remove existing content
-   Paste below code

``` json
{
  "TestNG XML": {
    "prefix": "testngxml",
    "body": [
      "<!DOCTYPE suite SYSTEM \"https://testng.org/testng-1.0.dtd\" >",
      "<suite name=\"DemoSuite\">",
      "    <test name=\"DemoTests\">",
      "        <classes>",
      "            <class name=\"com.demo.SampleTest\"/>",
      "        </classes>",
      "    </test>",
      "</suite>"
    ],
    "description": "Generate a TestNG XML template"
  }
}
```

-   Save and close the file

------------------------------------------------------------------------

## Step 10: Usage of Snippets

-   Open any XML file
-   Type → `testngxml`
-   Press Enter

------------------------------------------------------------------------

## Step 11: Open Maven Project in Terminal

-   Right click on project
-   Select → Open in Integrated Terminal
-   Type → `mvn clean test`
-   Press Enter

------------------------------------------------------------------------

## Step 12: Verify Output

-   Check Terminal logs
-   Verify that the testcases should be executed in sequential manner
-   Verify test execution status (PASS/FAIL)

------------------------------------------------------------------------

## Summary

  Step   Action
  ------ ------------------------------
  1      Create Maven project
  2      Add dependencies and plugins
  3      Setup project structure
  4      Create test class
  5      Convert method
  6      Add `@Test`
  7      Create XML
  8      Add test cases
  9      Configure snippets
  10     Use snippets
  11     Execute using Maven
  12     Verify output

------------------------------------------------------------------------
