Pig
===

Three ways to run
---
* Grunt interactive shell
* Pig Latin script
* embedded queries inside Java programs (_PigServer_ class)

Two modes to run
---
* Local mode:
```Pig
pig -x(-exectype) local
```
* Hadoop mode (MapReduce mode), the default
```Pig
pig -x(-exectype) mapreduce
```

Utility commands
---
* help
* quit
* kill _jobid_
* set debug [on|off]
* set job.name '_jobname_'

File commands
---
* cat
* cd
* copyFromLocal
* copyToLocal
* cp
* ls
* mkdir
* mv
* pwd
* rm
* rmf
* exec
* run

Data operators
---
#### LOAD
```Pig
alias = LOAD 'file' [USING function] [AS schema];
```
Load data from a file into a relation. Uses the PigStorage load function as default
unless specified otherwise with the USING option. The data can be given a schema
using the AS option.

#### LIMIT
```Pig
LIMIT alias = LIMIT alias n;
```
Limit the number of tuples to n. When used right after alias was processed by an
ORDER operator, LIMIT returns the first n tuples. Otherwise there’s no guarantee which
tuples are returned. The LIMIT operator defies categorization because it’s certainly
not a read/write operator but it’s not a true relational operator either. We include it here
for the practical reason that a reader looking up the DUMP operator, explained later, will
remember to use the LIMIT operator right before it.

#### DUMP 
````Pig
DUMP alias;
```
Display the content of a relation. Use mainly for debugging. The relation should be
small enough for printing on screen. You can apply the LIMIT operation on an alias to
make sure it’s small enough for display.

#### STORE 
```Pig
STORE alias INTO 'directory' [USING function];
```
Store data from a relation into a directory. The directory must not exist when this
command is executed. Pig will create the directory and store the relation in files named
part-nnnnn in it. Uses the PigStorage store function as default unless specified
otherwise with the USING option.
