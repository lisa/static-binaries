# Building Python

This will build Python-2.7.15rc1 into a static container:

    docker build -t lisa/static-python:2.7.15rc1-r1 .

A requirement is the presence of [lisa/docker-musl-cross#use-musl-1.1.19](https://github.com/lisa/docker-musl-cross/tree/use-musl-1.1.19) tagged as `lisa/musl-cross:1.1.19`

At some point these might make it on to a public container registry but until then they will be local operations.

# Usage

    $ docker run -ti lisa/static-python:2.7.15rc1-r1
    Python 2.7.15rc1 (default, May 15 2018, 23:33:46) 
    [GCC 5.3.0] on linux2
    >>> 

Base image info later.
