Useful predefined Mapper implementations
----

|__Class__|__Description__|
|---------|---------------|
IdentityMapper<K,V>| Implements Mapper<K,V,K,V> and maps inputs directly to outputs
InverseMapper<K,V>| Implements Mapper<K,V,V,K> and reverses the key/value pair
RegexMapper<K>| Implements Mapper<K,Text,Text,LongWritable> and generates a (match, 1) pair for every regular expression match
TokenCountMapper<K>| Implements Mapper<K,Text,Text,LongWritable> and generates a (token, 1) pair when the input value is tokenized

Useful predefined Reducer implementations
----

|__Class__|__Description__|
|---------|---------------|
IdentityReducer<K,V>| Implements Reducer<K,V,K,V> and maps inputs directly to outputs
LongSumReducer<K>| Implements Reducer<K,LongWritable,K,LongWritable> and determines the sum of all values corresponding to the given key
