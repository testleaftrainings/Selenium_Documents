# TestNG Data Driven Testing using Excel

------------------------------------------------------------------------

## Data Driven Execution using Excel -- Execute using Maven

------------------------------------------------------------------------

## Step 1: Create Data Folder

-   Right click on project
-   Create new folder → `data`
-   Place Excel file inside (Example: `testdata.xlsx`)

------------------------------------------------------------------------

## Step 2: Add Apache POI Dependency in `pom.xml`

Check if Apache POI dependency is added. If not, add the following:

``` xml
<dependency>
  <groupId>org.apache.poi</groupId>
  <artifactId>poi</artifactId>
  <version>5.2.3</version>
</dependency>

<dependency>
  <groupId>org.apache.poi</groupId>
  <artifactId>poi-ooxml</artifactId>
  <version>5.2.3</version>
</dependency>
```

------------------------------------------------------------------------

## Step 3: Create ReadExcel Class

-   Go to `src/test/java`
-   Create class → `ReadExcel.java`

``` java
import java.io.FileInputStream;
import org.apache.poi.xssf.usermodel.*;

public class ReadExcel {

    public static String[][] readData(String fileName) throws Exception {

        XSSFWorkbook wb = new XSSFWorkbook("./data/" + fileName + ".xlsx");
        XSSFSheet sheet = wb.getSheetAt(0);

        int rowCount = sheet.getLastRowNum();
        int colCount = sheet.getRow(0).getLastCellNum();

        String[][] data = new String[rowCount][colCount];

        for (int i = 1; i <= rowCount; i++) {
            for (int j = 0; j < colCount; j++) {
                data[i - 1][j] = sheet.getRow(i).getCell(j).toString();
            }
        }

        wb.close();
        return data;
    }
}
```

------------------------------------------------------------------------

## Step 4: Create BaseClass and Set File Name

``` java
import org.testng.annotations.BeforeTest;

public class BaseClass {

    public String fileName;

    @BeforeTest
    public void setValues() {
        fileName = "testdata";
    }
}
```

------------------------------------------------------------------------

## Step 5: Use DataProvider in Test Class

``` java
import org.testng.annotations.DataProvider;
import org.testng.annotations.Test;

public class SampleTest extends BaseClass {

    @Test(dataProvider = "fetchData")
    public void loginTest(String username, String password) {
        System.out.println(username + " " + password);
    }

    @DataProvider
    public String[][] fetchData() throws Exception {
        return ReadExcel.readData(fileName);
    }
}
```

------------------------------------------------------------------------

## Step 6: Open Maven Project in Terminal

-   Right click on project
-   Select → Open in Integrated Terminal

------------------------------------------------------------------------

## Step 7: Execute using Maven Command

Run the following command:

``` bash
mvn clean test
```

Press Enter

------------------------------------------------------------------------

## Step 8: Verify Output and Check Console Logs

-   Data from Excel should be printed row by row

``` text
// Output: Test runs multiple times with Excel data
```

------------------------------------------------------------------------

## Summary

  Step   Action
  ------ ----------------------------
  1      Create data folder
  2      Add Apache POI dependency
  3      Read Excel data
  4      Set file name in BaseClass
  5      Use DataProvider
  6      Open terminal
  7      Run `mvn clean test`
  8      Verify output

------------------------------------------------------------------------
