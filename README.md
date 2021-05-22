##  GooglePinYinIMEDict

### 项目介绍

- 项目简介

    基于谷歌拼音输入法词库生成工具优化的输入法词库生成工具及常见词库整理。

- 目录结构

    ```
    ├── CMakeLists.txt： C++编译配置
    │
    ├── command：词库生成工具源码
    │
    ├── data：词库原始数据
    │   │
    │   ├── rawdict_utf16_65105_freq.txt：中文日常词库
    │   │
    │   └── valid_utf16.txt：词库文字库
    │   
    ├── dict：生成词库
    │   │
    │   └── dict_pinyin.dat：基于 rawdict_utf16_65105_freq.txt 生成的词库
    │   
    ├── include：词库源码
    │
    └── share：词库源码
    ```

### 使用方式

- 环境准备

    ```
    ➜  GooglePinYinIMEDict git:(master) ✗ cmake --version
    cmake version 3.19.1

    CMake suite maintained and supported by Kitware (kitware.com/cmake).
    ```

- 编译工具


    ```
    ➜  GooglePinYinIMEDict git:(master) ✗ rm -fr CMakeCache.txt CMakeFiles/ PinYinImeDicBuilder Makefile cmake_install.cmake libjni_pinyinime.dylib
    ➜  GooglePinYinIMEDict git:(master) ✗  cmake -DCMAKE_INSTALL_PREFIX=/usr
    CMake Warning:
    No source or binary directory provided.  Both will be assumed to be the
    same as the current working directory, but note that this warning will
    become a fatal error in future CMake releases.

    ……

    ➜  GooglePinYinIMEDict git:(master) ✗ make
    Scanning dependencies of target PinYinImeDicBuilder
    [  5%] Building CXX object CMakeFiles/PinYinImeDicBuilder.dir/command/pinyinime_dictbuilder.cpp.o
    [ 11%] Building CXX object CMakeFiles/PinYinImeDicBuilder.dir/share/dictbuilder.cpp.o

    ……

    [100%] Linking CXX executable PinYinImeDicBuilder
    [100%] Built target PinYinImeDicBuilder
    ```

- 生成词库

    ```
    ➜  GooglePinYinIMEDict git:(master) ✗ ./PinYinImeDicBuilder
    (null) 23232
    read succesfully, lemma num: 84049
    最大词频:4828294.500000 总词频：97179190.884383 平均词频：1156.220668
    ------------Spelling Possiblities--------------

    ……

    start_pos_[kMaxLemmaSize]:172440
    保存词库
    lma_node_num_le0_:417
    lma_node_num_ge1_:57247
    lma_idx_buf_len_:252177
    top_lmas_num_:10
    [1]    15427 segmentation fault  ./PinYinImeDicBuilder
    ```
