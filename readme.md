caution: this project is a work in progress

![logo](hyperos.png)

For more info see [the website](http://hyperos.io)
 
### components

- [hyperfs](https://www.npmjs.com/package/hyperfs) - content-addressable userspace union file system
- [hyperlog](https://www.npmjs.com/package/hyperlog) - merkle DAG that replicates based on scuttlebutt logs and causal linking
- [hyperfuse](https://github.com/mafintosh/hyperfuse) - expose a filesystem over tcp or stdio
- [hyperfused](https://github.com/mafintosh/hyperfused) - mount a remote hyperfuse drive over tcp or stdio (C daemon)
- [hypercore](https://github.com/maxogden/hypercore) - a distribution of tinycore linux that includes hyperfused
- [linux](https://www.npmjs.com/package/linux) - a node wrapper around the Mac OS (and eventually Windows) hypervisor that can download and run the hypercore linux VM
- [mini-container](https://github.com/mafintosh/mini-container) - a minimal container runtime that does very few things
- [dat](https://github.com/maxogden/dat) - a dataset version control tool, which will eventually incorporate the above components into its workflows