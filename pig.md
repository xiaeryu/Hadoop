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
```shell
pig -x(-exectype) local
```
* Hadoop mode (MapReduce mode), the default
```shell
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
