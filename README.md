# CS380I Programming Assignment 2: LiveOak - 2 to SaM Compiler

## 1. Assignment Overview
### 1.1 Task
Create a handwritten recursive-descent parser and SaM code generator for levels 0, 1, and 2 of the LiveOak language. Use the provided SaMTokenizer class for lexical analysis. The compiler should take a file containing a LiveOak program as input and produce an output file containing a SaM program that is a correct translation of the input program. The assignment aims to help understand recursive-descent parsing and what it means to implement a compiler. Related lecture videos include LiveOak, stack machines and SaM, recursive-descent parsing, and code generation.
### 1.2 Score and Due Date
The score is 100 points. The due date is October 20th at 11:59 pm. You can use up to 2 late (extension) days.
### 1.3 Submission Method
All submissions are electronic. You can do the assignment on any machine. The submission testing is automated on Gradescope. You need to submit compiler.jar (a runnable.jar file of your project) and source.zip (a.zip file containing all your source files).

## 2. Preparation Materials
### 2.1 Required Materials
- The SaM library (v2.6.3) containing the lexer (obtained from Programming Assignment 1). Compile your code with this.jar file. If you use an IDE, you need to add this.jar file as an external library to your project.
- A collection of public test cases (still being expanded).
### 2.2 Optional Materials
- A starter template for your compiler, available here (https://utexas.instructure.com/courses/1404625/ files/79509966?wrap=1) (https://utexas.instructure.com/courses/1404625/files/79509966/ download?download_frd=1).
- The HTML documentation of the SaM API, available here (https://utexas.instructure.com/ courses/1404625/files/79016316?wrap=1) (https://utexas.instructure.com/courses/1404625/ files/79016316/download?download_frd=1).
- The design document containing the complete workings of the SaM interpreter, available here (https://utexas.instructure.com/courses/1404625/files/79016315?wrap=1) (https:// utexas.instructure.com/courses/1404625/files/79016315/download?download_frd=1).

## 3. Assignment Details
### 3.1 Grammar Related
- There will always be a main method in the input program. The program starts executing from the main method. The main method takes no parameters.
- There will always be a return statement at the end of a method in the input program.
- Comments in the input program are automatically handled by the SamTokenizer class.
- There is no overloading of methods.
- The definition of a method can occur either before or after calls to it. Each method needs a symbol table.
- A break statement must be lexically nested within one or more loops. When executed, it terminates the execution of the innermost loop in which it is nested. You are required to handle illegal break statements.
- If a program does not satisfy the grammar or the textual description of the language, the compiler should print a short error message and/or exit with a non-zero exit status.
### 3.2 Compiler Related
The compiler should be in the Java class assignment2.LiveOak2Compiler. It should take two command-line arguments. The first is an input file containing a LiveOak program. The second is an output file that will contain the generated SaM code. It is recommended to handle complexity by working up through the levels of the source language.

## 4. Evaluation
### 4.1 Evaluation Commands
- Compiling a LiveOak - 2 program: java -jar compiler.jar test1.lo output.sam
- Running a SaM program: java -cp SaM - 2.6.3.jar edu.utexas.cs.sam.ui.SamText output.sam
### 4.2 Evaluation Criteria
The compiler's correctness is evaluated based on the program's exit status. The public test cases are not exhaustive. It is highly recommended to create more test cases for testing. Before submitting the.jar file, make sure the exit status matches the expected output on all test cases.

## 5. Resources
The assignment counts for 30% of your course grade and is auto-graded using Gradescope. The names of the test cases indicate the level of the language they are testing. Grading is based only on the LiveOak - 2 test cases. Both public and private test cases will be used.



# CS380I Programming Assignment 2: LiveOak - 2 to SaM Compiler

## 1. 作业概述
### 1.1 任务
创建一个手写的递归下降解析器和SaM代码生成器，用于LiveOak语言的0、1、2级。需使用提供的SaMTokenizer类进行词法分析，编译器要接受包含LiveOak程序的文件作为输入，并生成包含正确翻译输入程序的SaM程序的输出文件。作业旨在帮助理解递归下降解析以及实现编译器的意义。相关讲座视频包括LiveOak、栈机和SaM、递归下降解析和代码生成。
### 1.2 分值与截止日期
分值为100分，截止日期为10月20日晚上11:59，可使用最多2个延迟（延期）天数。
### 1.3 提交方式
所有提交均为电子形式，可在任何机器上完成作业，提交的测试在Gradescope上自动进行。需提交compiler.jar（项目的可运行.jar文件）和source.zip（包含所有源文件的.zip文件）。

## 2. 准备材料
### 2.1 必需材料
- SaM库（v2.6.3），包含词法分析器（从编程作业1获得），编译代码时需使用此.jar文件，若使用IDE，需将其作为外部库添加到项目中。
- 公共测试用例集合（仍在扩展中）。
### 2.2 可选材料
- 编译器的起始模板，可从此处获取（https://utexas.instructure.com/courses/1404625/ files/79509966?wrap=1）（https://utexas.instructure.com/courses/1404625/files/79509966/ download?download_frd=1）。
- SaM API的HTML文档，从此处获取（https://utexas.instructure.com/ courses/1404625/files/79016316?wrap=1）（https://utexas.instructure.com/courses/1404625/ files/79016316/download?download_frd=1）。
- 包含SaM解释器完整工作原理的设计文档，从此处获取（https://utexas.instructure.com/courses/1404625/files/79016315?wrap=1）（https:// utexas.instructure.com/courses/1404625/files/79016315/download?download_frd=1）。

## 3. 作业细节
### 3.1 语法相关
- 输入程序中总会有一个main方法，程序从main方法开始执行，main方法无参数。
- 输入程序中方法的末尾总会有一个return语句。
- 输入程序中的注释由SamTokenizer类自动处理。
- 方法无重载。
- 方法的定义可在调用它之前或之后，每个方法需要一个符号表。
- break语句必须在一个或多个循环内，执行时终止其所在的最内层循环，需处理非法的break语句。
- 若程序不满足语法或语言的文本描述，编译器应打印简短的错误消息和/或以非零退出状态退出。
### 3.2 编译器相关
编译器应在Java类assignment2.LiveOak2Compiler中，应接受两个命令行参数，第一个是包含LiveOak程序的输入文件，第二个是将包含生成的SaM代码的输出文件。建议按源语言的级别逐步处理以管理复杂性。

## 4. 评估
### 4.1 评估命令
- 编译LiveOak - 2程序：java -jar compiler.jar test1.lo output.sam
- 运行SaM程序：java -cp SaM - 2.6.3.jar edu.utexas.cs.sam.ui.SamText output.sam
### 4.2 评估标准
根据程序的退出状态评估编译器的正确性，公共测试用例不详尽，强烈建议创建更多测试用例进行测试，提交.jar文件前确保退出状态在所有测试用例上与预期输出匹配。

## 5. 资源
作业占课程成绩的30%，由Gradescope自动评分，测试用例名称表明其测试的语言级别，评分仅基于LiveOak - 2测试用例，会使用公共和私人测试用例。
# CS380I LiveOak utexas

# CS Tutor | 计算机编程辅导 | Code Help | Programming Help

# WeChat: cstutorcs

# Email: tutorcs@163.com

# QQ: 749389476

# 非中介, 直接联系程序员本人
