# Cucumber Parameterization and Scenario Outline (Step-by-Step Guide)

------------------------------------------------------------------------

## 1) Invalid Login Scenario using Parameterization

------------------------------------------------------------------------

## Step 1: Add New Scenario in Feature File

-   Open `login.feature`
-   Add new scenario for invalid login

``` gherkin
Feature: Login

Scenario: Invalid login
Given user enters username as 'invalidUser'
When user enters password as 'invalidPass'
Then user clicks login
```

------------------------------------------------------------------------

## Step 2: Parameterize Values using Quotes

-   Use single quotes `' '` for dynamic values

``` gherkin
Given user enters username as 'invalidUser'
```

------------------------------------------------------------------------

## Step 3: Update Step Definition with `{string}`

``` java
@Given("user enters username as {string}")
public void enterUsername(String username) {
    System.out.println(username);
}
```

------------------------------------------------------------------------

## Step 4: Add Password Step

``` java
@When("user enters password as {string}")
public void enterPassword(String password) {
    System.out.println(password);
}
```

------------------------------------------------------------------------

## Step 5: Keep Action Step Same

``` java
@Then("user clicks login")
public void clickLogin() {
    System.out.println("Login clicked");
}
```

------------------------------------------------------------------------

## Step 6: Execute Test

-   Right click `TestRunner.java`
-   Run as TestNG Test

------------------------------------------------------------------------

## Step 7: Verify Output

-   Check console logs
-   Invalid values should be printed

``` text
// Output: Parameters passed dynamically using {string}
```

------------------------------------------------------------------------

## Summary

  Step   Action
  ------ -----------------------
  1      Add scenario
  2      Use quotes for values
  3      Map using `{string}`
  4      Add password step
  5      Keep action step
  6      Execute test
  7      Verify output

------------------------------------------------------------------------

## Key Concept

-   Use `'value'` in feature file
-   Map with `{string}` in step definition
-   Pass inside method

------------------------------------------------------------------------
