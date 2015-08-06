Pig
===

Data Type
---
#### Atomic data types
|__Type__|__Description__|
|--------|---------------|
int|Signed 32-bit integer
long|Signed 64-bit integer
float|32-bit floating point
double|64-bit floating point
chararray|Character array (string) in Unicode UTF-8
bytearray|Byte array (binary object), the default

#### Complex data types
|__Type__|__Description__|
|--------|---------------|
Tuple|A tuple is an ordered set of fields. It’s most often used as a row in a relation. It’s represented by fields separated by commas, all enclosed by parentheses.
Bag|A bag is an unordered collection of tuples. A relation is a special kind of bag, sometimes called an outer bag. An inner bag is a bag that is a field within some complex type. A bag is represented by tuples separated by commas, all enclosed by curly brackets. Tuples in a bag aren’t required to have the same schema or even have the same number of fields. It’s a good idea to do this though, unless you’re handling semistructured or unstructured data.
Map|A map is a set of key/value pairs. Keys must be unique and be a string (chararray). The value can be any type.

Expressions
---
* **Constant**: 12, 19.2, 'hello world'
* **Basic arithmetic**: +,-,*,/
* **Sign**: +x, -x
* **Cast**: (t)x
* **Modulo**: x%y
* **Conditional**: (x ? y : z)
* **Comparison**: ==,!=,<,>,<=,>=
* **Pattern matching**: x matches regex(Java style)
* **Null**: x is null, x is not null
* **Boolean**: x and y, x or y, not x

Built-in Functions
---
* **AVG**: Calculate the average of numeric values in a single-column bag.
* **CONCAT**: Concatenate two strings (chararray) or two bytearrays.
* **COUNT**: Calculate the number of tuples in a bag. See SIZE for other data types.
* **DIFF**: Compare two fields in a tuple. 
If the two fields are bags, it will return tuples that are in one bag but not the other. 
If the two fields are values, it will emit tuples where the values don’t match.
* **MAX, MIN**: The column must be a numeric type or a chararray.
* **SIZE**: Calculate the number of elements. For a bag it counts the number of tuples. 
For a tuple it counts the number of elements. For a chararray it counts the number of characters. 
For a bytearray it counts the number of bytes. For numeric scalars it always returns 1.
* **SUM**: Calculate the sum of numeric values in a single-column bag.
* **TOKENIZE**: Split a string (chararray) into a bag of words (each word is a tuple in the bag). 
Word separators are space, double quote ("), comma, parentheses, and asterisk (*).
* **IsEmpty**: Check if a bag or map is empty.
