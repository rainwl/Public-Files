# Protocol Buffer

## Overview

## Usage

- clone the repo: https://github.com/protocolbuffers/protobuf
- or download the release: https://github.com/protocolbuffers/protobuf/releases
- use cmake to build the project
- new a C++ proj to use protocol buffer

**NOTICE**
```
I used Protocol Buffers v21.4 instead of the latest release.(protobuf-cpp-3.21.4.zip)
Because the latest release has some bug when using.
```

- turn `protobuf_BUILD_LIBPROTOC` on

<img src="https://pic4rain.oss-cn-beijing.aliyuncs.com/img/cmakeproto.png">

**NOTICE**
```
Here are some differences between different releases
```

<img src="https://pic4rain.oss-cn-beijing.aliyuncs.com/img/buildProto.png">

<img src="https://pic4rain.oss-cn-beijing.aliyuncs.com/img/another.png">

**NOTICE**
```
Add the protoc.exe file directory to PATH
```
<img src="https://pic4rain.oss-cn-beijing.aliyuncs.com/img/path.png">


##  Use Visual Studio Project For Test

- New a visual studio C++ console project to test.
- And create 2 files `include` and `lib`.
- The `include` file place the `src/google`
- And the `lib` file place the build lib in `Release`.
- Do not forget to fill the `Include directiories` and `Library Directories` with them.
- And place 2 lib files in `Linker\Input\Additional Dependencies`.
- This could be different between different release.


![](https://pic4rain.oss-cn-beijing.aliyuncs.com/img/inclue%20lib.png)

![](https://pic4rain.oss-cn-beijing.aliyuncs.com/img/from%20here.png)

![](https://pic4rain.oss-cn-beijing.aliyuncs.com/img/from%20here%20google.png)

![](https://pic4rain.oss-cn-beijing.aliyuncs.com/img/property.png)

![](https://pic4rain.oss-cn-beijing.aliyuncs.com/img/lib.png)

**Write a test proto file**

![](https://pic4rain.oss-cn-beijing.aliyuncs.com/img/protocontent.png)

**Generate .cc and .h**
```
protoc --cpp_out=. myproto.proto
```

![](https://pic4rain.oss-cn-beijing.aliyuncs.com/img/protocmd.png)

**NOTICE**
```
If use the latest release,may use absl,place in include as well 
```

![](https://pic4rain.oss-cn-beijing.aliyuncs.com/img/absl.png)

**NOTICE**
in `myproto.pb.h`,add this code
```
#define PROTOBUF_USE_DLLS
```

![](https://pic4rain.oss-cn-beijing.aliyuncs.com/img/usedll.png)