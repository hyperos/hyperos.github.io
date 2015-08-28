
caution: mostly vaporware, don't take this seriously yet

![logo](hyperos.png)

HyperOS is a set of components that make it easy to quickly download and run containerized software on top of version controlled data in a reproducible way without sacrificing performance.

Whereas other container tools tend to focus on secure cloud deployment use cases, HyperOS is more like a cross platform container package manager designed to do software + data dependency management. It works on Linux, Mac and soon Windows and is intended to be used primarily as an end-user CLI tool on workstations.

### components

- [hyperfs](https://www.npmjs.com/package/hyperfs) - content-addressable userspace union file system
- [hyperlog](https://www.npmjs.com/package/hyperlog) - merkle DAG that replicates based on scuttlebutt logs and causal linking
- [hypercore](https://github.com/maxogden/hypercore) - a distribution of tinycore linux that includes our remote fs mounting daemon hyperfused
- [hyperfuse](https://github.com/mafintosh/hyperfuse) - expose a filesystem over tcp or stdio
- [hyperfused](https://github.com/mafintosh/hyperfused) - mount a remote hyperfuse drive over tcp or stdio (C daemon)
- [mini-container](https://github.com/mafintosh/mini-container) - a minimal container runtime that does very few things

### technical features

- runs a tiny cross platform linux VM (10mb tinycore linux)
- will run hypercore in OS hypervisors on OS X and Windows (xhyve, hyper-v)
- can run user supplied OS images inside hypercore (containers, either chroot or runc)
- filesystem in the host is actually a userspace filesystem (hyperfuse) that proxies fs over local network to/from host OS
- hyperfs is a content-addressable union userspace file system build on top of fuse, hyperlog, leveldb and node
- thanks to hyperfs files are deduplicated across images, and images are versioned (git-like)
- can 'lazy boot' images, fetching the files on demand needed to execute users code quickly
- tinycore VM only contains a networking stack and a network fuse daemon (hyperfuse) for mounting data from external hyperfuse

### design goals

- encourage code reproducibility by making a cross platform container host environment with a content addressable filesystem easy to use
- be container runtime agnostic, e.g. support [runc](https://github.com/opencontainers/runc), [mini-container](https://github.com/mafintosh/mini-container) and any others depending on the use case
- secure code sandboxing is not a goal of this project, we instead delegate that responsibility to the container runtime
- support mac, linux, and windows without any heavy dependencies (e.g. no kernel extensions or build chains)
- don't sacrifice performance (e.g. don't run in virtualbox, instead use fast kernel level hypervisors)
- no large dependencies, making it fast to install and run (e.g. no virtualbox)
- unix philosophy: be composable by focusing on one thing: removing software dependency conflict issues
- use alongside [dat](http://dat-data.com) (also built on hyperfs) to version code and data together

