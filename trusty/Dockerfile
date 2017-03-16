FROM ubuntu:trusty

RUN apt-get update && apt-get upgrade && apt-get install -y build-essential checkinstall wget ruby1.9 && apt-get build-dep imagemagick -y
RUN wget https://www.imagemagick.org/download/releases/ImageMagick-6.9.7-10.tar.xz
RUN gem install fpm
RUN mkdir /out
RUN tar -xvJf ImageMagick-6.9.7-10.tar.xz
RUN ln -s $(find ImageMagick-* -type d | head -n 1) /imagemagick
WORKDIR /imagemagick
RUN ./configure
RUN make clean
RUN make
RUN mkdir /tmp/out
RUN make install DESTDIR=/tmp/out
RUN ls -al /tmp/out/usr/local

CMD fpm -s dir -t deb -n imagemagick -v 6.9.7-10 -C /tmp/out -p imagemagick_VERSION_ARCH.deb usr/bin usr/lib && cp *.deb /out
