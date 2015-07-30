Signatures for classes
========

Mapper class
---
```Java
// Older API
public static class MapClass extends MapReduceBase implements Mapper<K1, V1, K2, V2> {
  public void map(K1 key, V1 value, OutputCollector<K2, V2> output, Reporter reporter) throws IOException { }
}

// Newer API
public static class MapClass extends Mapper<K1, V1, K2, V2> {
  public void map(K1 key, V1 value, Context context) throws IOException, InterruptedException { }
}
```

Reducer class
---
```Java
// Older API
public static class Reduce extends MapReduceBase implements Reducer<K2, V2, K3, V3> {
  public void reduce(K2 key, Iterator<V2> values, OutputCollector<K3, V3> output, Reporter reporter) throws IOException { }
}

// Newer API
public static class Reduce extends Reducer<K2, V2, K3, V3> {
  public void reduce(K2 key, Iterable<V2> values, Context context) throws IOException, InterruptedException { }
}
```
