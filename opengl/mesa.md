# opengl(mesa) for ubuntu14.04

關於 mesa
mesa是一個開源的OpenGL的實現。它被廣泛用於包括X-Windows在內的各種渲染系統中。 具體見官網：http://www.mesa3d.org/intro.html
       ftp://ftp.freedesktop.org/pub/mesa/
現在，我們將在Ubuntu 14.04上編譯並安裝最新版mesa。

##安裝 LLVM/Clang 3.3
LLVM/Clang是構架編譯器(compiler)的框架系統，以C++編寫而成，用於優化以任意程序語言編寫的程序的編譯時間(compile-time)、鏈接時間(link-time)、運行時間(run-time)以及空閒時間(idle-time)，它是編譯mesa的依賴之一。目前，LLVM/Clang的最新版為3.4，在Ubuntu 14.04上，我們可以直接使用 sudo apt-get install llvm來安裝最新版LLVM/Clang。但是，由於LLVM 3.4的一些bug會對之後的工作造成一定的麻煩，這裡，我們自行編譯、安裝較為穩定的LLVM 3.3。
具體的，首先，我們從http://www.llvm.org/releases/上下載LLVM 3.3 和 Clang 3.3的源代碼。源代碼下載完成後，進行解壓縮，然後將Clang 3.3的源代碼目錄命名為clang，並移動到llvm源代碼目錄下的tools目錄下。具體的目錄關係應如下所示：

```sh
<llvmsrc>
    tools
        clang
```

接下來我們使用configure來配置生成llvm的Makefile文件，然後就可以進行編譯與安裝。注意，這裡llvm之後要被mesa所link，所以在配置是應開啟--enable-shared選項。


```sh
cd llvm-3.3.src
./configure --enable-shared=yes --prefix=/usr/local/llvm-3.3
make
sudo make install
```
```sh
export PATH=/usr/local/llvm-3.3/bin:$PATH
```

##安裝 libdrm-2.4.65
最新版的mesa的編譯需要高於2.4.65的libdrm_radeon庫，我們使用與上文介紹的相同的方法來編譯和安裝。
首先，從http://dri.freedesktop.org/libdrm/下載libdrm 2.4.65的源代碼，解壓縮後，運行如下命令。

```sh
cd libdrm-2.4.65
./configure   --prefix=/usr/local/libdrm-2.4.65
make
sudo make install
```
- ~/.bashrc

```sh
PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/libdrm-2.4.65/lib/pkgconfig
export PKG_CONFIG_PATH

```


##安裝其他依賴包
mesa的編譯還需要其他依賴包，如果這些包缺失，mesa的配置將會失敗，我們可以從configure的錯誤信息中得出缺失的包的名字，然後自行安裝，以下羅列了安裝一些可能缺失的包的命令（Ubuntu下）。

```sh
sudo apt-get install x11proto-gl-dev
sudo apt-get install  x11proto-dri2-dev
sudo apt-get install  x11proto-dri3-dev
sudo apt-get install  x11proto-present-dev
sudo apt-get install libxdamage-dev
sudo apt-get install libxext-dev
sudo apt-get install libx11-xcb-dev
sudo apt-get install libxcb-glx0-dev
sudo apt-get install libxcb-dri2-0-dev
sudo apt-get install libxcb-dri3-dev
sudo apt-get install libxcb-present-dev
sudo apt-get install libxshmfence-dev
sudo apt-get install libudev-dev
sudo apt-get install autoreconf
sudo apt-get install libtool
sudo apt-get install expat
sudo apt-get install libexpat1-dev
```
##獲取mesa的最新源代碼
我們使用git（git可以使用sudo apt-get install git來安裝）來獲取mesa的最新源代碼。之後就可以進行配置，編譯與安裝。 需要注意的是，git master branch所獲得的源代碼中並不包含生成好的configure文件，作為替代，我們運行autogen.sh命令來生成和運行configure，因此configure的配置選項也應該加入到autogen.sh命令後。 
```sh
git clone git://anongit.freedesktop.org/git/mesa/mesa
cd mesa
./autogen.sh --enable-gbm --enable-glx-tls
make
sudo make install
```
至此mesa的編譯與安裝就成功了，在mesa目錄下，我們可以使用git pull origin命令來獲得最新版的mesa代碼，並編譯和安裝。


