# Cucumber Framework Setup in VS Code using TestNG (Step-by-Step Guide)

------------------------------------------------------------------------

## Step 1: Create Maven Project

-   Press `Ctrl + Shift + P`
-   Type → `Maven: New Project`
-   Select → `no-archetype`
-   Enter GroupId → `com.demo`
-   Enter ArtifactId → `cucumberproject`
-   Choose Destination folder
-   Press Enter

``` text
// Output: Maven project is created
```

------------------------------------------------------------------------

## Step 2: Add Dependencies in `pom.xml`

Open `pom.xml`. Check if the dependency is added for Cucumber. If not
added, add the below dependencies:

``` xml
<dependency>
    <groupId>io.cucumber</groupId>
    <artifactId>cucumber-java</artifactId>
    <version>7.11.2</version>
</dependency>

<dependency>
    <groupId>io.cucumber</groupId>
    <artifactId>cucumber-testng</artifactId>
    <version>7.11.2</version>
</dependency>
```

------------------------------------------------------------------------

## Step 3: Project Structure Setup

-   Navigate to `src/test/java` → for Step Definition & Runner
-   Create `src/test/resources` manually → for Feature files

------------------------------------------------------------------------

## Step 4: Create Feature Layer

-   Right click `src/test`
-   Create new folder → `resources`
-   Create new package under the resources folder → `features`
-   Inside features package → create file → `login.feature`

------------------------------------------------------------------------

## Step 5: Write Feature File

Use Gherkin syntax

``` gherkin
Feature: Login

Scenario: Valid login
Given user enters username
When user enters password
Then user clicks login
```

------------------------------------------------------------------------

## Step 6: Create Step Definition Layer

-   Go to `src/test/java`
-   Create package → `stepdefinitions`
-   Create class → `LoginSteps.java`

Map steps using annotations

``` java
@Given("user enters username")
public void enterUsername() {
    System.out.println("Username entered");
}
```

------------------------------------------------------------------------

## Step 7: Create Runner Layer

-   Create package → `runner`
-   Create class → `TestRunner.java`
-   Extend `AbstractTestNGCucumberTests`

------------------------------------------------------------------------

## Step 8: Configure Runner Class

Add `@CucumberOptions`

``` java
@CucumberOptions(
    features = "src/test/resources/features",
    glue = "stepdefinitions",
    plugin = {"pretty"}
)
```

``` text
// Output: Cucumber will map feature and step definitions
```

------------------------------------------------------------------------

## Step 9: Execute Tests

-   Right click `TestRunner.java`
-   Run as TestNG Test

------------------------------------------------------------------------

## Step 10: Verify Output

-   Check console logs
-   Verify scenario execution status

------------------------------------------------------------------------

## Summary

  Step   Action
  ------ -------------------------
  1      Create Maven project
  2      Add dependencies
  3      Setup project structure
  4      Create feature
  5      Write feature file
  6      Map step definitions
  7      Create runner
  8      Configure runner
  9      Execute tests
  10     Verify output

------------------------------------------------------------------------
