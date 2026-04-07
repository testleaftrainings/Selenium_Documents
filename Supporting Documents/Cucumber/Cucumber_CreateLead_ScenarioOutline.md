# CreateLead Feature using Scenario Outline + BaseClass

------------------------------------------------------------------------

## Step 1: Create New Feature File

-   Go to `src/test/resources/features`
-   Create file → `CreateLead.feature`

------------------------------------------------------------------------

## Step 2: Write Feature with Scenario Outline

``` gherkin
Feature: Create Lead

Scenario Outline: Create new lead
Given user enters company name as <company>
When user enters first name as <firstname>
And user enters last name as <lastname>
Then user clicks create lead

Examples:
| company | firstname | lastname |
| TCS     | John      | Doe      |
| Infosys | Jane      | Smith    |
```

------------------------------------------------------------------------

## Step 3: Create Step Definition Class

-   Go to `src/test/java`
-   Create package → `stepdefinitions`
-   Create class → `CreateLeadSteps.java`

------------------------------------------------------------------------

## Step 4: Create BaseClass for Browser Setup

``` java
public class BaseClass {
    public void setup() {
        System.out.println("Browser launched");
    }
}
```

------------------------------------------------------------------------

## Step 5: Extend BaseClass in Step Definitions

``` java
public class CreateLeadSteps extends BaseClass {
}
```

------------------------------------------------------------------------

## Step 6: Implement Step Definitions

``` java
@Given("user enters company name as (.*)$")
public void enterCompany(String company) {
    System.out.println(company);
}

@When("user enters first name as (.*)$")
public void enterFirstName(String fname) {
    System.out.println(fname);
}

@When("user enters last name as (.*)$")
public void enterLastName(String lname) {
    System.out.println(lname);
}
```

------------------------------------------------------------------------

## Step 7: Keep Action Step

``` java
@Then("user clicks create lead")
public void clickCreateLead() {
    System.out.println("Lead created");
}
```

------------------------------------------------------------------------

## Step 8: Execute Test

-   Right click `TestRunner.java`
-   Run as TestNG Test

------------------------------------------------------------------------

## Step 9: Verify Output

-   Each row in Examples runs as separate test

``` text
// Output: Multiple executions with different data
```

------------------------------------------------------------------------

## Summary

  Step   Action
  ------ ------------------------
  1      Create feature file
  2      Use Scenario Outline
  3      Create step definition
  4      Create BaseClass
  5      Extend BaseClass
  6      Implement steps
  7      Add action step
  8      Execute test
  9      Verify output

------------------------------------------------------------------------

## Key Concept

-   Scenario Outline
-   `<>` for placeholders
-   Examples table for data
-   `(.*)` for parameter mapping
-   Multiple data execution

------------------------------------------------------------------------
