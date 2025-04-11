# apche-commons-csv

```java
import org.apache.commons.csv.CSVFormat;
import org.apache.commons.csv.CSVRecord;

import java.io.FileReader;
import java.io.Reader;
import java.util.ArrayList;
import java.util.List;

public class DataLoader {
    public static List<double[]> loadCSV(String filePath) throws Exception {
        List<double[]> data = new ArrayList<>();
        Reader in = new FileReader(filePath);
        Iterable<CSVRecord> records = CSVFormat.DEFAULT.withFirstRecordAsHeader().parse(in);
        for (CSVRecord record : records) {
            double[] row = record.stream().mapToDouble(Double::parseDouble).toArray();
            data.add(row);
        }
        return data;
    }
}
```
