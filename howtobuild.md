Step by Step Guide to Build Modestcoin in Ubuntu 18.04                                                                                                                  

*Step 1: Install the prerequisite

sudo apt-get update  
sudo apt-get install build-essential
sudo apt-get install autoconf libtool pkg-config libboost-all-dev libssl-dev libprotobuf-dev protobuf-compiler libevent-dev libqt4-dev libcanberra-gtk-module libdb++-dev


*Step 2: Install BerkeleyDB using the below commands (If not already Installed)

wget http://download.oracle.com/berkeley-db/db-4.8.30.NC.tar.gz
tar -xvf db-4.8.30.NC.tar.gz
cd db-4.8.30.NC/build_unix
mkdir -p build
BDB_PREFIX=$(pwd)/build
../dist/configure --disable-shared --enable-cxx --with-pic --prefix=$BDB_PREFIX
sudo make install

*Step 3: Build the Coin

./autogen.sh
./configure CPPFLAGS="-I${BDB_PREFIX}/include/ -O2" LDFLAGS="-L${BDB_PREFIX}/lib/"
make                                                                                                                                                                   
sudo make install                                                                                                                                                    
cd ~                                                                                                                                                                  
cd modestcoin/src                                                                                                                                                    
./modestcoind                                                                                                                                                         
./modestcoin-cli getnewaddress                                                                                                                                        

Thanks for everyones support in the community, i hope you love modestcoin as much as i do <3
any developmental support is very much welcome, and appreciated <3

If someone should get the .EXE file generated and publish it online, i will support it, and add
its url to the main page, and website <3 *pay in modestcoin <3
