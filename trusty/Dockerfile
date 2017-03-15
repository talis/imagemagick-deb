FROM ubuntu:trusty

RUN apt-get update && apt-get upgrade && apt-get install -y build-essential checkinstall wget && apt-get build-dep imagemagick -y
RUN wget https://www.imagemagick.org/download/releases/ImageMagick-6.9.7-10.tar.xz
RUN mkdir /out
RUN tar -xvJf ImageMagick-6.9.7-10.tar.xz
RUN ln -s $(find ImageMagick-* -type d | head -n 1) /imagemagick
WORKDIR /imagemagick
RUN ./configure
RUN make clean
RUN make
RUN checkinstall
RUN ldconfig /usr/local/lib
RUN find *.deb -type f

CMD cp *.deb /out
