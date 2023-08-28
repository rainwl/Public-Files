# iMSTK-unity

## Setup for develoment

从GitLab检出iMSTK-Unity时，首先需要构建iMSTK。iMSTK使用CMake作为其构建系统。iMSTK是一个超级构建，意味着它会构建、包含并链接到所有依赖项，无需手动查找它们。正确版本的iMSTK作为git子模块包含在存储库中，位于iMSTKSource~目录下。在更新存储库后，要确保它是最新的，请运行git submodule update。要构建iMSTK，您需要使用cmake。在构建时，请确保构建目录（二进制文件存放的位置）不在iMSTKSource~目录内，而是靠近您的驱动器根目录，例如C:imstk-build。iMSTK的项目结构足够深，以至于Windows路径长度会导致问题。此外，打开IMSTK_BUILD_FOR_UNITY cmake开关，这将减少正在构建的依赖项数量。它还将在安装目录中生成“.cs”文件以及“.dll”/“.so”文件，这些文件是“.cs”代码所需的，将在Unity中使用。根据需要，还可以启用iMSTK_USE_VRPN和/或iMSTK_USE_OpenHaptics以支持设备。

有两种不同的方法可以安装二进制文件，对于这两种方法，您需要知道安装了iMSTK的目录。如果您没有进行任何更改，该目录将被称为install，并位于您在cmake中定义用于构建imstk的目录内，例如C:\Projects\imstk\build\install：

或者您可以在Unity中为iMSTK启用开发者模式。此选项可以在“编辑->项目设置->iMSTK设置”中找到。启用后，每次启动Unity时都会提示您安装iMSTK。在启用此选项后，您可能需要重新启动Unity。当它提示您时，选择“是”并提供iMSTK的安装目录，位于 `<iMSTK构建目录>/install`。所有必要的文件都将被复制。如果您不想被要求重新安装iMSTK，请将此选项切换为关闭状态。

