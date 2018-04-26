FROM lisa/musl-cross:1.1.19
MAINTAINER Andrew Dunham <andrew@du.nham.ca>

RUN apt-get update && apt-get install -y zip

# Add our build script
ADD . /build/

# This builds the program and copies it to /output
CMD /build/build.sh
