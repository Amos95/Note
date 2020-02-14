1. Make

   * Make工具就根据MakeFile中的命令进行编译和链接的.

   * MakeFile的基础格式

     ```makefile
     target...:prerequisites
     	command
     	...
     ```

     target:规则的目标。通常是最后需要生成的文件名或者为了实现这个目的而必需的中间过程文件名。可以是.o文件、也可以是最后的可执行程序的文件名等。另外,目标也可以是一个make执行的动作的名称,如目标“clean”,我们称这样的目标是“伪目标”。

     prerequisites:规则的依赖。生成规则目标所需要的文件名列表。通常一个目标依赖于一个或者多个文件。

     command:规则的命令行。是规则所要执行的动作(任意的 shell 命令或者是可在shell 下执行的程序)。它限定了 make 执行这条规则时所需要的动作。

     ```makefile
     all:foo
     foo:hello.o world.o
         gcc -o foo hello.o world.o -I.
     hello.o:hello.c hello.h world.h
         gcc -c hello.c
     world.o:world.c world.h
         gcc -c world.c
     clean:
         rm hello.o world.o
     ```

2. Cmake

   MakeFile在一些简单的工程完全可以人工手下，但是当工程非常大的时候，手写MakeFile也是非常麻烦的。

   Cmake根据CmakeList.txt跨平台生成对应平台能用的MakeFile。