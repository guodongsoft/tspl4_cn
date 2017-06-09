第1章 介绍

Scheme is a general-purpose computer programming language. It is a high-level language, supporting operations on structured data such as strings, lists, and vectors, as well as operations on more traditional data such as numbers and characters. While Scheme is often identified with symbolic applications, its rich set of data types and flexible control structures make it a truly versatile language. Scheme has been employed to write text editors, optimizing compilers, operating systems, graphics packages, expert systems, numerical applications, financial analysis packages, virtual reality systems, and practically every other type of application imaginable. Scheme is a fairly simple language to learn, since it is based on a handful of syntactic forms and semantic concepts and since the interactive nature of most implementations encourages experimentation. Scheme is a challenging language to understand fully, however; developing the ability to use its full potential requires careful study and practice.

Scheme是一门通用的计算机编程语言。它是一门高级语言，既能操作数字和字符这样的基本数据类型一样，也能对结构化数据进行操作，比如字符串，列表和向量。Scheme通常被运用在符号运算上，它有丰富的数据类型和灵活的控制结构，使它成为正真意义上的通用语言。Scheme已经被用于编写文本编辑器，优化编译器，操作系统，图形处理，专家系统，数值运算，金融分析，虚拟现实系统和几乎所有可能的应用类型。Scheme是一门相当简单易学的语言，基于很少的语法形式和语义概念，并且大部分实现具备交互性质，鼓励编程过程中进行验证。要充分理解Scheme语言，是非常有挑战性的。要想在开发中发挥它的各种能力，需要认真的学习以及练习。

Scheme programs are highly portable across versions of the same Scheme implementation on different machines, because machine dependencies are almost completely hidden from the programmer. They are also portable across different implementations because of the efforts of a group of Scheme language designers who have published a series of reports, the "Revised Reports" on Scheme. The most recent, the "Revised6 Report" [24], emphasizes portability through a set of standard libraries and a standard mechanism for defining new portable libraries and top-level programs.

相同版本的Scheme实现在不同机器上有很高的可移植性，因为对于开发人员来说，机器的具体实现细节基本上被隐藏掉了。不同的实现之间也具备可移植性，因为Scheme语言的设计者们致力于定制语言标准“Revised Reports"。最近的标准版本是"Revised6 Report"，通过一套标准库和一个标准机制来定义新的可移植库以及顶级程序来增强可移植性。

Although some early Scheme systems were inefficient and slow, many newer compiler-based implementations are fast, with programs running on par with equivalent programs written in lower-level languages. The relative inefficiency that sometimes remains results from run-time checks that support generic arithmetic and help programmers detect and correct various common programming errors. These checks may be disabled in many implementations.

早期的Scheme系统比较低效且运行缓慢，现在新的基于编译器的实现，运行速度和用低级语言开发的程序一样快。它支持在运行时进行一般性算数运算检查可以发现各种常见错误，但有时候会拖慢执行速度。在很多的实现里这些检查可以被禁用。

Scheme supports many types of data values, or objects, including characters, strings, symbols, lists or vectors of objects, and a full set of numeric data types, including complex, real, and arbitrary-precision rational numbers.

Scheme支持多种数据类型或对象，包括字符，字符串，符号，列表，或向量，还有一套完整的数值类型，包括复数，实数和任意精度的有理数。

The storage required to hold the contents of an object is dynamically allocated as necessary and retained until no longer needed, then automatically deallocated, typically by a garbage collector that periodically recovers the storage used by inaccessible objects. Simple atomic values, such as small integers, characters, booleans, and the empty list, are typically represented as immediate values and thus incur no allocation or deallocation overhead.

存储器需要为对象动态分配空间，并且一直保持该对象的数据直到不再需要它，然后自动释放，通常通过垃圾回收器来定期回收不再使用的存储空间。简单的原始值，比如小整数，字符，布尔值，和空列表等，通常被当作立即数处理，因此不会产生分配和释放的开销。

