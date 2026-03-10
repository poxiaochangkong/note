# cmake笔记

## cmake简介

[video url](https://www.bilibili.com/video/BV14s4y1g7Zj/?spm_id_from=333.337.search-card.all.click&vd_source=57ff078d1abdc46b59d1ef743bdfcda1)

cmake功能:跨平台生成Makefile



```
cmake构建流程:
(linux)
项目->CMakeLists.txt->cmake->Makefile
(windows)
项目->CMakeLists.txt->cmake->.sln,.vcxproj等文件
```

## cmake使用

### 注释

- \#进行行注释
```
# 这是一个注释
```

- \#[[]]进行块注释
```
#[[

这是一个块注释
]]
```

### cmake命令

- cmake_minimum_required(VERSION 3.10) # 指定cmake的最低版本要求   

+ project：定义工程名称，并可指定工程的版本、工程描述、web主页地址、支持的语言（默认情况支持所有语言）

```
project(<PROJECT-NAME>
       [VERSION <major>[.<minor>[.<patch>[.<tweak>]]]]
       [DESCRIPTION <project-description-string>]
       [HOMEPAGE_URL <url-string>]
       [LANGUAGES <language-name>...])

```

* add_executable：添加可执行文件
```
add_executable(可执行程序名 源文件名称)
#源文件需要全部列出，可以使用相对路径
```

- cmake命令
```
cmake dir #CMakeLists.txt所在目录
cmake会在当前执行的目录下生成构建文件，建议在构建目录执行cmake命令

make #根据cmake生成的makefile编译，在构建目录执行，或者说，在makefile所在的目录执行
懒人命令 cmake --build . #在构建目录执行，或者说，在makefile所在的目录执行，无论windows还是linux都适用
```



#### set
+ set设置变量,$调用变量
```
set(VAR [VALUE]) .e.g:set(SRC main.cpp src/value.cpp)
add_executable(app ${SRC})
```

* set设置C++标准
```
set(CMAKE_CXX_STANDARD 17) #设置C++标准17,CMAKE_CXX_STANDARD是内置的变量
```

- set设置输出目录
```
set(EXECUTABLE_OUTPUT_PATH  VALUE)#EXECUTABLE_OUTPUT_PATH是内置的变量
```

#### 文件搜索

1. aux_source_directory命令
```
aux_source_directory(DIRECTORY VAR) #会在DIRECTORY下搜索源文件并赋值给VAR
```

2. file命令
```

```


## cmake遇到的问题
**vscode的cmake tools如果指定了编译器/kit，将会自动注入kit自带的vcpkg，忽略环境变量vcpkg或者settings.json的toolchian,可以通过选择未指定,让settings.json的toolchain生效,或者按照官方文档设置对应的一个.json文件避免问题**