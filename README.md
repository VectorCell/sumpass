# checksum-passthru

Tool for getting the checksum of piped input while it's in use.

Use the same way you'd use md5sum-type programs without arguments (getting data from stdin), but
unlike md5sum-type programs, checksum-passthru outputs to stderr and passes input from stdin to stdout.

For example, you could use it to verify a file as it's being downloaded:
```
curl http://url/image.iso | md5pass > image.iso 2> image.iso.md5
```

As a side note, performance seems to be superior to corresponding md5sum-type programs.

Benchmarked with `benchmark.sh` using an Intel Xeon E3-1271 @ 3.6 GHz in Ubuntu 14.04.3 LTS, built with GCC.

| Hash   | *sum     | *pass    |
|--------|----------|----------|
| MD5    | 659 MB/s | 703 MB/s |
| SHA1   | 433 MB/s | 830 MB/s |
| SHA224 | 239 MB/s | 286 MB/s |
| SHA256 | 224 MB/s | 293 MB/s |
| SHA384 | 364 MB/s | 444 MB/s |
| SHA512 | 365 MB/s | 446 MB/s |

Travis CI builds:

|Branch      |Status   |
|------------|---------|
|master      | [![Build Status](https://travis-ci.org/VectorCell/checksum-passthru.svg?branch=master)](https://travis-ci.org/VectorCell/checksum-passthru?branch=master) |