Regardless of representation, all objects are first-class data values; because they are retained indefinitely, they may be passed freely as arguments to procedures, returned as values from procedures, and combined to form new objects. This is in contrast with many other languages where composite data values such as arrays are either statically allocated and never deallocated, allocated on entry to a block of code and unconditionally deallocated on exit from the block, or explicitly allocated and deallocated by the programmer.

不管如何表现，所有的对象都是第一等数据；因为他们都是永久保持的，他们可以被作为参数自由的传递给过程，作为结果值从过程中返回，或者组合成新的对象。和许多其它语言有所不同的是，这些语言的复合数据，如数组时静态分配的，并且从不释放，有的是在进入一个代码块时分配空间，退出时无条件释放，或者由程序员来管理分配与释放。

Scheme is a call-by-value language, but for at least mutable objects (objects that can be modified), the values are pointers to the actual storage. These pointers remain behind the scenes, however, and programmers need not be conscious of them except to understand that the storage for an object is not copied when an object is passed to or returned from a procedure.

Scheme是一种"call-by-value"(传值调用)语言，但是，至少对于可变对象来说，它们存储的是地址。这些地址被隐藏起来了，程序员不需要意识到这些，只需理解，当一个对象被传递或返回时，并不是进行对象拷贝，而是地址传递。

At the heart of the Scheme language is a small core of syntactic forms from which all other forms are built. These core forms, a set of extended syntactic forms derived from them, and a set of primitive procedures make up the full Scheme language. An interpreter or compiler for Scheme can be quite small and potentially fast and highly reliable. The extended syntactic forms and many primitive procedures can be defined in Scheme itself, simplifying the implementation and increasing reliability.

Scheme的语法内核很小，其它语法形式是由核心语法形式扩展出来的。这些核心形式，再加上从它们扩展的语法形式，以及一组原始过程，就构成了完整的Scheme语言。Scheme的解释器和编译器可以做到很小，并有潜在的执行速度和高度的可靠性。扩展的语法形式和许多原始过程可以由Scheme本身来定义，简化了实现的复杂性，并且增加了可靠性。

Scheme programs share a common printed representation with Scheme data structures. As a result, any Scheme program has a natural and obvious internal representation as a Scheme object. For example, variables and syntactic keywords correspond to symbols, while structured syntactic forms correspond to lists. This representation is the basis for the syntactic extension facilities provided by Scheme for the definition of new syntactic forms in terms of existing syntactic forms and procedures. It also facilitates the implementation of interpreters, compilers, and other program transformation tools for Scheme directly in Scheme, as well as program transformation tools for other languages in Scheme.

Scheme程序和数据结构使用相同的表示方式。这样做的结果，任何Scheme代码都可以自然而然地被表示为列表形式。例如，变量和语法关键字表示为符号，结构化的语法表示为列表。这些表示形式是Scheme进行语法扩展的基础，可以从现有的语法形式和过程扩展出新的语法形式。它还有助于直接用Scheme语法自身来实现Scheme解释器，编译器和其它程序转换工具，以及其它语言的程序转换工具。

Scheme variables and keywords are lexically scoped, and Scheme programs are block-structured. Identifiers may be imported into a program or library or bound locally within a given block of code such as a library, program, or procedure body. A local binding is visible only lexically, i.e., within the program text that makes up the particular block of code. An occurrence of an identifier of the same name outside this block refers to a different binding; if no binding for the identifier exists outside the block, then the reference is invalid. Blocks may be nested, and a binding in one block may shadow a binding for an identifier of the same name in a surrounding block. The scope of a binding is the block in which the bound identifier is visible minus any portions of the block in which the identifier is shadowed. Block structure and lexical scoping help create programs that are modular, easy to read, easy to maintain, and reliable. Efficient code for lexical scoping is possible because a compiler can determine before program evaluation the scope of all bindings and the binding to which each identifier reference resolves. This does not mean, of course, that a compiler can determine the values of all variables, since the actual values are not computed in most cases until the program executes.

