# SWIG

## Overview
https://www.swig.org/

SWIG is a software development tool that connects programs written in C and C++ with a variety of high-level programming languages. SWIG is used with different types of target languages including common scripting languages such as Javascript, Perl, PHP, Python, Tcl and Ruby. The list of supported languages also includes non-scripting languages such as C#, D, Go language, Java including Android, Lua, OCaml, Octave, Scilab and R. Also several interpreted and compiled Scheme implementations (Guile, MzScheme/Racket) are supported. SWIG is most commonly used to create high-level interpreted or compiled programming environments, user interfaces, and as a tool for testing and prototyping C/C++ software. SWIG is typically used to parse C/C++ interfaces and generate the 'glue code' required for the above target languages to call into the C/C++ code. SWIG can also export its parse tree in the form of XML. SWIG is free software and the code that SWIG generates is compatible with both commercial and non-commercial projects.

SWIG是一种软件开发工具，用于将用C和C++编写的程序与多种高级编程语言连接起来。SWIG与不同类型的目标语言一起使用，包括常见的脚本语言，如Javascript、Perl、PHP、Python、Tcl和Ruby。支持的语言列表还包括非脚本语言，如C＃、D、Go语言、Java（包括Android）、Lua、OCaml、Octave、Scilab和R。此外，还支持几种解释型和编译型Scheme实现（Guile、MzScheme/Racket）。SWIG最常用于创建高级解释型或编译型编程环境、用户界面，并用作测试和原型开发C/C++软件的工具。SWIG通常用于解析C/C++接口并生成所需的“粘合代码”，以便上述目标语言能够调用C/C++代码。SWIG还可以将其解析树导出为XML格式。SWIG是自由软件，其生成的代码与商业项目和非商业项目均兼容。

SWIG is an interface compiler that connects programs written in C and C++ with scripting languages such as Perl, Python, Ruby, and Tcl. It works by taking the declarations found in C/C++ header files and using them to generate the wrapper code that scripting languages need to access the underlying C/C++ code. In addition, SWIG provides a variety of customization features that let you tailor the wrapping process to suit your application.

SWIG是一个接口编译器，用于将用C和C++编写的程序与诸如Perl、Python、Ruby和Tcl之类的脚本语言连接起来。它通过获取C/C++头文件中的声明，并使用这些声明来生成脚本语言需要访问底层C/C++代码的包装器代码来实现。此外，SWIG还提供了多种定制功能，使您可以根据需要调整包装过程，以适应您的应用程序。

SWIG is used in a number of ways:

- Building more powerful C/C++ programs. Using SWIG, you can replace the main() function of a C program with a scripting interpreter from which you can control the application. This adds quite a lot of flexibility and makes the program "programmable." That is, the scripting interface allows users and developers to easily modify the behavior of the program without having to modify low-level C/C++ code. The benefits of this are numerous. In fact think of all of the large software packages that you use every day---nearly all of them include special a macro language, configuration language, or even a scripting engine that allows users to make customizations.
- Rapid prototyping and debugging. SWIG allows C/C++ programs to be placed in a scripting environment that can be used for testing and debugging. For example, you might test a library with a collection of scripts or use the scripting interpreter as an interactive debugger. Since SWIG requires no modifications to the underlying C/C++ code, it can be used even if the final product does not rely upon scripting.
- Systems integration. Scripting languages work fairly well for controlling and gluing loosely-coupled software components together. With SWIG, different C/C++ programs can be turned into scripting language extension modules. These modules can then be combined together to create new and interesting applications.
- Construction of scripting language extension modules. SWIG can be used to turn common C/C++ libraries into components for use in popular scripting languages. Of course, you will still want to make sure that no-one else has already created a module before doing this.

SWIG的应用方式有多种：

- 构建更强大的C/C++程序。使用SWIG，您可以将C程序的main()函数替换为脚本解释器，通过该解释器可以控制应用程序。这增加了相当多的灵活性，使程序变得"可编程"。也就是说，脚本接口允许用户和开发人员在不必修改底层C/C++代码的情况下轻松修改程序的行为。这带来了许多好处。事实上，想想您每天使用的所有大型软件包，几乎所有这些软件包都包括特殊的宏语言、配置语言，甚至是脚本引擎，允许用户进行定制。
- 快速原型制作和调试。SWIG允许将C/C++程序放置在可用于测试和调试的脚本环境中。例如，您可以使用一组脚本测试库，或将脚本解释器用作交互式调试器。由于SWIG不需要对底层C/C++代码进行修改，即使最终产品不依赖于脚本，也可以使用它。
- 系统集成。脚本语言相当适用于控制和组合松散耦合的软件组件。通过SWIG，不同的C/C++程序可以转换为脚本语言扩展模块。然后，可以将这些模块组合在一起，创建新的有趣应用程序。
- 构建脚本语言扩展模块。可以使用SWIG将常见的C/C++库转换为供流行脚本语言使用的组件。当然，在执行此操作之前，您仍然需要确保没有其他人已经创建了相应的模块。

SWIG有时会与诸如CORBA和COM等系统中的接口定义语言（IDL）编译器进行比较。尽管存在一些相似之处，SWIG的整个设计理念是使您无需为应用程序添加额外的IDL规范层。从某种程度上说，它更像是一种快速应用程序开发和原型制作工具。具体来说：

- ISO C/C++语法。SWIG解析已经使用许多特殊指令扩展的ISO C++。因此，接口通常是通过获取头文件并稍微调整来构建的。这种特定方法在底层C/C++程序经常需要修改时特别有用。

