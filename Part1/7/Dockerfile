FROM ubuntu:16.04

WORKDIR /mydir 
RUN apt-get update && apt-get install -y curl
COPY script.bat .
CMD ["/bin/bash", "script.bat"]

