FROM centos:7.3.1611

# - Move default shell from sh to bash
# - Update all packages
# - Install required packages
RUN rm /bin/sh \
	&& ln -s /bin/bash /bin/sh \
	&& yum update -y \
	&& yum install -y \
	gcc \
	zlib-devel \
	bzip2-devel \
	openssl-devel \
	ncurses-devel \
	sqlite-devel \
	readline-devel \
	tk-devel \
	gdbm-devel \
	db4-devel \
	libpcap-devel \
	libffi-devel \
	xz-devel \
	expat-devel \
	numactl \
	wget \
	git \
	make

# Install SQLite
RUN cd /usr/src \
	&& wget http://www.sqlite.org/2019/sqlite-autoconf-3290000.tar.gz \
	&& tar xvfz sqlite-autoconf-3290000.tar.gz \
	&& cd sqlite-autoconf-3290000 \
	&& ./configure \
	&& make \
	&& make install

# Install python
RUN cd /usr/src \
	&& wget https://www.python.org/ftp/python/3.7.4/Python-3.7.4.tar.xz \
	&& tar xf Python-3.7.4.tar.xz \
	&& cd Python-3.7.4 \
	&& ./configure \
	--enable-optimizations \
	--enable-loadable-sqlite-extensions \
	&& make \
	&& make altinstall

RUN ln -s /usr/local/bin/python3.7 /usr/bin/python3.7 \
	&& ln -s /usr/local/bin/pip3.7 /usr/bin/pip3.7
