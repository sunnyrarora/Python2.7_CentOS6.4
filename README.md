# Python2.7_CentOS6.4
# Standard way to Install Python 2.7 on CentOS 6.4 
yum install gcc openssl-devel bzip2-devel libffi-devel python-devel -y
yum groupinstall development
cd /usr/src
wget https://www.python.org/ftp/python/2.7.10/Python-2.7.10.tgz
tar xzf Python-2.7.10.tgz
cd Python-2.7.10
vi Modules/Setup.dist
   Uncomment: _ssl _ssl.c \
   -DUSE_SSL -I$(SSL)/include -I$(SSL)/include/openssl \
    -L$(SSL)/lib -lssl -lcrypto

./configure --prefix=/usr/local --enable-unicode=ucs2 --enable-shared       LDFLAGS="-Wl,-rpath /usr/local/lib"
make && make altinstall
cp /usr/lib64/python2.6/lib-dynload/bz2.so /usr/local/lib/python2.7/

cd /opt
	wget https://bootstrap.pypa.io/ez_setup.py -O - | python2.7   #install the setup tools.
	/usr/local/bin/easy_install --version    # check this easy_install version, this should be related to python2.7
	/usr/local/bin/easy_install pip     #install pip2.7  for python2.7
	pip2.7 install --upgrade pip
	pip2.7 install --upgrade virtualenv    #upgrade the virtualenv which is related to python2.7
    
