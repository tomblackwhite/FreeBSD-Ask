# 第七节 Python 与 VScode

在这一节，我们将假设你已经成功设置好 `pkg` 工具。如果你还没有，请参考本书 **第三章第四节** 以进行设置。

## Python

在 FreeBSD 中，不同的 Python 版本被分开包装。意思是说，Python3.8 和 Python3.11 属于不同的包。就好像 `llvm11` 和 `llvm13` 那样。

但是，就目前的 FreeBSD 13 来说，支持最完整的 Python 是 Python 3.8。`pip` 与 `numpy` 之类的工具只有针对 `py38` 的打包。这也就是 `python3` 这个虚包指向的是 `python38` 的原因。

所以想要安装Python，你需要这样做：

```
# pkg install python38 py38-pip
```

显式要求 `python38` 的原因是为了防止 `python3` 指向的那个Python未来发生变化以后，`pip` 却没有跟着进入新版本之类的事情发生。

当然你也可以通过：

```
# pkg install python311
```

之类的命令来要求一个更新的 Python 版本。但是请记住，最新版本的 Python 版本在 FreeBSD 上可能没有那么完全。

然而不管怎么说，这总好过某些 Linux 发行版，从来只维护一个 Python 版本，也不管这么做的后果是什么。（是的，我就是在说你，Arch Linux）

## VS Code

在以前，FreeBSD 用户想要安装 VS Code 手动从 GitHub 上下载源码，自己配置 Electron 的编译环境，然后自己编译 VS Code。或者通过利用 Linux 兼容层的方式来直接运行 VS Code 的 RPM 包。

但是自从 VS Code 进入 ports tree，进而进入 pkg repo 以后，用户可以不用那么折腾了。直接：

```
# pkg install vscode
```

然后你就能写代码了。

需要注意的是，通过这种方式获取到的 VS Code 其实是 Code - OSS。Code - OSS 和 VS Code 的区别将不在这里展开陈述，有兴趣的人可以自己 [做做功课](https://github.com/microsoft/vscode/wiki/Differences-between-the-repository-and-Visual-Studio-Code)。

这里只想提一下，目前已知微软的 Python/PyLance 插件，以及 LLVM 的 clangd 插件都能直接在 Code - OSS 运行，使用起来和 VS Code 没有任何区别。

微软的 Remote Development 在 Code - OSS 也没有任何问题。

设置同步服务看起来是不能用的。
