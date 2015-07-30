Signatures for classes
========

Mapper class
---
```Java
public static class MapClass extends MapReduceBase implements Mapper<K1, V1, K2, V2> {
  public void map(K1 key, V1 value, OutputCollector<K2, V2> output, Reporter reporter) throws IOException { }
}
```

Reducer class
---
```Java
public static class Reduce extends MapReduceBase implements Reducer<K2, V2, K3, V3> {
  public void reduce(K2 key, Iterator<V2> values, OutputCollector<K3, V3> output, Reporter reporter) throws IOException { }
}
```
