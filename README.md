# Qt CMake With CLion Boilerplate

A simple empty boilerplate project to make Qt desktop GUI program by CMake which is compatible to CLion.

适用于 CLion 的一个空白 Qt CMake GUI 程序模板。

## Initialization 初始化

1. I assume you have installed Qt newest stable sdk and made it as default tool chain.

   假设你已经安装好了 Qt SDK 最新稳定版，并设置成了默认工具链。

2. Create environment variable `CMAKE_PREFIX_PATH`

   创建环境变量，参考路径 example value: `C:\Qt\Qt5.14.2\5.14.2\mingw73_64`

3. Git clone this project, open in CLion or Qt Creator at your pleasure.

   克隆项目，选择喜欢的 IDE 打开。

## Enable Run on Windows 调试运行

1. 追加路径环境变量 Append path environment variable 

   `PATH+=C:\Qt\Qt5.14.2\Tools\mingw730_64\bin;C:\Qt\Qt5.14.2\5.14.2\mingw73_64\bin`

2. File | Settings | Tools | External Tools, add new external tool called `WinDeployQt`

   打开设置，添加新的工具

3. Following:

   | Tool Settings | Value                       |
   | ------------- | --------------------------- |
   | Program       | `windeployqt.exe`           |
   | Arguments     | `$CMakeCurrentProductFile$` |

4. Run | Edit Configurations... > Before Launch

   click "+" 添加启动前配置，select: `Run External Tools` > `WinDeployQt`

## FAQ 疑难解答

### error in mainwindow.cpp ui 对应文件报错

`Ctrl` + `F9` or File | Reload CMake Profile

构建一下项目文件，或者刷新一下 CMake 

### 怎样发布我写好的小程序？ How to publish the deploy project on Windows?

1. File | Settings | Build, Execution, Deployment | CMake > Create Release Profile 创建发布配置

2. Switch to Release Profile, Run Build. 切换到发布模式并构建。

3. Copy necessary files including the main execution file ( <project\_\_root>/cmake-build-release/*) at least to the destination folder.

   把至少包含主文件在内的程序拷贝到目标文件夹

4. Execute `windeployqt <program_name>.exe` to copy necessary library files.

   执行命令拷贝所需要的库文件

   `windeployqt --help` 详细介绍，with `--no-*` parameter to reduce unnecessary files 设置参数以打包避免不需要的文件
