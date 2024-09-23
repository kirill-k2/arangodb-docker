## ArangoDB docker builder

Build deb packages of ArangoDB for Ubuntu 24.04 using docker

See https://github.com/arangodb/arangodb

Written for version 3.12

### Build

env `BUILD_IMAGE` - base build image (default `ubuntu:noble`)

#### Build from Git

```shell
docker build . -t arangodb
```

#### Build from local sources

Get sources

```shell
git clone --single-branch --depth 1 https://github.com/arangodb/arangodb.git
cd arangodb
git submodule update --init
```

Build

```shell
docker build . -t arangodb -f Dockerfile-src
```

### Get DEB Packages

```shell
docker cp $(docker create --name tmp local/arangodb):/opt ./build/ && docker rm tmp
```

### Docs

- https://docs.arangodb.com/3.10/operations/installation/compiling/compile-on-debian/
- https://github.com/arangodb/arangodb/issues/20586#issuecomment-1924045115
- http://jsteemann.github.io/blog/2014/10/16/how-to-compile-arangodb-from-source/ 
- https://decovar.dev/blog/2021/09/23/cmake-cpack-package-deb-apt/
