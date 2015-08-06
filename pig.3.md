Pig
===

Relational operators
---
#### SPLIT
```Pig
SPLIT alias INTO alias IF expression, alias IF expression [, alias IF expression ...];
```
Splits a relation into two or more relations, based on the given Boolean expressions. 
Note that a tuple can be assigned to more than one relation, or to none at all.

#### UNION
```Pig
alias = UNION alias, alias, [, alias ...]
```
Creates the union of two or more relations.
Note that:
* As with any relation, there’s no guarantee to the order of tuples
* Doesn’t require the relations to have the same schema or even the same number of fields
* Doesn’t remove duplicate tuples

#### FILTER
```Pig
alias = FILTER alias BY expression;
```
Selects tuples based on Boolean expression. Used to select tuples that you want or remove tuples that you don’t want.

#### DISTINCT
```Pig
alias = DISTINCT alias [PARALLEL n];
```
Remove duplicate tuples.

#### SAMPLE
```Pig
alias = SAMPLE alias factor;
small_data = SAMPLE large_data 0.01;
```
Randomly sample a relation. The sampling factor is given in factor. Not exactly 1%. May not be the same each time.

#### FOREACH
```Pig
alias = FOREACH alias GENERATE expression [,expression...] [AS schema];
```
Loop through each tuple and generate new tuple(s).
Usually applied to transform columns of data, such as adding or deleting fields.
One can optionally specify a schema for the output relation; for example, naming new fields.

#### FOREACH (nested)
```Pig
alias = FOREACH nested_alias {
  alias = nested_op;
  [alias = nested_op; ...]
  GENERATE expression [, expression ...];
};
```
Loop through each tuple in nested_alias and generate new tuple(s).
At least one of the fields of nested_alias should be a bag.
DISTINCT, FILTER, LIMIT, ORDER, and SAMPLE are allowed operations in nested_op to operate on the inner bag(s).

#### JOIN
```Pig
alias = JOIN alias BY field_alias, alias BY field_alias [,alias BY field_alias …] [USING "replicated"] [PARALLEL n];
```
Compute inner join of two or more relations based on common field values.
When using the replicated option, Pig stores all relations after the first one in memory for faster processing.
You have to ensure that all those smaller relations together are indeed small enough to fit in memory.
Under JOIN, when the input relations are flat, the output relation is also flat.
In addition, the number of fields in the output relation is the sum of the number of
fields in the input relations, and the output relation’s schema is a concatenation of the input relations’ schemas.

#### GROUP
```Pig
alias = GROUP alias { [ALL] | [BY {[field_alias [,field_alias]] | * | [expression]] } [PARALLEL n];
```
Within a single relation, group together tuples with the same group key. 
Usually the group key is one or more fields, but it can also be the entire tuple (*) or an expression.
One can also use GROUP alias ALL to group all tuples into one group.
The output relation has two fields with autogenerated names.
The first field is always named “group” and it has the same type as the group key.
The second field takes the name of the input relation and is a bag type.
The schema for the bag is the same as the schema for the input relation.

#### COGROUP
```Pig
alias = COGROUP alias BY field_alias [INNER | OUTER], alias BY field_alias [INNER | OUTER] [PARALLEL n];
```
Group tuples from two or more relations, based on common group values.
The output relation will have a tuple for each unique group value. Each tuple will have the group value as its first field.
The second field is a bag containing tuples from the first input relation with matching group value.
Ditto for the third field of the output tuple.
In the default OUTER join semantic, all group values appearing in any input relation are represented in the output relation.
If an input relation doesn’t have any tuple with a particular group value, it will have an empty bag in the corresponding output tuple.
If the INNER option is set for a relation, then only group values that exist in that input relation are allowed in the output relation.
There can’t be an empty bag for that relation in the output.
You can group on multiple fields. For this, you have to specify the fields in a comma-separated list enclosed by parentheses for field_alias.
COGROUP (with INNER) and JOIN are similar except that COGROUP generates nested output tuples.

#### CROSS
```Pig
alias = CROSS alias, alias [, alias …] [PARALLEL n];
```
Compute the (flat) cross-product of two or more relations.
This is an expensive operation and you should avoid it as far as possible.

#### ORDER
```Pig
alias = ORDER alias BY { * [ASC|DESC] | field_alias [ASC|DESC] [, field_alias [ASC|DESC] …] } [PARALLEL n];
```
Sort a relation based on one or more fields.
If you retrieve the relation right after the ORDER operation (by DUMP or STORE), it’s guaranteed to be in the desired sorted order.
Further processing (FILTER, DISTINCT, etc.) may destroy the ordering.

#### STREAM
```Pig
alias = STREAM alias [, alias …] THROUGH {'command' | cmd_alias } [AS schema];
```
Process a relation with an external script.