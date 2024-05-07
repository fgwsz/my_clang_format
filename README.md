﻿# my_clang_format
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
```yaml
 # 语言: None, Cpp, Java, JavaScript, ObjC, Proto, TableGen, TextProto
 Language:Cpp
 # BasedOnStyle:LLVM
 # 访问说明符(public、private等)的偏移
 AccessModifierOffset:-4
 # 开括号(开圆括号、开尖括号、开方括号)后的对齐: Align,DontAlign,AlwaysBreak(总是在开括号后换行
 AlignAfterOpenBracket:Align
 # 连续赋值时，对齐所有等号
 AlignConsecutiveAssignments:true
 # 连续声明时，对齐所有声明的变量名
 AlignConsecutiveDeclarations:true
 # 左对齐逃脱换行(使用反斜杠换行)的反斜杠
 AlignEscapedNewlinesLeft:true
 # 水平对齐二元和三元表达式的操作数
 AlignOperands:true
 # 对齐连续的尾随的注释
 AlignTrailingComments:true
 # 允许函数声明的所有参数在放在下一行
 AllowAllParametersOfDeclarationOnNextLine:true
 # 允许短的块放在同一行
 AllowShortBlocksOnASingleLine:false
 # 允许短的case标签放在同一行
 AllowShortCaseLabelsOnASingleLine:false
 # 允许短的函数放在同一行: None, InlineOnly(定义在类中), Empty(空函数), Inline(定义在类中，空函数), All
 AllowShortFunctionsOnASingleLine:Empty
 # 允许短的if语句保持在同一行
 AllowShortIfStatementsOnASingleLine:false
 # 允许短的循环保持在同一行
 AllowShortLoopsOnASingleLine:false
 # 总是在定义返回类型后换行(deprecated)
 AlwaysBreakAfterDefinitionReturnType:None
 # 总是在返回类型后换行: None, All, TopLevel(顶级函数，不包括在类中的函数), 
 #   AllDefinitions(所有的定义，不包括声明), TopLevelDefinitions(所有的顶级函数的定义)
 AlwaysBreakAfterReturnType:None
 # 总是在多行string字面量前换行
 AlwaysBreakBeforeMultilineStrings:false
 # 总是在template声明后换行
 AlwaysBreakTemplateDeclarations:false
 # false表示函数实参要么都在同一行，要么都各自一行
 BinPackArguments:true
 # false表示所有形参要么都在同一行，要么都各自一行
 BinPackParameters:true
 # 大括号换行，只有当BreakBeforeBraces设置为Custom时才有效
 BraceWrapping:   
   # class定义后面
  AfterClass:false
   # 控制语句后面
  AfterControlStatement:false
   # enum定义后面
  AfterEnum:false
   # 函数定义后面
  AfterFunction:false
   # 命名空间定义后面
  AfterNamespace:false
   # ObjC定义后面
  AfterObjCDeclaration:false
   # struct定义后面
  AfterStruct:false
   # union定义后面
  AfterUnion:false
   # catch之前
  BeforeCatch:true
   # else之前
  BeforeElse:true
   # 缩进大括号
  IndentBraces:false
 # 在二元运算符前换行: None(在操作符后换行), NonAssignment(在非赋值的操作符前换行), All(在操作符前换行)
 BreakBeforeBinaryOperators:NonAssignment
 # 在大括号前换行: Attach(始终将大括号附加到周围的上下文), Linux(除函数、命名空间和类定义，与Attach类似), 
 #   Mozilla(除枚举、函数、记录定义，与Attach类似), Stroustrup(除函数定义、catch、else，与Attach类似), 
 #   Allman(总是在大括号前换行), GNU(总是在大括号前换行，并对于控制语句的大括号增加额外的缩进), WebKit(在函数前换行), Custom
 #   注：这里认为语句块也属于函数
 BreakBeforeBraces:Custom
 # 在三元运算符前换行
 BreakBeforeTernaryOperators:true
 # 在构造函数的初始化列表的逗号前换行
 BreakConstructorInitializersBeforeComma:false
 # 每行字符的限制，0表示没有限制
 ColumnLimit:200
 # 描述具有特殊意义的注释的正则表达式，它不应该被分割为多行或以其它方式改变
 CommentPragmas:'^ IWYU pragma:'
 # 构造函数的初始化列表要么都在同一行，要么都各自一行
 ConstructorInitializerAllOnOneLineOrOnePerLine:false
 # 构造函数的初始化列表的缩进宽度
 ConstructorInitializerIndentWidth:4
 # 延续的行的缩进宽度
 ContinuationIndentWidth:4
 # 去除C++11的列表初始化的大括号{后和}前的空格
 Cpp11BracedListStyle:false
 # 继承最常用的指针和引用的对齐方式
 DerivePointerAlignment:false
 # 关闭格式化
 DisableFormat:false
 # 自动检测函数的调用和定义是否被格式为每行一个参数(Experimental)
 ExperimentalAutoDetectBinPacking:false
 # 需要被解读为foreach循环而不是函数调用的宏
 ForEachMacros:[ foreach, Q_FOREACH, BOOST_FOREACH ]
 # 对#include进行排序，匹配了某正则表达式的#include拥有对应的优先级，匹配不到的则默认优先级为INT_MAX(优先级越小排序越靠前)，
 #   可以定义负数优先级从而保证某些#include永远在最前面
 IncludeCategories: 
   - Regex:'^"(llvm|llvm-c|clang|clang-c)/'
    Priority:2
   - Regex:'^(<|"(gtest|isl|json)/)'
    Priority:3
   - Regex:'.*'
    Priority:1
 # 缩进case标签
 IndentCaseLabels:false
 # 缩进宽度
 IndentWidth:4
 # 函数返回类型换行时，缩进函数声明或函数定义的函数名
 IndentWrappedFunctionNames:false
 # 保留在块开始处的空行
 KeepEmptyLinesAtTheStartOfBlocks:true
 # 开始一个块的宏的正则表达式
 MacroBlockBegin:''
 # 结束一个块的宏的正则表达式
 MacroBlockEnd:''
 # 连续空行的最大数量
 MaxEmptyLinesToKeep:1
 # 命名空间的缩进: None, Inner(缩进嵌套的命名空间中的内容), All
 NamespaceIndentation:Inner
 # 使用ObjC块时缩进宽度
 ObjCBlockIndentWidth:4
 # 在ObjC的@property后添加一个空格
 ObjCSpaceAfterProperty:false
 # 在ObjC的protocol列表前添加一个空格
 ObjCSpaceBeforeProtocolList:true
 # 在call(后对函数调用换行的penalty
 PenaltyBreakBeforeFirstCallParameter:19
 # 在一个注释中引入换行的penalty
 PenaltyBreakComment:300
 # 第一次在<<前换行的penalty
 PenaltyBreakFirstLessLess:120
 # 在一个字符串字面量中引入换行的penalty
 PenaltyBreakString:1000
 # 对于每个在行字符数限制之外的字符的penalty
 PenaltyExcessCharacter:1000000
 # 将函数的返回类型放到它自己的行的penalty
 PenaltyReturnTypeOnItsOwnLine:60
 # 指针和引用的对齐: Left, Right, Middle
 PointerAlignment:Left
 # 允许重新排版注释
 ReflowComments:true
 # 允许排序#include
 SortIncludes:true
 # 在C风格类型转换后添加空格
 SpaceAfterCStyleCast:false
 # 在赋值运算符之前添加空格
 SpaceBeforeAssignmentOperators:true
 # 开圆括号之前添加一个空格: Never, ControlStatements, Always
 SpaceBeforeParens:ControlStatements
 # 在空的圆括号中添加空格
 SpaceInEmptyParentheses:false
 # 在尾随的评论前添加的空格数(只适用于//)
 SpacesBeforeTrailingComments:2
 # 在尖括号的<后和>前添加空格
 SpacesInAngles:true
 # 在容器(ObjC和JavaScript的数组和字典等)字面量中添加空格
 SpacesInContainerLiterals:true
 # 在C风格类型转换的括号中添加空格
 SpacesInCStyleCastParentheses:true
 # 在圆括号的(后和)前添加空格
 SpacesInParentheses:true
 # 在方括号的[后和]前添加空格，lamda表达式和未指明大小的数组的声明不受影响
 SpacesInSquareBrackets:true
 # 标准: Cpp03, Cpp11, Auto
 Standard:Cpp11
 # tab宽度
 TabWidth:4
 # 使用tab字符: Never, ForIndentation, ForContinuationAndIndentation, Always
 UseTab:Never
 ...

```
## 忽略部分代码的格式化
如果希望某个代码段不要参与格式化，可使用 // clang-format off 和 // clang-format on 注释对该代码段进行限定，像下面这样：
```cpp
void test(){
    // clang-format off
    Eigen::MatrixXd ref_mat=Eigen::MatrixXd::Zero(6,6);
    ref_mat<<
         1,        0,        0,        0,        0,        0,
         1,      0.5,     0.25,    0.125,   0.0625,  0.03125,
         1,        1,        1,        1,        1,        1,
        -1,       -0,       -0,       -0,       -0,       -0,
        -1,     -0.5,    -0.25,   -0.125,  -0.0625, -0.03125,
        -1,       -1,       -1,       -1,       -1,       -1;
    // clang-format on
}
```