Scheme的变量和关键字是词法作用域的，Scheme程序是块结构的。标识符可以导入到程序或库中，或者被局部绑定到给定的代码块内部，例如库，程序或过程体内部。局部绑定只能在特定的代码块中可见。代码块外部出现的同名标识符指向不同的绑定，如果标识符在代码块外部没有绑定，在代码块外部对它的引用是无效的。代码块可以嵌套，并且一个内层的代码块里的绑定可以屏蔽外层代码块中的同名绑定。一个绑定的作用域，是该绑定所在的代码块的作用域，减去那些屏蔽该绑定的内层代码块的作用域之后的部分。由块结构和词法作用域构造出的模块化程序，容易阅读，维护简单，且提高可靠性。生成高效的词法作用域的代码是有可能的，因为编译器可以在执行程序之前，确定所有绑定的作用域以及解析出每个标识符引用到的绑定。当然，这并不意味着编译器能够确定所有变量的值，因为变量的值在大多数情况下不会被计算出来，直到程序执行到它为止。

In most languages, a procedure definition is simply the association of a name with a block of code. Certain variables local to the block are the parameters of the procedure. In some languages, a procedure definition may appear within another block or procedure so long as the procedure is invoked only during execution of the enclosing block. In others, procedures can be defined only at top level. In Scheme, a procedure definition may appear within another block or procedure, and the procedure may be invoked at any time thereafter, even if the enclosing block has completed its execution. To support lexical scoping, a procedure carries the lexical context (environment) along with its code.

在大多数语言中，过程的定义只是简单的把名字和代码块关联起来。有些语言的代码块的局部变量就是过程的参数。有些语言，过程可以定义在另一个过程或代码块中，但是只能在封闭的代码块被执行时才能被调用。而对于另外一些语言，过程只能定义成全局的。对于Scheme语言来说，过程可以定义在另一个过程或者代码块中，并且可以在被定义之后的任意时刻调用，甚至在外层代码结束之后也可以。Scheme支持词法作用域，它的过程携带了词法上下文（环境）。

Furthermore, Scheme procedures are not always named. Instead, procedures are first-class data objects like strings or numbers, and variables are bound to procedures in the same way they are bound to other objects.

另外，Scheme的过程并不是都被命名。它的过程是第一等数据对象，就像字符串和数字那样，并且变量可以像绑定其它数据对象那样绑定过程。

As with procedures in most other languages, Scheme procedures may be recursive. That is, any procedure may invoke itself directly or indirectly. Many algorithms are most elegantly or efficiently specified recursively. A special case of recursion, called tail recursion, is used to express iteration, or looping. A tail call occurs when one procedure directly returns the result of invoking another procedure; tail recursion occurs when a procedure recursively tail-calls itself, directly or indirectly. Scheme implementations are required to implement tail calls as jumps (gotos), so the storage overhead normally associated with recursion is avoided. As a result, Scheme programmers need master only simple procedure calls and recursion and need not be burdened with the usual assortment of looping constructs.

和大多数其它语言一样，Scheme的过程也可以递归调用，也就是说，过程可以直接或间接的调用自己。很多算法用递归的方式来实现，会显得更优雅或者更高效。有一种特殊的递归，叫做尾递归，它用来实现迭代（循环）算法。尾调用发生在当一个过程调用另一个过程，并直接把它的返回值发回给自己的调用者时；尾递归发生在一个过程直接或间接的尾调用自己。一个Scheme的实现需要将尾调用实现为跳转，这样，就避免了和递归相关联的存储开销。

Scheme supports the definition of arbitrary control structures with continuations. A continuation is a procedure that embodies the remainder of a program at a given point in the program. A continuation may be obtained at any time during the execution of a program. As with other procedures, a continuation is a first-class object and may be invoked at any time after its creation. Whenever it is invoked, the program immediately continues from the point where the continuation was obtained. Continuations allow the implementation of complex control mechanisms including explicit backtracking, multithreading, and coroutines.

