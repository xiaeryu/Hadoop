Aggregator Functions
===

##### List of value aggregator functions supported by the Aggregate package

|__Value aggregator__|__Description__|
|--------------------|---------------|
DoubleValueSum| Sums up a sequence of double values.
LongValueMax| Finds the maximum of a sequence of long values.
LongValueMin| Finds the minimum of a sequence of long values.
LongValueSum| Sums up a sequence of long values.
StringValueMax| Finds the lexicographical maximum of a sequence of string values.
StringValueMin| Finds the lexicographical minimum of a sequence of string values.
UniqValueCount| Finds the number of unique values (for each key).
ValueHistogram| Finds the count, minimum, median, maximum, average, and standard deviation of each value.

##### Usage:
The Aggregate package under Streaming functions as a reducer that computes aggregate statistics.
You only have to provide a mapper that processes records and sends out a specially formatted output.
Each line of the mapper’s output looks like:  
**function:key\tvalue**  
Specify in the command line that:  
**-reducer aggregate**
