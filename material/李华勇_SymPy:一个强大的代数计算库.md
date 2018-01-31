# SymPy--一个简洁易用的Python代数计算系统:point_left:
>相比于广为人知的用于数值计算的Python库：[Numpy](www.numpy.org/)，[SymPy](https://github.com/sympy/sympy)似乎有点默默无闻。本文旨在介绍Sympy这个强大的Python代数计算库，恰当使用Sympy能够极大简化代数计算的过程，降低开发计算的成本。

## Sympy是什么？
![Sympy logo](http://jbcdn1.b0.upaiyun.com/2014/05/160px-Sympy-160px.png)

SymPy是一个用来处理数学符号的Python库，旨在成为一个多功能但代码尽可能简洁以便于理解和扩展的计算机代数系统(CAS)。同时，SymPy完全是用Python编写的，并且不依赖任何外部的库。

Sympy的详细文档位于：http://docs.sympy.org/latest/index.html （需要翻墙）

Sympy的github主页位于：https://github.com/sympy/sympy

SymPy 这种符号运算系统的真正威力是，它能够做所有类型的符号运算。SymPy 能够计算导数、积分、求极限、解方程、矩阵运算等等。所有这些，都是基于符号的。它还包括了绘图（绘制函数的输出）、自动生成` LaTex` 代码、物理、统计、数论、几何、逻辑等模块。

大家可能还是不太明白，我稍微解释一下，单纯用语言内置的运算与变量解决的是，由值求结果。如：
```python
#仅用于说明，不要直接运行
print(x + y)
```
上式中的x与y在这条语句执行前你肯定得赋值的，否则就会出错。

而符号计算不同，你可以在之前将其设为符号。
```python
#仅用于说明，不要直接运行
x = Symbol('x')
y = Symbol('y')
print(x + y)
```
上述代码是可以的。因为Sympy库将x与y转换成了符号（概念上）。
## 给我一个使用Sympy的理由 (`へ´*)ノ
有许多现存的计算机代数系统（CAS），这里[维基百科](https://en.wikipedia.org/wiki/List_of_computer_algebra_systems)列出了其中的许多。在这些CAS中，SymPy 有哪些优势呢？

首先 SymPy 是完全免费的。它是开源的，并且遵守 BSD 许可。如果你想的话，你可以修改源代码之后拿出去卖。相比流行的商业系统，要花费高额资金购买授权。

第二， SymPy 使用 Python 语言。学多 CAS 发明了他们自己的语言。而 SymPy 没有，它完全采用 Python 编写，完全在 Python 中运行。这就意味着，如果你已经学会 Python ，也就会很容易地使用 SymPy ，因为你已经学会了语法。（如果你并不会 Python ，它也很容易学）。除此之外，我们已经知道，Python 是一个设计优良的编程语言。 SymPy 的开发者对他们开发数学软件的能力很自信，但是发明一门全新语言就是另外一回事情了。通过重用现有语言，我们将精力集中在了主要问题——数学上。

另外一个 CAS ，Sage 也使用 Python 作为它的语言。但是 Sage 很庞大，要下载超过 1GB 的数据。 SymPy 的一大优势就是它很轻量。除了体积小之外，他只依赖 Python ，所以容易地在任何地方运行。此外，Sage 和 SymPy 的目标不同。Sage 的目标是一个全功能的数学系统，通过将所有主要的开源数学系统编译组合成为一个。当你在 Sage 中调用一个函数，例如积分，它将调用其所包含的开源包中的一个。实际上， SymPy 也被包含在 Sage 之中。 SymPy 的目标是成为一个独立的系统，所有特性都是 SymPy 自己实现的。

SymPy 的最后一个重要特性是，它可以被当作库来使用。许多 CAS 致力于在交互环境下使用，但是若你打算将运算自动化，或者是扩展，他们将很难实现。而使用 SymPy ，你可以轻松地使用两种环境：交互式 Python 环境或作为库导入到你自己 Python 程序中。 SymPy 也提供了 API 给你，用来扩展你自己自定义的函数。
## 安装Sympy

sympy 可以安装在python 2.7或以上的任何计算机上。sympy需要首先安装mpmath python库。你可以选择使用anaconda安装或者直接使用pip安装。

* 使用anaconda安装：
```bash
conda update sympy
```
* 使用pip直接安装：
```bash
pip install -U sympy
```
* 或者你也可以选择使用git安装（这是最麻烦的方式，不过还是有人喜欢这么来┓( ´∀` )┏）
```bash
git clone git://github.com/sympy/sympy.git
git pull origin master
setupegg.py develop
```
## sympy 功能举例
sympy支持的非常多的运算，这里不可能全部展开写，详细的功能介绍请参考官方网站的[文档]()。这里我们选取几个功能简单介绍下：
### 符号计算
```python
from sympy import Symbol
x = Symbol('x')
y = Symbol('y')

from sympy import symbols, var
a, b, c = symbols('a,b,c')
d, e, f = symbols('d:f')
var('g:h')  #(g, h)
var('g:2')  #(g0, g1)

x + y + x - y   #2*x
(x + y)**2   #(x + y)**2
((x + y)**2).expand()   #x**2 + 2*x*y + y**2

#使用函数 subs(old, new) 可以将给定的符号代换成其它的数字，符号或者表达式
((x + y)**2).subs(x, 1)   #(y + 1)**2
((x + y)**2).subs(x, y)   #4*y**2
```
### 求极限
在SymPy中使用极限很简单，使用函数 `limit(function, variable, point)` ，所以为了计算当x趋于0时的极限只需要输入`limit(f,x,0)`，如下：
```python
from sympy import limit, Symbol, sin, oo
x = Symbol("x")
limit(sin(x)/x, x, 0)  # 1

limit(x, x, oo)     #oo
limit(1/x, x, oo)   #0
limit(x**x, x, 0)   #1
```
### 求导数
你可以对任何SymPy的表达式进行求导，使用函数 `diff(func, var)`, 高阶导数使用` diff(func, var, n)` :
```python
from sympy import diff, Symbol, sin, tan
x = Symbol('x')

diff(sin(x), x)     # cos(x)
diff(sin(2*x), x)   #2*cos(2*x)

diff(sin(2*x), x, 1)    # 2*cos(2*x)
diff(sin(2*x), x, 2)    # -4*sin(2*x)
diff(sin(2*x), x, 3)    # -8*cos(2*x)
```
### 求积分
SymPy支持初等超越函数和特使函数的不定积分和定积分，通过使用函数 `integrate()` ，这个函数用到了强大的扩展`Risch-Norman算法`、一些`启发式算法`和`模式匹配` ，例如：
```python
from sympy import integrate, erf, exp, sin, log, oo, pi, sinh, symbols
x, y = symbols('x,y')

#初等函数积分
integrate(6*x**5, x)  # x**6
integrate(sin(x), x)  # -cos(x)
integrate(log(x), x)  # x*log(x) - x

#定积分
integrate(x**3, (x, -1, 1))      # 0
integrate(sin(x), (x, 0, pi/2))  # 1
```
### 求微分方程
```python
>>> from sympy import Function, Symbol, dsolve
>>> f = Function('f')
>>> x = Symbol('x')
>>> f(x).diff(x, x) + f(x)
        2
       d
f(x) + ---(f(x))
         2
       dx

>>> dsolve(f(x).diff(x, x) + f(x), f(x))
f(x) = C1*sin(x) + C2*cos(x)
```
### 模式匹配
使用` .match() `模式和` Wild` 类，可以对表达式执行模式匹配，返回结果就是所需要的各个匹配值，以字典的形式呈现，就像：
```python
>>> from sympy import Symbol, Wild
>>> x = Symbol('x')
>>> p = Wild('p')
>>> (5*x**2).match(p*x**2)
{p: 5}

>>> q = Wild('q')
>>> (x**2).match(p*x**q)
{p: 1, q: 2}
```
如果匹配不成功，则返回` None `：
```python
>>> print((x + 1).match(p**x))
None
```
还可以在 `Wild` 类中添加排除参数，使得这些被排除的参数不会出现在结果当中：
```python
>>> p = Wild('p', exclude=[1, x])
>>> print((x + 1).match(x + p)) # 1 is excluded
None
>>> print((x + 1).match(p + 1)) # x is excluded
None
>>> print((x + 1).match(x + 2 + p)) # -1 is not excluded
{p_: -1}
```