Scheme通过continuations（续延）支持定义任意的控制结构。continunation表示的是过程在给定的位置，程序“接下来”要做的事情。continuation可以在程序执行的任意时刻被捕获。和其它过程一样，continuation也是第一等数据对象，可以在创建后的任意时刻被调用。不管它什么时候被调用，程序会立即从捕获它的位置开始执行。通过continuaion可以实现复杂的控制机制，包括回溯，多线程及协同程序。

Scheme also allows programmers to define new syntactic forms, or syntactic extensions, by writing transformation procedures that determine how each new syntactic form maps to existing syntactic forms. These transformation procedures are themselves expressed in Scheme with the help of a convenient high-level pattern language that automates syntax checking, input deconstruction, and output reconstruction. By default, lexical scoping is maintained through the transformation process, but the programmer can exercise control over the scope of all identifiers appearing in the output of a transformer. Syntactic extensions are useful for defining new language constructs, for emulating language constructs found in other languages, for achieving the effects of in-line code expansion, and even for emulating entire languages in Scheme. Most large Scheme programs are built from a mix of syntactic extensions and procedure definitions.

Scheme允许程序员定义新的语法形式（语法扩展），通过编写转换过程，确定每一个新的语法形式如何映射到现有的语法形式中。这些转换过程本身借助于Scheme的便捷的高级模式语言，它可以自动执行语法检查，解析输入并重新构造输出。缺省情况下，转换过程保持词法作用域，但是程序员可以控制所有标识符在代码转换后的作用域。语法扩展通过定义新的语言结构，用来模仿其它语言里的语法结构，达到内联代码的效率，甚至用Scheme模拟整个语言。大型的Scheme程序一般是混合使用语法扩展和过程定义。

Scheme evolved from the Lisp language and is considered to be a dialect of Lisp. Scheme inherited from Lisp the treatment of values as first-class objects, several important data types, including symbols and lists, and the representation of programs as objects, among other things. Lexical scoping and block structure are features taken from Algol 60 [21]. Scheme was the first Lisp dialect to adopt lexical scoping and block structure, first-class procedures, the treatment of tail calls as jumps, continuations, and lexically scoped syntactic extensions.

Scheme从Lisp语言演化而来，被认为是Lisp的方言之一。Scheme从Lisp那里继承了将值作为第一等对象的处理方式，和一些重要的数据类型，包括符号和列表，还有将程序表示为对象等。词法作用域及块结构继承自Algol 60[21]。在Lisp的方言中，Scheme第一个支持词法作用域，快结构，第一等过程，尾递归，continuation，以及词法作用域限定的语法扩展。

Common Lisp [27] and Scheme are both contemporary Lisp languages, and the development of each has been influenced by the other. Like Scheme but unlike earlier Lisp languages, Common Lisp adopted lexical scoping and first-class procedures, although Common Lisp's syntactic extension facility does not respect lexical scoping. Common Lisp's evaluation rules for procedures are different from the evaluation rules for other objects, however, and it maintains a separate namespace for procedure variables, thereby inhibiting the use of procedures as first-class objects. Also, Common Lisp does not support continuations or require proper treatment of tail calls, but it does support several less general control structures not found in Scheme. While the two languages are similar, Common Lisp includes more specialized constructs, while Scheme includes more general-purpose building blocks out of which such constructs (and others) may be built.

Common Lisp [27]和Scheme是当代的Lisp方言，并且相互受到对方的影响。像Scheme一样，不同于以前的Lisp语言，Common Lisp采用了词法作用域和第一等过程。尽管Common Lisp的语法扩展并不遵守词法作用域。Common Lisp对过程的求值规则和其它对象的求值规则并不相同，它把在一个单独的命名空间里维护过程变量（过程名），从而限制了将过程作为第一等对象的使用。Common Lisp也不支持continuation和尾调用，但是它支持几种 Scheme没有的控制结构。这两种语言比较相似，Common Lisp包含更多的专门的结构，而 Scheme包括更多的通用模块，若没有的话，也可以被构建出来。

The remainder of this chapter describes Scheme's syntax and naming conventions and the typographical conventions used throughout this book.

本章剩下的部分描述Scheme的语法及命名规约，以及贯穿与本书中的排版规则。
