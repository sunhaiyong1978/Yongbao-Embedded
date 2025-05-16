# “勇豹”嵌入式版(Yongbao-Embedded)发行版构建项目 使用说明

## 简介：

“勇豹”嵌入式版(Yongbao-Embedded)是一个使用交叉编译的方式构建目标指令集架构操作系统发行版的项目。

以下“勇豹”嵌入式版及“Yongbao-Embedded”均指代该项目。

“勇豹”嵌入式版旨在用来为目标指令集架构提供一个全新可使用的操作系统，亦可用来帮助用户编译、验证在目标系统上运行的程序。

目前“勇豹”嵌入式版支持构建的操作系统为Linux，支持的目标指令集架构：LoongArch32。

## 获取方式：

“勇豹”嵌入式版项目可以通过git命令进行获取，使用以下命令获取最新的版本：

```sh
git clone https://github.com/sunhaiyong1978/Yongbao-Embedded.git --depth 1
```


## 准备运行环境

运行“勇豹”嵌入式版的构建代码需要提供基本的开发环境：

### Fedora系统：

```sh
sudo dnf install @c-development gawk gettext vim wget autoconf texinfo file flex bison \
		rsync pkg-config cmake ninja tcl gperf patch openssl icu \
		zlib-devel python3-devel libunistring-devel libffi-devel gc-devel libicu-devel glib2-devel gettext-devel \
		glibc-static glib2-static zlib-static \
		expat-devel perl-open perl-FindBin
```

### Ubuntu系统：

```sh
sudo apt-get install build-essential gawk gettext vim wget autoconf texinfo file flex bison \
		rsync pkg-config cmake ninja-build autopoint tcl gperf \
		zlib1g-dev python3-dev libunistring-dev libffi-dev libgc-dev libicu-dev libglib2.0-dev
```

## 基本使用方式：

当获取了“勇豹”嵌入式版的代码和准备好运行环境后，即可以开始进行构建发行版的工作了。

获取“勇豹”嵌入式版的代码后在Yongbao目录中运行构建命令：

```sh
pushd loongarch32
	./build.sh
popd
```

该命令会进行目标指令集架构操作系统的构建，在构建前会对构建过程中所需的源码包和资源文件进行下载，请保持网络环境的畅通。

可以通过 -h 参数获取build.sh命令的基本用法说明。

因构建过程取决于构建机器的性能，因此不同机器的构建时间差异可能巨大，请耐心等待构建过程完成。

