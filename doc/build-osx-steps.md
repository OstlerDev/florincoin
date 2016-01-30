1) Install brew from brew.sh, this should prompt you to install "Developer Tools"

```
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

2) Using brew install git

```
$ brew install git
```

3) Install dependencies using brew

```
$ brew install autoconf automake libtool boost miniupnpc openssl pkg-config protobuf qt
```

4) Custom install Berkeley-db4, there was an issue with previous versions, so it needs to be installed without java.
```
$ brew install https://raw.github.com/mxcl/homebrew/master/Library/Formula/berkeley-db4.rb -–without-java
```
5) Once inside brew interactive mode, run the following commands
```
$ cd ..
$ db-4.8.30/dist/configure --prefix=/usr/local/Cellar/berkeley-db4/4.8.30
$ make
$ make install
$ exit
```
6) Link Berkley-db4
```
$ brew link --force berkeley-db4
```
7) If on OSX 10.11, reboot into recovery mode and launch terminal, run csrutil disable then if you got the message that security mode was disabled, reboot. Backup the old version of openssl that was installed with OSX
```
$ mv /usr/bin/openssl /usr/bin/openssl_OLD
```
9) Create a link to the version of OpenSSL installed using Brew, the version may change a bit so pay attention to what version you installed.
```
$ ln -s /usr/local/Cellar/openssl/1.0.2e_1/bin/openssl /usr/bin/openssl
```
10) Run openssl version to check the current version of OpenSSL that is installed, I recieved OpenSSL 1.0.2e 3 Dec 2015, if yours is the same or newer, move on.
11) Clone florincoin
```
$ git clone https://github.com/florincoin-project/florincoin.git
$ cd florincoin
```
12) Build florincoin
```
$ ./autogen.sh
$ ./configure
$ make
```
13) Check to make sure you built correctly using make check

Assuming you recieved no errors and the build did not fail, you should be able to find florincoind inside florincoin/src/florincoind