Pig
===

User Defined Functions
---
UDFs should be written in Java and packaged as .jar files.
#### Example
```Pig
REGISTER piggybank/java/piggybank.jar;
DEFINE Upper org.apache.pig.piggybank.evaluation.string.UPPER();
b = FOREACH a GENERATE Upper($0);
```

UDF Statements
---
#### DEFINE
```Pig
DEFINE alias { function | 'command' [...] };
```
Assign an alias to a function or command.

#### REGISTER
```Pig
REGISTER alias;
```
Register UDFs with Pig. Currently UDFs are only written in Java, and alias is the path of the JAR file.
All UDFs must be registered before they can be used.

Key Point
---
To create an eval UDF you make a Java class that extends the abstract EvalFunc<T> class.
It has only one abstract method which you need to implement:
```Java
abstract public T exec(Tuple input) throws IOException;
```
#### Example
```Java
public class UPPER extends EvalFunc<String>{
    public String exec(Tuple input) throws IOException {
        if (input == null || input.size() == 0) return null;
        try {
            String str = (String)input.get(0);
            return str.toUpperCase();
        } catch(Exception e){
            System.err.println("Failed to process input; error - " + e.getMessage());
        return null;
        }
    }
}
```


Data Classes
---
|__Pig Latin type__|__Java class__|
|------------------|--------------|
Bytearray|DataByteArray
Chararray|String
Int|Integer
Long|Long
Float|Float
Double|Double
Tuple|Tuple
Bag|DataBag
Map|Map<Object, Object>

Scripts
---
#### Command line arguments
```shell
pig -param input=excite-small.log -param size=4 Myscript.pig
```
The parameters in this script can be refered to as $input and $size.
If you run this script using the pig command, you specify the parameters using the -param name=value argument.  
Command line arguments can also be specified in a file: 

```shell
pig -param_file Myparams.txt Myscript.pig
```
An example of the Myparams.txt:
> \# Comments in a parameter file start with hash  
> input=excite-small.log  
> size=4
