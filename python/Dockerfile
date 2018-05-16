FROM lisa/musl-cross:1.1.19
MAINTAINER Lisa Seelye <lisa@thedoh.com>
# Upstream maintainer:
#MAINTAINER Andrew Dunham <andrew@du.nham.ca>

RUN apt-get update && apt-get install -y zip

# Add our build script
ADD . /build/

# This builds the program and copies it to /output
RUN /build/build.sh

###
FROM scratch
MAINTAINER Lisa Seelye <lisa@thedoh.com>
WORKDIR /
COPY --from=0 /output/python* /
ENV \
  PYTHONHOME=/python2.7.zip \
  PYTHONPATH=/python2.7.zip

ENTRYPOINT [ "/python", "-s", "-S" ]

