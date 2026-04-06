# TestNG DataProvider Implementation (Step-by-Step Guide)

------------------------------------------------------------------------

## Step 1: Understand DataProvider

-   DataProvider is used to pass multiple sets of data to a test method
-   Each row = one test execution

------------------------------------------------------------------------

## Step 2: Create DataProvider Method

-   Add `@DataProvider` annotation
-   Return type should be `String[][]`

``` java
import org.testng.annotations.DataProvider;

@DataProvider(name="fetchData")
public String[][] sendData() throws IOException {

    String[][] data = new String[2][3];

    data[0][0] = "TestLeaf";    
    data[0][1] = "Vineeth";
    data[0][2] = "Rajendran";

    data[1][0] = "Qeagle";
    data[1][1] = "Saranya";
    data[1][2] = "S";

    return data;
}
// Output: 2 sets of data created
```

------------------------------------------------------------------------

## Step 3: Create Test Method

-   Add `@Test` annotation
-   Use `dataProvider` attribute

``` java
import org.testng.annotations.Test;

@Test(dataProvider = "loginData")
public void loginTest(String companyName, String companyName, String lastName) {
    System.out.println(companyName + " " + companyName + " " + lastName);
}
// Output: Test will run multiple times with different data
```

------------------------------------------------------------------------

## Step 4: Link DataProvider with Test

Ensure DataProvider name matches

``` java
@DataProvider(name = "loginData")
@Test(dataProvider = "loginData")
```

------------------------------------------------------------------------

## Step 5: Execute Test

-   Ensure that the Testcase is added in `testng.xml`
-   Open terminal
-   Run → `mvn clean test`

------------------------------------------------------------------------

## Step 6: Verify Output

-   Console will show multiple executions

------------------------------------------------------------------------

## Summary

  Step   Action
  ------ -----------------------------
  1      Understand DataProvider
  2      Create DataProvider method
  3      Create test method
  4      Link DataProvider with test
  5      Execute test
  6      Verify multiple executions

------------------------------------------------------------------------
