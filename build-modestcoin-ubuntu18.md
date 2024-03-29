# Step by Step Guide to Build Modestcoin in Ubuntu 18.04                                                                                                                  

### Step 1: Install the prerequisite#

$ sudo apt-get update 

$ sudo apt-get install build-essential 

$ sudo apt-get install autoconf libtool pkg-config libboost-all-dev libssl-dev libprotobuf-dev protobuf-compiler libevent-dev libqt4-dev libcanberra-gtk-module libdb++-dev

(for ubuntu 19 and higher replace libqt4-dev with qt5*-dev in the above command)

### Step 2: Install BerkeleyDB using the below commands (If not already Installed)#
*Follow this link for Debian: https://github.com/bitcoin/bitcoin/blob/master/doc/build-unix.md#berkeley-db*


$ wget http://download.oracle.com/berkeley-db/db-4.8.30.NC.tar.gz    

$ tar -xvf db-4.8.30.NC.tar.gz                                                                                                                                         

$ cd db-4.8.30.NC/build_unix                                                                                                                                           

$ mkdir -p build                                                                                                                                                       

$ BDB_PREFIX=$(pwd)/build                                                                                                                                             

$ ../dist/configure --disable-shared --enable-cxx --with-pic --prefix=$BDB_PREFIX  

$ sudo make install 


For Certian Debian Users Only:
(./configure \
    BDB_LIBS="-L${BDB_PREFIX}/lib -ldb_cxx-4.8" \
    BDB_CFLAGS="-I${BDB_PREFIX}/include")


### Step 3: Build the Coin#

$ git clone https://github.com/modestcoin/modestcoin.git

$ cd modestcoin

$ ./autogen.sh                                                                                                                                                         

$ ./configure CPPFLAGS="-I${BDB_PREFIX}/include/ -O2" LDFLAGS="-L${BDB_PREFIX}/lib/"                                                                                   

$ sudo make install                                                                                                                                                   

$ cd ~                                                                                                                                                                 

$ cd modestcoin/src                                                                                                                                                   

$ ./modestcoind                                                                                                                                                       

$ ./modestcoin-cli getnewaddress                                                                                                                                      


## *Thanks for everyones support in the community, we hope you love modestcoin as much as we do <3
## any developmental support is very much welcome, and appreciated <3
