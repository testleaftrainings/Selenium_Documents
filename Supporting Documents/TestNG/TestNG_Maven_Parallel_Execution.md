# TestNG Advanced Execution using Maven (Parallel Execution)

## Parallel Execution -- Execute using Maven

------------------------------------------------------------------------

## Step 1: Configure Parallel Execution in `testng.xml`

Add parallel and thread-count

``` xml
<test name="DemoTests" parallel="classes" thread-count="2">>
```

------------------------------------------------------------------------

## Step 2: Open Maven Project in Terminal

-   Right click on project
-   Select → Open in Integrated Terminal

------------------------------------------------------------------------

## Step 3: Execute using Maven Command

Run the following command:

``` bash
mvn clean test
```

Press Enter

------------------------------------------------------------------------

## Step 4: Verify Output

-   Check Terminal logs
-   Observe multiple tests running simultaneously

``` text
// Output: Tests will execute in parallel
```

------------------------------------------------------------------------

## Summary

  Step   Action
  ------ ----------------------------------------------
  1      Configure parallel execution in `testng.xml`
  2      Open terminal
  3      Run `mvn clean test`
  4      Verify parallel execution

------------------------------------------------------------------------
