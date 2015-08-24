## HyperOS

**caution** mostly vaporware, don't take this seriously yet

### technical features

- runs a tiny cross platform linux VM (10mb tinycore linux)
- goal is to run the same on mac, linux, and windows
- will integrate with OS hypervisors on OS X and Windows (xhyve, hyper-v)
- can run user supplied OS images inside the host (chroot/cgroup/namespaces)
- filesystem in the host is actually fuse that proxies data from hyperfs over local network
- hyperfs is a content-addressable union file system build on top of fuse, hyperlog, leveldb and node
- thanks to hyperfs files are deduplicated across images, and images are versioned (git-like)
- tinycore VM only contains a networking stack and a rust network fuse daemon for mounting data from external hyperfs

### design goals

- code reproducibility through content addressable OS images running on linux everywhere
- no large dependencies, making it fast to install and run
- secure sandboxing is not a design goal, assumes code is trusted. hyperos is a dependency management tool
