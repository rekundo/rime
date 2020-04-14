> Building and installing ibus-rime.

# Packages for Linux Distributions

## Archlinux

    pacman -S ibus-rime

## Debian

Rime 已收錄於 [Debian Jessie](https://wiki.debian.org/DebianJessie) 及以上版本

    sudo apt-get install ibus-rime # or fcitx-rime

## Gentoo

    emerge ibus-rime  # or fcitx-rime

## Ubuntu

Rime 已收錄於 [Ubuntu 12.10 (Quantal Quetzal)](http://old-releases.ubuntu.com/releases/12.10/) 及以上版本

    sudo apt-get install ibus-rime

    ibus engine rime

安裝更多輸入方案：（推薦使用 [/plum/](https://github.com/rime/plum) 安裝最新版本）

    # 朙月拼音（預裝）
    sudo apt-get install librime-data-luna-pinyin
    # 雙拼
    sudo apt-get install librime-data-double-pinyin
    # 宮保拼音
    sudo apt-get install librime-data-combo-pinyin
    # 注音、地球拼音
    sudo apt-get install librime-data-terra-pinyin librime-data-bopomofo
    # 倉頡五代（預裝）
    sudo apt-get install librime-data-cangjie5
    # 速成五代
    sudo apt-get install librime-data-quick5
    # 五筆86、袖珍簡化字拼音、五筆畫
    sudo apt-get install librime-data-wubi librime-data-pinyin-simp librime-data-stroke-simp
    # IPA (X-SAMPA)
    sudo apt-get install librime-data-ipa-xsampa
    # 上海吳語
    sudo apt-get install librime-data-wugniu
    # 粵拼
    sudo apt-get install librime-data-jyutping
    # 中古漢語拼音
    sudo apt-get install librime-data-zyenpheng

## Ubuntu PPA

for Ubuntu 12.04 and higher

    # this repo provides libkyotocabinet, libgoogle-glog for Ubuntu 12.04;
    # these packages are officially supported since Ubuntu 12.10.
    sudo add-apt-repository ppa:fcitx-team/nightly

    # providing libyaml-cpp0.5, librime, rime-data, ibus-rime
    sudo add-apt-repository ppa:lotem/rime

    sudo apt-get update
    sudo apt-get install ibus-rime

Ubuntu 12.04 以下版本，參考下文的安裝手記。

## Fedora 22+

    sudo dnf install ibus-rime

## Fedora 18/19

    sudo yum install ibus-rime

## Fedora 17

轉自 http://hi.baidu.com/swordswift/item/68e8584728dc900cc1161393

swordswift: 因为fedora下没有打包好的安装包，所以我就做了一个安装源，也算是对作者的支持和感谢吧。

安装办法:

    cd /etc/yum.repos.d/
    sudo wget http://heimu-packages.stor.sinaapp.com/fedora/heimu.repo
    sudo yum install ibus-rime

有手藝、有時間、熱心腸的Linux技術高手！ 請幫我把Rime打包到你喜愛的Linux發行版，分享給其他同學吧。

謝謝你們！

# Manual Installation

## Prerequisites

To build la rime, you need these tools and libraries:
  * cmake
  * boost >= 1.46
  * glog (for librime>=0.9.3)
  * gtest (optional, recommended for developers)
  * libibus-1.0
  * libnotify (for ibus-rime>=0.9.2)
  * kyotocabinet (for librime<=1.2)
  * leveldb (for librime>=1.3, replacing kyotocabinet)
  * libmarisa (for librime>=1.2)
  * opencc 0.x
  * yaml-cpp >= 0.5

Note: If your compiler doesn't fully support C++11, please checkout `oldschool` branch from https://github.com/rime/librime/tree/oldschool

## Build and install ibus-rime

clone project and submodules:

    git clone --recursive https://github.com/rime/ibus-rime.git
    cd ibus-rime
    # do this as normal user
    ./install.sh

## Configure IBus

  * restart IBus
  * add "Rime" to the input method list in IBus Preferences

Voilà !

## ibus-rime on Ubuntu 12.04 安裝手記

註：這篇文章過時了。Ubuntu 12.04 可直接使用上文給出的 PPA 安裝最新版本。

今天天氣不錯，我更新了一把Ubuntu，記錄下安裝 ibus-rime 的步驟。

    # 安裝編譯工具
    sudo apt-get install build-essential cmake

    # 安裝程序庫
    sudo apt-get install libopencc-dev libz-dev libibus-1.0-dev libnotify-dev

    sudo apt-get install libboost-dev libboost-filesystem-dev libboost-regex-dev libboost-signals-dev libboost-system-dev libboost-thread-dev
    # 如果不嫌多，也可以安裝整套Boost開發包（敲字少：）
    # sudo apt-get install libboost-all-dev


    mkdir ~/rimeime
    cd ~/rimeime

    wget http://google-glog.googlecode.com/files/glog-0.3.2.tar.gz
    tar xzf glog-0.3.2.tar.gz
    cd glog-0.3.2
    ./configure
    make
    sudo make install

    cd ~/rimeime

    wget http://fallabs.com/kyotocabinet/pkg/kyotocabinet-1.2.76.tar.gz
    tar xzf kyotocabinet-1.2.76.tar.gz
    cd kyotocabinet-1.2.76
    ./configure
    make
    sudo make install

    cd ~/rimeime

    wget http://yaml-cpp.googlecode.com/files/yaml-cpp-0.3.0.tar.gz
    tar xzf yaml-cpp-0.3.0.tar.gz
    cd yaml-cpp
    mkdir build
    cd build
    cmake -DBUILD_SHARED_LIBS=ON ..
    make
    sudo make install


    sudo ldconfig


    cd ~/rimeime

    wget http://rimeime.googlecode.com/files/brise-0.13.tar.gz
    wget http://rimeime.googlecode.com/files/librime-0.9.4.tar.gz
    wget http://rimeime.googlecode.com/files/ibus-rime-0.9.4.tar.gz
    tar xzf brise-0.13.tar.gz
    tar xzf librime-0.9.4.tar.gz
    tar xzf ibus-rime-0.9.4.tar.gz
    cd ibus-rime
    ./install.sh


## ibus-rime on Centos 7
```
yum install -y gcc gcc-c++ boost boost-devel cmake make cmake3
yum install glog glog-devel kyotocabinet kyotocabinet-devel marisa-devel yaml-cpp yaml-cpp-devel gtest gtest-devel libnotify zlib zlib-devel gflags gflags-devel leveldb leveldb-devel libnotify-devel ibus-devel
cd /usr/src

# install opencc
curl -L https://github.com/BYVoid/OpenCC/archive/ver.1.0.5.tar.gz | tar zx
cd OpenCC-ver.1.0.5/
make
make install
ln -s /usr/lib/libopencc.so /usr/lib64/libopencc.so

cd /usr/src
git clone --recursive https://github.com/rime/ibus-rime.git

cd /usr/src/ibus-rime
./install.sh

# checkout master & pull
cd /usr/src/ibus-rime/plum/
git checkout master
git pull origin master

cd /usr/src/ibus-rime
# skip submodule init
sed -i 's/git submodule update --init/#git submodule update --init/g' ./install.sh
./install.sh
```