FROM ubuntu:16.04
RUN apt-get clean && apt-get update && apt-get install -y locales tzdata
RUN locale-gen en_US.UTF-8
RUN locale-gen ru_RU.UTF-8
RUN update-locale
ENV LC_ALL ru_RU.UTF-8
RUN mkdir /usr/src/app
RUN ln -fs /usr/share/zoneinfo/Europe/Moscow /etc/localtime && dpkg-reconfigure -f noninteractive tzdata
WORKDIR /usrc/src/app
RUN apt-get update \
  && apt-get install -y build-essential libpam0g-dev apt-utils wkhtmltopdf \
  && apt-get install -y libpq-dev libmysqlclient-dev cpanminus \
  && apt-get autoremove -y \
  && rm -r /var/cache/apt/archives/* \
  && rm -r /var/lib/apt/*
# RUN cpanm Devel::Cycle Text::CSV App::mojopaste Mojo::mysql Mojo::SQLite
# For todo
RUN cpanm Devel::Cycle Text::CSV App::mojopaste
ENV PASTE_DIR /usr/src/app/data
ENV MOJO_CONFIG /usr/src/app/mojopaste.conf
