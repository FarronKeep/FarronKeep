If `core` file did not show up after program crashed, check if `user limits` are preventing `core` file from being created.

`User limits` - limit the use of system-wide resources. 

```bash
# C tag represents core file setting, command below allows unlimited
# number of core files to be created by kernel
ulimit -c unlimited
```

Content of `/proc/sys/kernel/core_pattern` is the file name of `core` files created, it could be changed at will.
