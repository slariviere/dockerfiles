FROM ubuntu:19.10
RUN apt-get update
RUN apt-get install -y curl patch unzip m4 gcc make
WORKDIR /tmp
RUN curl https://raw.githubusercontent.com/ocaml/opam/master/shell/install.sh -o install.sh
RUN chmod +x install.sh
RUN echo | ./install.sh
RUN groupadd -r opam -g 1000 && useradd -u 1000 -r -g opam -m -d /app -s /sbin/nologin -c "opam user" opam
RUN chmod 755 /app
USER opam
WORKDIR /app
RUN opam init --disable-sandboxing --compiler=4.08.0 -y
RUN opam update
RUN echo 'eval `opam env`' >> /app/.bashrc
