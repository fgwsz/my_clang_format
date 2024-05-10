# my_clang_format
## 安装vscode clang-format插件
可以在插件商店中搜索Clang-Format 并点击安装，或直接通过命令行进行安装（例如当我们要实现流程自动化时）：
```shell
code --install-extension xaver.clang-format
```
安装完成后配置设置选项卡
```
C_CPP:Formatting:clangFormat
Editor:DefaultFormatter:Clang-Format
Editor:FormatOnSaveMode:file
Editor:FormatOnSave:true
```
以后每次修改完代码保存时，vscode 的 clang-format 插件会调用系统中的 clang-format（默认从 PATH 环境变量中查找，也可以单独指定路径）对代码进行格式化。
## clang-format 终端用例
```shell
# 在当前工作目录下生成谷歌编码规范标准文件
clang-format -style=google -dump-config > .clang-format
# 以LLVM代码风格格式化main.cpp, 结果输出到stdout
clang-format -style=LLVM main.cpp
# 以file中的代码风格格式化main.cpp, 结果直接写到main.cpp
clang-format -style=file -i main.cpp
# 当然也支持对指定行格式化，格式化main.cpp的第1，2行
clang-format -lines=1:2 main.cpp
```
## 根据这份文件进行配置的修改
## 一个在线网站
可以查看配置文件的效果：<https://clang-format-configurator.site/>
