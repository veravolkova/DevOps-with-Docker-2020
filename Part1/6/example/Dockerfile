FROM ubuntu:16.04 

#RUN mkdir /mydir
WORKDIR /mydir

RUN apt-get update && apt-get install -y wget 

#RUN touch hello.txt
RUN cd > hello.txt
RUN cd > local.txt

COPY local.txt .

RUN wget http://example.com/index.html 
CMD ["/bin/bash"]