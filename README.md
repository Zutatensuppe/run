# run

Script to call other scripts in a unified way.

## Getting started

1. Put `run` into a folder :)
```
$ tree .
.
├── [...]
└── run
```

2. Create a scripts folder next to it
```
$ mkdir scripts

$ tree .
├── [...]
├── scripts
└── run
```

3. Create a script and make it executable
```
$ echo "#\!/bin/sh\\necho \"hi, this is \$RUN_TASK\"" > scripts/mytask
$ chmod +x scripts/mytask
```

4. Run the script via `run`
```
$ ./run mytask
hi, this is mytask
```

## Environment variables (set by `run`)

The following environment variables are exported before `run` calls
a script, so they are always available:

**RUN_BIN**  

The path to `run`. This is useful if other scripts need to 
be called from a script.  

**RUN_DIR**  

The directory in which `run` exists.  

**RUN_TASK**  

The task that was given to `run`.  

## Additional Environment variables (convention)

The following environment variables are not set by `run`, but should
be used according to their description when needed:

**RUN_ENV**  

Environment in which run is being called. This is useful if scripts
need to behave differently in different environments. Example values
could be `"production"`, `"dev"` or `"ci"`.