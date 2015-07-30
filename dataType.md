Hadoop Data Types
===

Hadoop data types implement **WritableComparable**, which is a combination of the Writable and java.lang.Comparable<T> interfaces. 
Some predefined data types are:

|__Class__|__Description__|
----------|----------------
|BooleanWritable| Wrapper for a standard Boolean variable|  
|ByteWritable| Wrapper for a single byte|
|DoubleWritable| Wrapper for a Double|
|FloatWritable| Wrapper for a Float|
|IntWritable| Wrapper for a Integer|
|LongWritable| Wrapper for a Long|
|Text| Wrapper to store text using the UTF8 format|
|NullWritable| Placeholder when the key or value is not needed|


An example of a personalized data type:  
```Java
public class Edge implements WritableComparable<Edge>{
  private String departureNode;
  private String arrivalNode;
  
  public String getDepartureNode() { return departureNode;}

  @Override
  public void readFields(DataInput in) throws IOException {
    departureNode = in.readUTF();
    arrivalNode = in.readUTF();
  }

  @Override
  public void write(DataOutput out) throws IOException {
    out.writeUTF(departureNode);
    out.writeUTF(arrivalNode);
  }
  
  @Override
  public int compareTo(Edge o) {
    return (departureNode.compareTo(o.departureNode) != 0) ? departureNode.compareTo(o.departureNode): arrivalNode.compareTo(o.arrivalNode);
  }
}
```
