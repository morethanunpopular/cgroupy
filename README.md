# cgroupy
cgroupy is a python module that provides a simple interface for managing cgroups

# Installation
You can install `cgroupy` using pip:

```
pip install cgroupy
```

# Usage

`cgroupy` impelemets a `cgroup` object. This object can be used to both create a new cgroup, and to interact with an existing one.  When you initialize a `cgroup` object, you must specify the CPU and memory limits you wish to set. Memory is specified in megabytes, and CPU limits are specified in CPU shares/megahertz.

```
>>> from cgroupy import cgroup
>>> c = cgroup(1000,1000,'test')
>>> c.setup()
>>> c.execute('sleep 100', join=False)
[]
>>> c.execute('sleep 100', join=False)
[]
>>> c.tasks
{'8177', '8181'}
>>> c.teardown()
```

`with` syntax is also supported for automated setup and teardown:

```
>>> with cgroup(1000,1000,'test') as c:
...   c.execute('echo hello world')
... 
hello world
```
