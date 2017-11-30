FROM ubuntu:xenial

ADD sources.list /etc/apt/sources.list
RUN apt-get update && apt-get upgrade -y && apt-get install -y build-essential checkinstall wget ruby-dev && apt-get build-dep imagemagick -y
RUN wget https://www.imagemagick.org/download/releases/ImageMagick-7.0.7-12.tar.xz
RUN gem install fpm
RUN mkdir /out
RUN tar -xvJf ImageMagick-7.0.7-12.tar.xz
RUN ln -s $(find ImageMagick-* -type d | head -n 1) /imagemagick
WORKDIR /imagemagick
RUN ./configure
RUN make clean
RUN make
RUN mkdir /tmp/out
RUN make install DESTDIR=/tmp/out

CMD fpm -s dir -t deb -n imagemagick -v 7.0.7-12-xenial-pace -C /tmp/out -p imagemagick_VERSION_ARCH.deb \
    -d "libdjvulibre-dev (>=0)" \
    -d "libwmf-dev (>=0)" \
    -d "libopenexr-dev (>=0)" \
    -d "libpango1.0-dev (>=0)" \
    -d "libc6 (>=0)" \
    -d "libmagickcore5 (>=0)" \
    -d "libmagickwand5 (>=0)" \
    -d "hicolor-icon-theme (>=0)" \
    --deb-shlibs \
    usr/local && cp *.deb /out
