FROM ubuntu:trusty

RUN apt-get update && apt-get upgrade && apt-get install -y build-essential checkinstall wget && apt-get build-dep imagemagick -y
RUN wget https://www.imagemagick.org/download/ImageMagick.tar.gz
RUN mkdir /out
RUN tar -zxvf ImageMagick.tar.gz
RUN ln -s $(find ImageMagick-* -type d | head -n 1) /imagemagick
WORKDIR /imagemagick
RUN ./configure
RUN make clean
RUN make
RUN checkinstall
RUN ldconfig /usr/local/lib
RUN find *.deb -type f

CMD cp *.deb /out