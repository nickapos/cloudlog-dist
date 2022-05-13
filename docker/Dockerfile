FROM debian:bullseye
MAINTAINER nickapos@oncrete.gr
EXPOSE 80
RUN apt-get update && apt-get -y upgrade && apt-get -y install php7.4 php7.4-curl php7.4-mysql php7.4-mbstring php7.4-xml git sudo
COPY clone-cloudlog /tmp/clone-cloudlog
RUN /tmp/clone-cloudlog
COPY set-ownership /tmp/set-ownership
RUN /tmp/set-ownership
COPY set-permissions /tmp/set-permissions
CMD /bin/bash