- SWIG不是存根（stub）生成器。SWIG生成的代码只需进行编译和运行。您不必像在类似RPC的系统中那样填写任何存根或编写特殊的客户端/服务器代码。

- SWIG不定义协议，也不是组件框架。SWIG不定义关于软件组件之间交互方式的机制或规则。它也不是专用的运行时库或替代的脚本语言API。SWIG只是一个代码生成器，提供了将C/C++与其他语言连接起来所需的粘合代码。

- 旨在与现有的C/C++代码一起使用。SWIG对现有代码几乎没有或根本没有修改要求。在很大程度上，它鼓励您在C/C++和其脚本接口之间保持清晰的分离。

- 可扩展性。SWIG提供了各种定制选项，允许您自由发挥。SWIG并不是为了强制执行编程道德规范。

最后值得注意的是，尽管SWIG偶尔会与其他更专门的脚本语言扩展构建工具（如Perl XS、Python bgen等）进行比较，但其主要受众是希望将脚本语言组件添加到其应用程序中的C/C++程序员。正因为如此，SWIG的关注点略有不同，与设计用于在脚本语言分发中构建小型模块以供广泛使用的工具不同。

有许多论文和教程介绍了SWIG。您还可以查看一个简单的教程，以查看SWIG的示例，或者查看其他人如何在其项目中使用SWIG。

自1996年2月以来，SWIG以各种形式免费提供，并且有大量开发人员进行了贡献。如今，SWIG仍然是一个全志愿的努力。大约有875人订阅了SWIG的邮件列表，并且在Github上有一个公共的Git仓库可供使用。现在，大多数Linux发行版中都可以找到SWIG的版本（不过，您几乎肯定会想在这里获取最新版本）。

SWIG provides control over most aspects of wrapper generation. Most of these customization options are fully integrated into the C++ type system--making it easy to apply customizations across inheritance hierarchies, template instantiations, and more. Features include:
Customized type conversion/marshaling.
- Exception handling.
- Class/structure extension.
- Memory management.
- Ambiguity resolution.
- Template instantiation.
- File import and cross-module linking.
- Code inclusion, helper function support.
- Extensive diagnostics (error/warning messages including fine grained warning suppression).
- Extended SWIG macro handling.

SWIG提供对大多数包装器生成方面的控制。这些定制选项大多完全集成到C++类型系统中，使得可以轻松地在继承层次结构、模板实例化等方面应用定制。其特点包括：
- 自定义类型转换/封送。
- 异常处理。
- 类/结构扩展。
- 内存管理。
- 歧义解决。
- 模板实例化。
- 文件导入和跨模块链接。
- 代码包含，辅助函数支持。
- 广泛的诊断（包括错误/警告消息，包括细粒度的警告抑制）。
- 扩展的SWIG宏处理。

## Tutorial

https://www.swig.org/tutorial.html

So you want to get going in a hurry? To illustrate the use of SWIG, suppose you have some C functions you want added to Tcl, Perl, Python, Java and C#. Specifically, let's say you have them in a file 'example.c'

所以您想要迅速上手？为了说明如何使用SWIG，假设您有一些C函数，您希望将它们添加到Tcl、Perl、Python、Java和C#中。具体来说，假设您在一个名为'example.c'的文件中有这些函数。

```c
/* File : example.c */

#include <time.h>
double My_variable = 3.0;

int fact(int n) {
    if (n <= 1) return 1;
    else return n*fact(n-1);
}

int my_mod(int x, int y) {
    return (x%y);
}
	
char *get_time()
{
    time_t ltime;
    time(&ltime);
    return ctime(&ltime);
}
```
### Interface file

Now, in order to add these files to your favorite language, you need to write an "interface file" which is the input to SWIG. An interface file for these C functions might look like this :

```c
/* example.i */
%module example
%{
/* Put header files here or function declarations like below */
extern double My_variable;
extern int fact(int n);
extern int my_mod(int x, int y);
extern char *get_time();
%}

extern double My_variable;
extern int fact(int n);
extern int my_mod(int x, int y);
extern char *get_time();
```

### Building a C# module

SWIG will also generate code for accessing C/C++ code from C# using PInvoke. Here is an example building a C# module (shown for Linux, see the SWIG Wiki Shared Libraries FAQ page for help with other operating systems). It uses the open source Mono C# compiler which runs on Windows and most Unix systems, but the Microsoft C# compiler (csc.exe) works equally well on Windows:

SWIG还将生成用于使用PInvoke从C#访问C/C++代码的代码。以下是一个构建C#模块的示例（显示为Linux版本，请参阅SWIG Wiki共享库常见问题页面以获取其他操作系统的帮助）。它使用开源的Mono C#编译器，该编译器适用于Windows和大多数Unix系统，但Microsoft的C#编译器（csc.exe）在Windows上同样适用：

```c
$ swig -csharp example.i
$ gcc -c -fpic example.c example_wrap.c
$ gcc -shared example.o  example_wrap.o   -o libexample.so
$ mono-csc -out:runme.exe *.cs
$ cat runme.cs
using System;
public class runme {
    static void Main() {
        Console.WriteLine(example.My_variable);
        Console.WriteLine(example.fact(5));
        Console.WriteLine(example.get_time());
    }
}
$ ./runme.exe
3
120
Thu Nov 17 21:24:13 2016

$
```