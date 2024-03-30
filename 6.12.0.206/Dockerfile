FROM ijs01140/mono:6.12.0.200 AS build

RUN apt-get update && \
  apt-get install -y git autoconf libtool automake build-essential gettext cmake python3 curl libtool-bin
RUN cd /tmp && \
  git clone https://github.com/mono/mono.git -b mono-6.12.0.206 --depth 1  && \
  cd mono && \
  ./autogen.sh --prefix=/usr/local && \
  make -j$(nproc) && \
  make install && \
  hash -r

FROM debian:bookworm-slim

COPY --from=build /usr/local /usr/local/
