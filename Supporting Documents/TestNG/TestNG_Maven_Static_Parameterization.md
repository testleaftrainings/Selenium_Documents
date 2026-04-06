# TestNG Advanced Execution using Maven (Static Parameterization)

## Static Parameterization -- Execute using Maven

------------------------------------------------------------------------

## Step 1: Create Base Class with Preconditions & Postconditions

Create a BaseClass

-   Add setup method with `@BeforeMethod` (preconditions like browser
    launch, URL load)
-   Add teardown method with `@AfterMethod` (postconditions like closing
    browser)

``` java
import org.testng.annotations.BeforeMethod;
import org.testng.annotations.AfterMethod;

public class BaseClass {

    @BeforeMethod
    public void setup() {
        System.out.println("Launch Browser and Load URL");
    }

    @AfterMethod
    public void teardown() {
        System.out.println("Close Browser");
    }
}
```

------------------------------------------------------------------------

## Step 2: Add Parameters in `testng.xml`

``` xml
<parameter name="browser" value="chrome"/>
<parameter name="url" value="https://example.com"/>
```

------------------------------------------------------------------------

## Step 3: Configure `@Parameters` in BaseClass

``` java
import org.testng.annotations.Parameters;

@Parameters({"browser","url"})
@BeforeMethod
public void setup(String browser, String url) {
    System.out.println(browser);
    System.out.println(url);
}
```

------------------------------------------------------------------------

## Step 4: Open Maven Project in Terminal

-   Right click on project
-   Select → Open in Integrated Terminal

------------------------------------------------------------------------

## Step 5: Execute using Maven Command

Run the following command:

``` bash
mvn clean test
```

Press Enter

------------------------------------------------------------------------

## Step 6: Verify Output and Check Terminal Logs

-   Values from XML should be printed

``` text
// Output: Parameters passed successfully
```

------------------------------------------------------------------------

## Summary

  Step   Action
  ------ ------------------------------------------
  1      Create BaseClass with setup and teardown
  2      Add parameters in `testng.xml`
  3      Configure `@Parameters` in BaseClass
  4      Open terminal
  5      Run `mvn clean test`
  6      Verify output

------------------------------------------------------------------------
