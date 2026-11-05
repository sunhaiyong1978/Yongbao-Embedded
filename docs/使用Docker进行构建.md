## 使用 Docker 进行构建

1、下载构建所需的源码包

```sh
DOCKER_BUILDKIT=1 docker buildx build -f docker/Dockerfile.download --target download_packages-out --output type=local,dest=./download_packages-cache .
```

上面的Docker命令将创建一个 download_packages-out 目录，该目录存放了构建系统所需要的全部源码包。

在构建系统前首先完成下载源码包可减少构建过程中的下载需求。

2、构建 loongarch 系统

修改 /etc/docker/json 文件以支持构建，增加以下内容：
```sh
{
  "builder": {
    "entitlements": {
      "security-insecure": true
    }
  }
}
```

运行构建

构建 loongarch32s 的sysroot，使用如下命令：
```sh
DOCKER_BUILDKIT=1 docker buildx build --builder insecure-builder --allow security.insecure \
	-f docker/Dockerfile.sysroot --build-arg ARCH=loongarch32 --target sysroot-builder \
	--output type=local,dest=./linux_sysroot_loongarch32-cache .
```

构建 loongarch32r 的sysroot，使用如下命令：
```sh
DOCKER_BUILDKIT=1 docker buildx build --builder insecure-builder --allow security.insecure \
	-f docker/Dockerfile.sysroot --build-arg ARCH=loongarch32r --target sysroot-builder \
	--output type=local,dest=./linux_sysroot_loongarch32r-cache .
```


