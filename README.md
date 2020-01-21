# Workshop MVNGIT - AREP

This program calculates the mean and the standard deviation of a set of *n* real numbers from a file. 

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites
#### Java
Java 1.8 JDK is necessary, check if it is installed by typing in the command prompt `java -version` and `javac -version`. The result should be similar to this:

```
java -version
java version "1.8.0_241"
Java(TM) SE Runtime Environment (build 1.8.0_241-b07)
Java HotSpot(TM) 64-Bit Server VM (build 25.241-b07, mixed mode)

javac -version
javac 1.8.0_221
```
If the command is not recognized, you can follow the instructions to install Java JDK 1.8 [here.](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

#### Maven
Maven is also necessary, you can check if it is installed by typing in the command prompt `mvn -v`. If installed, the result should be similar to this.

```
mvn -v

Apache Maven 3.6.1 (d66c9c0b3152b2e69ee9bac180bb8fcc8e6af555; 2019-04-04T14:00:29-05:00)
Maven home: C:\Program Files\Apache Maven\bin\..
Java version: 1.8.0_221, vendor: Oracle Corporation, runtime: C:\Program Files\Java\jdk1.8.0_221\jre
Default locale: en_US, platform encoding: Cp1252
OS name: "windows 10", version: "10.0", arch: "amd64", family: "windows"
```

If the command is not recognized, you can follow the instructions to install Maven [here.](https://maven.apache.org/install.html)

### Installing

Clone the repository and go to the folder `AREP-Taller01`.

`git clone https://github.com/JulianBenitez99/AREP-Taller01.git`

To compile the project, in the command prompt type:

```
mvn package
```

This downloads the dependencies needed for the project and executes the tests. After it finishes, the project its ready for it to be used.

### Running the Project
The program receives a path to a file with the data to be used, the project contains two test data files `dat01.txt` and `dat02.txt` in [`src/main/resources`](src/main/resources).

To execute the program, in the command prompt type:

```
mvn exec:java -Dexec.args="path/to/data"
```
**[NOTE]** In case a path is not provided, the data used will be the one in `dat01.txt`. 

Example, in folder `AREP-Taller01`:
```
mvn exec:java -Dexec.args="src/main/resources/dat02.txt"

[INFO]
[INFO] ------------------< edu.escuelaing.arep.tuno:taller1 >------------------
[INFO] Building taller1 1.0-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------
[INFO]
[INFO] >>> exec-maven-plugin:1.2.1:java (default-cli) > validate @ taller1 >>>
[INFO]
[INFO] <<< exec-maven-plugin:1.2.1:java (default-cli) < validate @ taller1 <<<
[INFO]
[INFO]
[INFO] --- exec-maven-plugin:1.2.1:java (default-cli) @ taller1 ---
The mean of the data is: 60.32
The standard deviation of the data is: 62.26
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  1.022 s
[INFO] Finished at: 2020-01-19T13:05:17-05:00
[INFO] ------------------------------------------------------------------------
```

## Running the tests

The project counts with tests for the `LinkedList` and `StatisticUtils` classes. They can be run by typing in the command prompt:

```
mvn test
```

### LinkedListTest class

This class is used for testing all the implemented methods of the linked list, verifying their correct implementation.

Example:
```java
public class LinkedListTest{
    ...
    @Test
    public void shouldGetTheElementAtTheSpecifiedIndex() {
      List<Integer> compareList =  new ArrayList<>();
      List<Integer> linkedList = new LinkedList<>();
      Random random = new Random();
      for (int i = 0; i < 250; i++) {
        compareList.add(random.nextInt(1000));
      }
      linkedList.addAll(compareList);
      for (int i = 0; i < compareList.size(); i++){
         assertEquals(compareList.get(i), linkedList.get(i));
       }
    }
    ...
}
```

### StatisticUtilsTest class

Test for the methods used in statistics, mean and standard deviation.

Example:
```java
public class StatisticUtilsTest {

    @Test
    public void shouldGiveSameMeanAndStdAsTheData01(){
        List<Double> linkedList = new LinkedList<>();
        linkedList.add(160d);
        ...
        linkedList.add(624d);
        double mean = StatisticUtils.calculateMean(linkedList);
        double stdv = StatisticUtils.calculateStandardDeviation(linkedList);
        assertEquals(550.6, DoubleRounder.round(mean, 2), 0.0);
        assertEquals(572.03, DoubleRounder.round(stdv, 2), 0.0);
    }
}
```

## JavaDocs
JavaDocs are available in the `javadocs` folder. Opening `javadocs/index.html` in the browser will display them.

JavaDocs can be generated by going to `AREP-Taller01` folder and typing in the command prompt:

```
mvn javadoc:javadoc
```

The resulting JavaDocs will end in `target/site`.

## Built With
* [Maven](https://maven.apache.org/) - Dependency Management


## Authors

* **Julián Benítez Gutíerrez** - *Development* - [JulianBenitez99](https://github.com/JulianBenitez99)


## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.