caution: mostly vaporware, don't take this seriously yet

![logo](hyperos.png)

### technical features

- runs a tiny cross platform linux VM (10mb tinycore linux)
- will integrate with OS hypervisors on OS X and Windows (xhyve, hyper-v)
- can run user supplied OS images inside the host (chroot/cgroup/namespaces)
- filesystem in the host is actually fuse that proxies data from hyperfs over local network from host OS
- hyperfs is a content-addressable union file system build on top of fuse, hyperlog, leveldb and node
- thanks to hyperfs files are deduplicated across images, and images are versioned (git-like)
- can 'lazy boot' images, fetching the files on demand needed to execute users code
- tinycore VM only contains a networking stack and a rust network fuse daemon for mounting data from external hyperfs

### design goals

- code reproducibility through content addressable OS images running on linux everywhere
- support running on mac, linux, and windows
- no large dependencies, making it fast to install and run (e.g. no virtualbox)
- unix philosophy: focus on removing dependency conflicts and being composable
- integrate with dat (also built on hyperfs) to version code and data together
- secure sandboxing is not a design goal, assumes code is trusted (same as npm)

### components

- hyper - the main cli tool (WIP)
- hypercore - a distribution of tinycore linux that includes our remote fs mounting daemon (WIP)
- [hyperfs](https://www.npmjs.com/package/hyperfs) - content-addressable union file system
- [hyperlog](https://www.npmjs.com/package/hyperlog) - merkle DAG that replicates based on scuttlebutt logs and causal linking