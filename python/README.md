# Building Python

This will build Python-2.7.15rc1 into a static container:

    docker build -t lisa/static-python:2.7.15rc1-r1 .

A requirement is the presence of [lisa/docker-musl-cross#use-musl-1.1.19](https://github.com/lisa/docker-musl-cross/tree/use-musl-1.1.19) tagged as `lisa/musl-cross:1.1.19`

At some point these might make it on to a public container registry but until then they will be local operations.

# Usage

By default the image will run `python -sS /entrypoint.py` but if you would prefer a Python shell invoke:

    $ docker run -ti lisa/static-python:2.7.15rc1-r1
    Python 2.7.15rc1 (default, May 17 2018, 15:15:27)
    [GCC 5.3.0] on linux2
    >>> 

## Entrypoint.py

A sample `entrypoint.py` to call an app using Factory pattern might be:

    import sys
    import os

    sys.path.append("/usr/src/app")

    os.chdir("/usr/src/app")

    from your.app import make_app

    app = make_app()

    app.run()

If you prefer to `execv` instead:

    import sys
    import os


    os.chdir("/")

    os.execv("/python", ["-s","-S","/myapp.py"])
    # No code runs after here


Or `subprocess`:

    import sys
    import os


    os.chdir("/")

    import subprocess

    subprocess.call(["/python", "-s","-S","/myapp.py"])
    # Code execution continues
