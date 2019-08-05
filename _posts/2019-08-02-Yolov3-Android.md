---
title: 安卓移植YOLOv3
published: true
category: work
tag: YOLO
---

## 编译项目

有三种方式：

1. 基于Make的ndk-build

2. CMake

3. 独立工具链，用于与其他编译系统集成，或与configure的项目搭配使用

## CMake

CMake是一个跨平台的安装（编译）工具，可以用简单的语句来描述所有平台的安装(编译过程)。他能够输出各种各样的makefile或者project文件，能测试编译器所支持的C++特性,类似UNIX下的automake。只是 CMake 的组态档取名为 CMakeLists.txt。Cmake 并不直接建构出最终的软件，而是产生标准的建构档（如 Unix 的 Makefile 或 Windows Visual C++ 的 projects/workspaces），然后再依一般的建构方式使用。

##

```
defaultConfig {
      externalNativeBuild {
            cmake {
                cFlags "-std=c99  -DOMP_NUM_THREADS=8"
                cppFlags "-std=c++11 -frtti -fexceptions"
            }
        }
}
buildTypes {
    release {
        minifyEnabled false
        proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
        signingConfig signingConfigs.chenty
    }
    debug {
        debuggable false
        minifyEnabled false
    }
}
externalNativeBuild {
    cmake {
        path "CMakeLists.txt"
    }
}
```
