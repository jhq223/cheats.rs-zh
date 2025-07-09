+++
weight = 1
sort_by = "weight"
template = "index.html"
insert_anchor_links = "right"
+++

<a href="javascript:request_admin()" style="cursor:default; "><img id="logo" class="hide_on_small" src="logo.png" alt="Ferris 拿着一张速查表。"></img></a>
<pagetitle>Rust 语言速查表</pagetitle>
<subtitle><span id="subtitle" onclick="advance_subtitle()">{{ date() }}</span></subtitle>


<blockquote class="legend">

<symbol-legend class="short">

包含可点击链接，指向
**The Book**、{{ book(page="") }}
**Rust by Example**、{{ ex(page="") }}
**标准库文档**、{{ std(page="std") }}
**Nomicon**{{ nom(page="") }} 和
**Reference**。{{ ref(page="") }}

</symbol-legend>

<symbol-legend class="long">

<twocolumn>
<column>

**可点击的符号** <br>
<br> <legend-symbol> {{ book(page="") }} </legend-symbol> **The Book**。
<br> <legend-symbol> {{ ex(page="") }} </legend-symbol> **Rust by Example**。
<br> <legend-symbol> {{ std(page="std") }} </legend-symbol> **标准库 (API)**。
<br> <legend-symbol> {{ nom(page="") }} </legend-symbol> **Nomicon**。
<br> <legend-symbol> {{ ref(page="") }} </legend-symbol> **Reference**。
<br> <legend-symbol> {{ rfc(page="") }} </legend-symbol> 官方 **RFC** 文档。
<br> <legend-symbol> {{ link(url="https://cheats.rs") }} </legend-symbol> **互联网**。
<br> <legend-symbol> {{ above(target="#") }} </legend-symbol> 在此页面**上方**。
<br> <legend-symbol> {{ below(target="#") }} </legend-symbol> 在此页面**下方**。

</column>
<column>

**其他符号** <br>
<br> <legend-symbol> {{ deprecated() }}   </legend-symbol>大部分已**弃用**。
<br> <legend-symbol> {{ edition(ed="'18") }} </legend-symbol>有**最低版本**要求。
<br> <legend-symbol> {{ experimental() }} </legend-symbol>需要 **Rust nightly**（或不完整）。
<br> <legend-symbol> {{ bad() }}   </legend-symbol>故意的**错误示例**或**陷阱**。
<br> <legend-symbol> {{ esoteric() }}   </legend-symbol>稍微**深奥**，很少使用或高级。
<br> <legend-symbol> {{ hot() }}   </legend-symbol>具有**卓越效用**的东西。
<br> <legend-symbol> {{ expands_to() }} </legend-symbol>父项**展开为** &hellip;
<br> <legend-symbol> {{ opinionated() }} </legend-symbol>**个人观点**。
<br> <legend-symbol> {{ todo() }} </legend-symbol>缺少**好的链接**或解释。

</column>
</twocolumn>
</symbol-legend>

<div style="text-align: right; height: 1px;">
    <span class="expander" style="font-size: 10px; position: relative; top: -20px;">
        <a href="javascript:toggle_legend();">➕</a>
    </span>
</div>

</blockquote>


<noprint>
<page-controls>
    <!-- <a id="" href="" style="float: left; margin-left:5px;">X-Ray Mode 👓</a> -->
    <a id="toggle_ligatures" href="javascript:toggle_ligatures()">字体连字 (<code>..=, =></code>)</a>
    <!-- <a id="expand_everything" class="hide_on_small" href="javascript:toggle_expand_all()">Expand all the things?</a> -->
    <a href="javascript:toggle_night_mode()">夜间模式 &#x1f4a1;</a>
    <a class="admin" href="javascript:toggle_xray()">X-Ray 📈</a>
</page-controls>

<div class="xray-help">
X-Ray 可视化已启用。这些显示了每个部分的汇总反馈。目前这是实验性的。已知问题：
<ul>
<li>一些收到大量反馈的部分没有显示（例如，“Hello Rust”）</li>
<li>它没有考虑部分的年龄（有些部分已经存在多年，有些只有几个月）</li>
<li>它既没有考虑反馈爆发（人们连续按同一个按钮3次），也没有考虑“最新反馈”（人们先赞后踩）。</li>
</ul>
反馈格式为（<span style="color:green;">正面</span>，<span style="color:red;">负面</span>，文本），等同于使用反馈按钮。
</div>

</noprint>

<noprint>
<toc><column>

**语言结构**
* [数据结构](#data-structures)
* [引用与指针](#references-pointers)
* [函数与行为](#functions-behavior)
* [控制流](#control-flow)
* [代码组织](#organizing-code)
* [类型别名与转换](#type-aliases-and-casts)
* [宏与属性](#macros-attributes)
* [模式匹配](#pattern-matching)
* [泛型与约束](#generics-constraints)
* [高阶项](#higher-ranked-items){{ esoteric() }}
* [字符串与字符](#strings-chars)
* [文档](#documentation)
* [杂项](#miscellaneous)

**幕后探秘**
* [抽象机](#the-abstract-machine)
* [语法糖](#language-sugar)
* [内存与生命周期](#memory-lifetimes)


**内存布局**
* [基本类型](#basic-types)
* [自定义类型](#custom-types)
* [引用与指针](#references-pointers-ui)
* [闭包](#closures-data)
* [标准库类型](#standard-library-types)

**杂项**
* [链接与服务](#links-services)
* [打印与 PDF](#printing-pdf)

</column>

<column>

**标准库**
* [一行代码](#one-liners)
* [线程安全](#thread-safety)
* [原子操作与缓存](#atomics-cache){{ esoteric() }}
* [迭代器](#iterators)
* [数字转换](#number-conversions)
* [字符串转换](#string-conversions)
* [字符串输出](#string-output)


**工具链**
* [项目结构](#project-anatomy)
* [Cargo](#cargo)
* [交叉编译](#cross-compilation)
* [工具指令](#tooling-directives)


**处理类型**
* [类型、Trait、泛型](#types-traits-generics)
* [外部类型与 Trait](#foreign-types-and-traits)
* [类型转换](#type-conversions)


**编码指南**
* [惯用的 Rust](#idiomatic-rust)
* [性能提示](#performance-tips)
* [Async-Await 101](#async-await-101)
* [API 中的闭包](#closures-in-apis)
* [Unsafe、Unsound、Undefined](#unsafe-unsound-undefined)
* [对抗性代码](#adversarial-code){{ esoteric() }}
* [API 稳定性](#api-stability)


</column>
</toc>
</noprint>

<noprint>

## 你好，Rust！

如果你是 Rust 新手，或者想尝试下面的内容：


<tabs>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-hello-1" name="tab-hello" checked/>
<label for="tab-hello-1"><b>Hello World</b></label>
<panel><div>
<div id="hellostatic">

```rust
fn main() {
    println!("Hello, world!");
}
```


</div>
<div id="helloplay"></div>
<div id="helloinfo">服务由 <a href="https://play.rust-lang.org/" target="_blank" rel="noopener">play.rust-lang.org <sup>🔗</sup></a> 提供</div>
<div id="helloctrl"><a href="javascript:show_playground(true);">▶️ 编辑并运行</a></div>
</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-hello-3" name="tab-hello">
<label for="tab-hello-3"><b>优势</b></label>
<panel><div>

**Rust 在可衡量方面做得非常好的事情**

- 编译后的代码[性能与 C / C++ 大致相同](https://benchmarksgame-team.pages.debian.net/benchmarksgame/box-plot-summary-charts.html)，并且内存和能源效率极佳。
- 可以[避免 C / C++ 中 70% 的安全问题](https://www.chromium.org/Home/chromium-security/memory-safety)，以及大多数内存问题。
- 强大的类型系统可防止[数据竞争](https://doc.rust-lang.org/nomicon/races.html)，带来[“无畏并发”](https://blog.rust-lang.org/2015/04/10/Fearless-Concurrency.html)（等等）。
- 无缝的 C 互操作性，以及[数十个受支持的平台](https://doc.rust-lang.org/rustc/platform-support.html)（基于 LLVM）。
- 连续 <strike>4</strike> <strike>5</strike> <strike>6</strike> <strike>7</strike> 8 年被评为[“最受喜爱或赞赏的语言”](https://survey.stackoverflow.co/2023/#section-admired-and-desired-programming-scripting-and-markup-languages)。🤷‍♀️
- 现代工具链：`cargo`（构建*就是好用*）、`clippy`（700+ 代码质量检查）、`rustup`（轻松管理工具链）。

</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-hello-4" name="tab-hello">
<label for="tab-hello-4"><b>劣势</b></label>
<panel><div>

**你可能会遇到的问题**

- 学习曲线陡峭；<sup>1</sup> 编译器强制执行的规则（尤其是内存规则），在其他语言中可能只是“最佳实践”。
- 在某些领域、目标平台（尤其是嵌入式）和 IDE 功能方面，缺少 Rust 原生库。<sup>1</sup>
- 编译时间比其他语言中的“类似”代码要长。<sup>1</sup>
- 库中粗心（使用 `unsafe`）的代码可能会偷偷破坏安全保证。
- ~~没有正式的语言规范~~，{{ link(url="https://spec.ferrocene.dev/") }} ~~可能会妨碍在某些领域（航空、医疗等）的合法使用~~。{{ link(url="https://ferrous-systems.com/ferrocene/") }}
- Rust 基金会可能会滥用其知识产权来影响“Rust”项目（例如，禁止使用名称，强制实施政策）。{{ link(url="https://devclass.com/2023/04/11/dont-call-it-rust-community-complains-about-draft-trademark-policy-restricting-use-of-word-marks/") }}{{ link(url="https://web.archive.org/web/20230413161930/https://old.reddit.com/r/rust/comments/12e7tdb/rust_trademark_policy_feedback_form/") }}<sup>2</sup>


<sup>1</sup> 比较 [Rust 调查](https://blog.rust-lang.org/2020/04/17/Rust-survey-2019.html#why-not-use-rust)。<br>
<sup>2</sup> 避免使用他们的标记（例如，在你的名称、URL、logo、着装中）可能就足够了。

</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-hello-5" name="tab-hello">
<label for="tab-hello-5"><b>安装</b></label>
<panel><div>

**下载**
- 从 [**rustup.rs**](https://rustup.rs/) 获取安装程序（强烈推荐）{{ hot() }}


**IDE**
- [**Rust Rover**](https://www.jetbrains.com/rust/)（非商业用途免费）
- [Visual Studio Code](https://code.visualstudio.com/) 与 [**rust-analyzer**](https://rust-analyzer.github.io/)（免费）


</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-hello-6" name="tab-hello">
<label for="tab-hello-6"><b>入门步骤</b></label>
<panel><div>

<!-- 注意 - 请只提交链接到高质量、"永久性"网站的PR
            这些网站专门用于学习Rust，可在浏览器中工作，内容适度
            精简，并有公开的Git仓库和问题跟踪器。
            此外，本节应非常简短，最多3个条目，因此只应列出
            “同类中最好的”。
             -->

**模块化入门资源**
- [**Rust 之旅 (Tour of Rust)**](https://tourofrust.com/TOC_en.html) - 实时代码和解释，并排呈现。
- [**简易英语学 Rust (Rust in Easy English)**](https://dhghomon.github.io/easy_rust/Chapter_3.html) - 60+ 概念，简单英语，示例驱动。
- [**给多语言程序员的 Rust 指南**](https://www.chiark.greenend.org.uk/~ianmdlvl/rust-polyglot/index.html) - 为有经验的程序员准备的指南。

此外，请考虑 **The Book**、{{ book(page="") }} **Rust by Example**、{{ ex(page="") }} **标准库**{{ std(page="std") }} 和 **Learn Rust**。{{ link(url="https://github.com/ImplFerris/LearnRust") }}



> **个人观点** {{ opinionated() }} &mdash; 如果你从未见过或使用过任何 Rust，最好在继续之前访问上面的链接之一；否则下一章可能会感觉有点简洁。

</div></panel></tab>

</tabs>
</noprint>


### 数据结构 {#data-structures}

通过关键字定义的数据类型和内存位置。

<fixed-2-column>

| 示例                                            | 解释                                                                                                                                                                                                                                                                                                      |
| ----------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `struct S {}`                                   | 定义一个**结构体 (struct)** {{ book(page="ch05-00-structs.html") }} {{ ex(page="custom_types/structs.html") }} {{ std(page="std/keyword.struct.html") }} {{ ref(page="expressions/struct-expr.html") }}，包含命名字段。                                                                                   |
| {{ tab() }} `struct S { x: T }`                 | 定义带有命名字段 `x`（类型为 `T`）的结构体。                                                                                                                                                                                                                                                              |
| {{ tab() }} `struct S` &#8203;`(T);`            | 定义“元组”结构体，其编号字段 `.0` 的类型为 `T`。                                                                                                                                                                                                                                                          |
| {{ tab() }} `struct S;`                         | 定义**零大小** {{ nom(page="exotic-sizes.html#zero-sized-types-zsts")}} 的单元结构体。不占空间，会被优化掉。                                                                                                                                                                                              |
| `enum E {}`                                     | 定义一个**枚举 (enum)**，{{ book(page="ch06-01-defining-an-enum.html") }} {{ ex(page="custom_types/enum.html#enums") }} {{ ref(page="items/enumerations.html") }} 类似于[代数数据类型](https://en.wikipedia.org/wiki/Algebraic_data_type)、[带标签的联合体](https://en.wikipedia.org/wiki/Tagged_union)。 |
| {{ tab() }}  `enum E { A, B`&#8203;`(), C {} }` | 定义枚举的变体；可以是单元式 `A`、元组式 `B` &#8203;`()` 和结构体式 `C{}`。                                                                                                                                                                                                                               |
| {{ tab() }}  `enum E { A = 1 }`                 | 带有显式**判别值**的枚举，{{ ref(page="items/enumerations.html#custom-discriminant-values-for-fieldless-enumerations") }} 例如用于 FFI。                                                                                                                                                                  |
| {{ tab() }}  `enum E {}`                        | 没有变体的枚举是**不可构造的 (uninhabited)**，{{ ref(page="glossary.html#uninhabited") }} 无法创建，类似于 'never' {{ below(target="#miscellaneous") }} {{ esoteric() }}                                                                                                                                  |
| `union U {}`                                    | 不安全的类 C **联合体 (union)** {{ ref(page="items/unions.html") }}，用于 FFI 兼容性。 {{ esoteric() }}                                                                                                                                                                                                   |
| `static X: T = T();`                            | **全局变量** {{ book(page="ch19-01-unsafe-rust.html#accessing-or-modifying-a-mutable-static-variable") }} {{ ex(page="custom_types/constants.html#constants") }} {{ ref(page="items/static-items.html#static-items") }}，具有 `'static` 生命周期，单一{{ bad() }}{{ note( note="1") }}内存位置。          |
| `const X: T = T();`                             | 定义**常量**，{{ book(page="ch03-01-variables-and-mutability.html#constants") }} {{ ex(page="custom_types/constants.html") }} {{ ref(page="items/constant-items.html") }} 在使用时会复制到一个临时位置。                                                                                                  |
| `let x: T;`                                     | 在栈上分配 `T` 字节{{ note( note="2") }}，绑定为 `x`。可赋值一次，但不可变。                                                                                                                                                                                                                              |
| `let mut x: T;`                                 | 类似于 `let`，但允许**可变性 (mutability)** {{ book(page="ch03-01-variables-and-mutability.html") }} {{ ex(page="variable_bindings/mut.html") }} 和可变借用。{{ note( note="3") }}                                                                                                                        |
| {{ tab() }} `x = y;`                            | 将 `y` 移动到 `x`，如果 `T` 不是 **`Copy`** {{ std(page="std/marker/trait.Copy.html") }}，则 `y` 失效；否则复制 `y`。                                                                                                                                                                                     |

</fixed-2-column>

<footnotes>

<sup>1</sup> 在*库*中，你可能会秘密地得到多个 `X` 的实例，这取决于你的 crate 是如何被导入的。{{ link(url="https://doc.rust-lang.org/cargo/reference/resolver.html#version-incompatibility-hazards") }} <br>
<sup>2</sup> **绑定变量** {{ book(page="ch03-01-variables-and-mutability.html") }} {{ ex(page="variable_bindings.html") }} {{ ref(page="variables.html") }} 在同步代码中存在于栈上。在 `async {}` 中，它们成为 async 状态机的一部分，可能驻留在堆上。<br>
<sup>3</sup> 从技术上讲，*可变 (mutable)* 和 *不可变 (immutable)* 是用词不当。不可变绑定或共享引用仍然可以包含 Cell {{ std(page="std/cell/index.html") }}，从而提供*内部可变性*。

</footnotes>


{{ tablesep() }}

创建和访问数据结构；以及一些更具符号意义的类型。

<fixed-2-column>

| 示例                | 解释                                                                                                                                                                                                 |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `S { x: y }`        | 创建 `struct S {}` 或 `use` 引入的 `enum E::S {}`，字段 `x` 设置为 `y`。                                                                                                                             |
| `S { x }`           | 同上，但使用局部变量 `x` 作为字段 `x` 的值。                                                                                                                                                         |
| `S { ..s }`         | 从 `s` 中填充剩余字段，对 `Default::default()` 尤其有用。{{ std(page="std/default/trait.Default.html") }}                                                                                            |
| `S { 0: x }`        | 类似于下面的 `S` &#8203;`(x)`，但使用结构体语法设置字段 `.0`。                                                                                                                                       |
| `S`&#8203; `(x)`    | 创建 `struct S` &#8203;`(T)` 或 `use` 引入的 `enum E::S`&#8203; `()`，字段 `.0` 设置为 `x`。                                                                                                         |
| `S`                 | 如果 `S` 是单元结构体 `struct S;` 或 `use` 引入的 `enum E::S`，则创建 `S` 类型的值。                                                                                                                 |
| `E::C { x: y }`     | 创建枚举变体 `C`。上述其他方法也适用。                                                                                                                                                               |
| `()`                | 空元组，既是字面量也是类型，也称为**单元 (unit)**。{{ std(page="std/primitive.unit.html") }}                                                                                                         |
| `(x)`               | 带括号的表达式。                                                                                                                                                                                     |
| `(x,)`              | 单元素**元组 (tuple)**表达式。{{ ex(page="primitives/tuples.html") }} {{ std(page="std/primitive.tuple.html") }} {{ ref(page="expressions/tuple-expr.html") }}                                       |
| `(S,)`              | 单元素元组类型。                                                                                                                                                                                     |
| `[S]`               | 未指定长度的数组类型，即**切片 (slice)**。{{ ex(page="primitives/array.html") }} {{ std(page="std/primitive.slice.html") }} {{ ref(page="types/slice.html") }} 不能存在于栈上。{{ note( note="*") }} |
| `[S; n]`            | 固定长度 `n` 的**数组类型 (array type)** {{ ex(page="primitives/array.html") }} {{ std(page="std/primitive.array.html") }} {{ ref(page="types/array.html") }}，包含 `S` 类型的元素。                 |
| `[x; n]`            | 包含 `n` 个 `x` 副本的**数组实例 (array instance)** {{ ref(page="expressions/array-expr.html") }}（表达式）。                                                                                        |
| `[x, y]`            | 包含给定元素 `x` 和 `y` 的数组实例。                                                                                                                                                                 |
| `x[0]`              | 集合索引，此处使用 `usize`。通过 [**Index**](https://doc.rust-lang.org/std/ops/trait.Index.html)、[**IndexMut**](https://doc.rust-lang.org/std/ops/trait.IndexMut.html) 实现。                       |
| {{ tab() }} `x[..]` | 同上，通过范围（此处为*全范围*），也可是 `x[a..b]`、`x[a..=b]` 等，见下文。                                                                                                                          |
| `a..b`              | 创建**右侧不包含的范围 (range)** {{ std(page="std/ops/struct.Range.html") }} {{ ref(page="expressions/range-expr.html") }}，例如 `1..3` 表示 `1, 2`。                                                |
| `..b`               | 无起点的右侧不包含的**到…的范围 (range to)** {{ std(page="std/ops/struct.RangeTo.html") }}。                                                                                                         |
| `..=b`              | 无起点的**到…的包含范围 (inclusive range to)** {{ std(page="std/ops/struct.RangeToInclusive.html") }}。                                                                                              |
| `a..=b`             | **包含范围**，{{ std(page="std/ops/struct.RangeInclusive.html") }} `1..=3` 表示 `1, 2, 3`。                                                                                                          |
| `a..`               | 无终点的**从…开始的范围 (range from)** {{ std(page="std/ops/struct.RangeFrom.html") }}。                                                                                                             |
| `..`                | **全范围 (full range)**，{{ std(page="std/ops/struct.RangeFull.html") }} 通常表示*整个集合*。                                                                                                        |
| `s.x`               | **命名字段访问**，{{ ref(page="expressions/field-expr.html") }} 如果 `x` 不是 `S` 类型的一部分，可能会尝试 [Deref](https://doc.rust-lang.org/std/ops/trait.Deref.html)。                             |
| `s.0`               | 编号字段访问，用于元组类型 `S` &#8203;`(T)`。                                                                                                                                                        |

</fixed-2-column>

<footnotes>

<sup>*</sup> 目前是这样，{{ rfc( page ="1909-unsized-rvalues.html") }} 等待 [跟踪问题](https://github.com/rust-lang/rust/issues/48055) 完成。

</footnotes>


### 引用与指针 {#references-pointers}

授予对非自有内存的访问权限。另请参见泛型与约束部分。


<fixed-2-column>

<!-- | {{ tab() }} `&pin mut T` | Ergonomic wrapper for `Pin<&mut T>`. {{ std(page="std/pin/") }} {{ experimental() }} Prevents _selfref._ `t` from moving. |
| {{ tab() }} `&pin const T` | Ergonomic wrapper for `Pin<&T>`. {{ experimental() }} | -->


| 示例                                   | 解释                                                                                                                                                                                                                                                                                                   |
| -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `&S`                                   | 共享**引用 (reference)** {{ book(page="ch04-02-references-and-borrowing.html") }} {{ std(page="std/primitive.reference.html") }} {{ nom(page="references.html")}} {{ ref(page="types.html#pointer-types")}}（类型；用于存放*任何* `&s` 的空间）。                                                      |
| {{ tab() }} `&[S]`                     | 特殊的切片引用，包含 (`地址`, `数量`)。                                                                                                                                                                                                                                                                |
| {{ tab() }} `&str`                     | 特殊的字符串切片引用，包含 (`地址`, `字节长度`)。                                                                                                                                                                                                                                                      |
| {{ tab() }} `&mut S`                   | 允许修改的独占引用（也适用于 `&mut [S]`, `&mut dyn S` 等）。                                                                                                                                                                                                                                           |
| {{ tab() }} `&dyn T`                   | 特殊的**trait 对象 (trait object)** {{ book(page="ch17-02-trait-objects.html#using-trait-objects-that-allow-for-values-of-different-types") }} {{ ref(page="types/trait-object.html")}} 引用，形式为 (`地址`, `虚函数表`)；`T` 必须是**对象安全的**。 {{ ref(page="items/traits.html#object-safety")}} |
| `&s`                                   | 共享**借用 (borrow)** {{ book(page="ch04-02-references-and-borrowing.html") }} {{ ex(page="scope/borrow.html") }} {{ std(page="std/borrow/trait.Borrow.html") }}（例如，*这个* `s` 的地址、长度、虚函数表等，如 `0x1234`）。                                                                           |
| {{ tab() }} `&mut s`                   | 允许**可变性**的独占借用。{{ ex(page="scope/borrow/mut.html") }}                                                                                                                                                                                                                                       |
| `*const S`                             | 不可变的**裸指针类型 (raw pointer type)** {{ book(page="ch19-01-unsafe-rust.html#dereferencing-a-raw-pointer") }} {{ std(page="std/primitive.pointer.html") }} {{ ref(page="types.html#raw-pointers-const-and-mut") }}，不提供内存安全保证。                                                           |
| {{ tab() }} `*mut S`                   | 可变的裸指针类型，不提供内存安全保证。                                                                                                                                                                                                                                                                 |
| {{ tab() }} `&raw const s`             | 不通过引用直接创建裸指针；类似于 `ptr:addr_of!()` {{ std(page="std/ptr/macro.addr_of.html") }} {{ esoteric() }}                                                                                                                                                                                        |
| {{ tab() }} `&raw mut s`               | 同上，但可变。{{ experimental() }} 用于未对齐、紧凑的字段。{{ esoteric() }}                                                                                                                                                                                                                            |
| `ref s`                                | **通过引用绑定 (bind by reference)**，{{ ex(page="scope/borrow/ref.html") }} 使绑定成为引用类型。{{ deprecated() }}                                                                                                                                                                                    |
| {{ tab() }} `let ref r = s;`           | 等同于 `let r = &s`。                                                                                                                                                                                                                                                                                  |
| {{ tab() }} `let S { ref mut x } = s;` | 可变引用绑定 (`let x = &mut s.x`)，是解构{{ below( target = "#pattern-matching") }}的简写版本。                                                                                                                                                                                                        |
| `*r`                                   | **解引用 (dereference)** {{ book(page="ch15-02-deref.html") }} {{ std(page="std/ops/trait.Deref.html") }} {{ nom(page="vec-deref.html") }} 一个引用 `r` 以访问它指向的内容。                                                                                                                           |
| {{ tab() }} `*r = s;`                  | 如果 `r` 是一个可变引用，则将 `s` 移动或复制到目标内存。                                                                                                                                                                                                                                               |
| {{ tab() }} `s = *r;`                  | 如果 `*r` 是 `Copy` 类型，则将 `s` 设为 `r` 所引用内容的副本。                                                                                                                                                                                                                                         |
| {{ tab() }} `s = *r;`                  | 如果 `*r` 不是 `Copy` 类型，则无法工作 {{ bad() }}，因为这会移动并留下空值。                                                                                                                                                                                                                           |
| {{ tab() }} `s = *my_box;`             | 对于**`Box`**{{ std(page="std/boxed/index.html") }}的特殊情况{{ link(url="https://web.archive.org/web/20230130111147/https://old.reddit.com/r/rust/comments/b4so6i/what_is_exactly/ej8xwg8/") }}，可以移出非 `Copy` 的借用内容。                                                                       |
| `'a`                                   | **生命周期参数**，{{ book(page="ch10-00-generics.html") }} {{ ex(page="scope/lifetime.html")}} {{ nom(page="lifetimes.html") }} {{ ref(page="items/generics.html#type-and-lifetime-parameters")}} 静态分析中一个流程的持续时间。                                                                       |
| {{ tab() }}  `&'a S`                   | 只接受某个 `s` 的地址；该地址存在时间为 `'a` 或更长。                                                                                                                                                                                                                                                  |
| {{ tab() }}  `&'a mut S`               | 同上，但允许地址内容被改变。                                                                                                                                                                                                                                                                           |
| {{ tab() }}  `struct S<'a> {}`         | 表明这个 `S` 将包含一个生命周期为 `'a` 的地址。`S` 的创建者决定 `'a`。                                                                                                                                                                                                                                 |
| {{ tab() }} `trait T<'a> {}`           | 表明任何 `impl T for S` 的 `S` 可能包含一个地址。                                                                                                                                                                                                                                                      |
| {{ tab() }}  `fn f<'a>(t: &'a T)`      | 表明此函数处理某个地址。调用者决定 `'a`。                                                                                                                                                                                                                                                              |
| `'static`                              | 特殊的生命周期，持续整个程序执行期间。                                                                                                                                                                                                                                                                 |

</fixed-2-column>



###  函数与行为 {#functions-behavior}

定义代码单元及其抽象。

<fixed-2-column>

| 示例                                                    | 解释                                                                                                                                                                                                                                                                                                             |
| ------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `trait T {}`                                            | 定义一个 **trait**；{{ book(page="ch10-02-traits.html") }} {{ ex(page="trait.html") }} {{ ref(page="items/traits.html") }} 类型可以遵循的共同行为。                                                                                                                                                              |
| `trait T : R {}`                                        | `T` 是**父 trait (supertrait)** {{ book(page="ch19-03-advanced-traits.html#using-supertraits-to-require-one-traits-functionality-within-another-trait") }} {{ ex(page="trait/supertraits.html") }} {{ ref(page="items/traits.html#supertraits") }} `R` 的子 trait。任何 `S` 必须先 `impl R` 才能 `impl T`。      |
| `impl S {}`                                             | 为类型 `S` **实现 (implementation)** {{ ref(page="items/implementations.html") }} 功能，例如方法。                                                                                                                                                                                                               |
| `impl T for S {}`                                       | 为类型 `S` 实现 trait `T`；指定 `S` *究竟如何*表现得像 `T`。                                                                                                                                                                                                                                                     |
| `impl !T for S {}`                                      | 禁用一个自动派生的 **auto trait**。{{ nom(page="send-and-sync.html") }} {{ ref(page="special-types-and-traits.html#auto-traits") }} {{ experimental() }} {{ esoteric() }}                                                                                                                                        |
| `fn f() {}`                                             | 定义一个**函数 (function)**；{{ book(page="ch03-03-how-functions-work.html") }}  {{ ex(page="fn.html") }} {{ ref(page="items/functions.html") }} 如果在 `impl` 内部，则是关联函数。                                                                                                                              |
| {{ tab() }} `fn f() -> S {}`                            | 同上，返回一个 `S` 类型的值。                                                                                                                                                                                                                                                                                    |
| {{ tab() }} `fn f(&self) {}`                            | 定义一个**方法 (method)**，{{ book(page="ch05-03-method-syntax.html") }}  {{ ex(page="fn/methods.html") }}  {{ ref(page="items/associated-items.html#methods") }}  例如在 `impl S {}` 内部。                                                                                                                     |
| `struct S` &#8203;`(T);`                                | 更晦涩地，*也*{{ above(target="#data-structures") }}定义了一个 `fn S(x: T) -> S` 的**构造函数**。 {{ rfc(page="1506-adt-kinds.html#tuple-structs") }} {{ esoteric() }}                                                                                                                                           |
| `const fn f() {}`                                       | 可在编译时使用的常量 `fn`，例如 `const X: u32 = f(Y);`。 {{ ref(page="const_eval.html#const-functions") }} {{ edition(ed="'18") }}                                                                                                                                                                               |
| {{ tab() }} `const { x }`                               | 在函数内部使用，确保 `{ x }` 在编译期间求值。{{ ref(page="expressions/block-expr.html#const-blocks") }}                                                                                                                                                                                                          |
| `async fn f() {}`                                       | **异步 (async)** {{ ref(page="items/functions.html#async-functions") }} {{ edition(ed="'18") }} 函数转换，{{ below(target="#async-await-101") }} 使 `f` 返回一个 `impl` **`Future`**。{{ std(page="std/future/trait.Future.html") }}                                                                             |
| {{ tab() }} `async fn f() -> S {}`                      | 同上，但使 `f` 返回一个 `impl Future<Output=S>`。                                                                                                                                                                                                                                                                |
| {{ tab() }} `async { x }`                               | 在函数内部使用，使 `{ x }` 成为一个 `impl Future<Output=X>`。{{ ref(page="expressions/block-expr.html#async-blocks") }}                                                                                                                                                                                          |
| {{ tab() }} `async move { x }`                          | 将捕获的变量移动到 future 中，类似于 move 闭包。 {{ ref(page="expressions/block-expr.html#capture-modes") }} {{ below(target="#functions-behavior") }}                                                                                                                                                           |
| `fn() -> S`                                             | **函数引用 (function references)**，<sup>1</sup> {{ book(page="ch19-05-advanced-functions-and-closures.html#function-pointers") }} {{ std(page="std/primitive.fn.html") }} {{ ref(page="types.html#function-pointer-types") }} 持有可调用实体地址的内存。                                                        |
| `Fn() -> S`                                             | **可调用 trait (callable trait)** {{ book(page="ch19-05-advanced-functions-and-closures.html#returning-closures") }} {{ std(page="std/ops/trait.Fn.html") }}（还有 `FnMut`, `FnOnce`），由闭包、函数等实现。                                                                                                     |
| `AsyncFn() -> S`                                        | **可调用异步 trait (callable async trait)** {{ std(page="std/ops/trait.AsyncFn.html") }}（还有 `AsyncFnMut`, `AsyncFnOnce`），由异步实体实现。                                                                                                                                                                   |
| <code>&vert;&vert; {} </code>                           | 一个**闭包 (closure)** {{ book(page="ch13-01-closures.html") }} {{ ex(page="fn/closures.html") }} {{ ref(page="expressions/closure-expr.html")}}，它借用其**捕获 (captures)**，{{ below(target="#closures-data") }} {{ ref(page="types/closure.html#capture-modes") }} （例如，一个局部变量）。                  |
| {{ tab() }} <code>&vert;x&vert; {}</code>               | 接受一个名为 `x` 的参数的闭包，主体是块表达式。                                                                                                                                                                                                                                                                  |
| {{ tab() }} <code>&vert;x&vert; x + x</code>            | 同上，但没有块表达式；只能由单个表达式组成。                                                                                                                                                                                                                                                                     |
| {{ tab() }} <code>move &vert;x&vert; x + y </code>      | **移动闭包 (move closure)** {{ ref(page="types/closure.html#capture-modes")}}，获取所有权；即，`y` 被转移到闭包中。                                                                                                                                                                                              |
| {{ tab() }} <code>async &vert;x&vert; x + x</code>      | **异步闭包 (async closure)**。{{ ref(page="expressions/closure-expr.html#async-closures")}} 将其结果转换为一个 `impl Future<Output=X>`。                                                                                                                                                                         |
| {{ tab() }} <code>async move &vert;x&vert; x + y</code> | **异步移动闭包 (async move closure)**。以上两者的结合。                                                                                                                                                                                                                                                          |
| {{ tab() }} <code>return &vert;&vert; true </code>      | 闭包有时看起来像逻辑或（这里：返回一个闭包）。                                                                                                                                                                                                                                                                   |
| `unsafe`                                                | 如果你喜欢调试段错误；**不安全代码 (unsafe code)**。{{ below(target="#unsafe-unsound-undefined") }} {{ book(page="ch19-01-unsafe-rust.html#unsafe-superpowers") }} {{ ex(page="unsafe.html#unsafe-operations") }} {{ nom(page="meet-safe-and-unsafe.html") }} {{ ref(page="unsafe-blocks.html#unsafe-blocks") }} |
| {{ tab() }} `unsafe fn f() {}`                          | 意味着“*调用可能导致 UB，{{ below(target="#unsafe-unsound-undefined") }} **你必须检查**前提条件*”。                                                                                                                                                                                                              |
| {{ tab() }} `unsafe trait T {}`                         | 意味着“*对 `T` 的粗心实现可能导致 UB；**实现者必须检查***”。                                                                                                                                                                                                                                                     |
| {{ tab() }} `unsafe { f(); }`                           | 向编译器保证“***我已经检查过**前提条件，相信我*”。                                                                                                                                                                                                                                                               |
| {{ tab() }} `unsafe impl T for S {}`                    | 保证*`S` 相对于 `T` 的行为是良好的*；人们可以在 `S` 上安全地使用 `T`。                                                                                                                                                                                                                                           |
| {{ tab() }} `unsafe extern "abi" {}`                    | 从 Rust 2024 开始，`extern "abi" {}` 块{{ below(target="#organizing-code")}} 必须是 `unsafe` 的。                                                                                                                                                                                                                |
| {{ tab() }} {{ tab() }} `pub safe fn f();`              | 在 `unsafe extern "abi" {}` 内部，标记 `f` 实际上可以安全调用。{{ rfc(page="3484-unsafe-extern-blocks.html") }}                                                                                                                                                                                                  |

</fixed-2-column>

<footnotes>

<sup>1</sup> 大多数文档称它们为函数**指针 (pointers)**，但函数**引用 (references)** 可能更合适{{ link(url="https://users.rust-lang.org/t/why-are-function-pointers-special-no-null/87990/16") }}，因为它们不能是 `null`，并且必须指向有效的目标。

</footnotes>

### 控制流 {#control-flow}

控制函数内的执行流程。

<fixed-2-column>

| 示例                                                                                       | 解释                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `while x {}`                                                                               | **循环 (loop)**，{{ ref(page="expressions/loop-expr.html#predicate-loops") }} 当表达式 `x` 为真时运行。                                                                                                                                                                                                                                                                                                                                                                       |
| `loop {}`                                                                                  | **无限循环** {{ ref(page="expressions/loop-expr.html#infinite-loops") }} 直到遇到 `break`。可以使用 `break x` 产生一个值。                                                                                                                                                                                                                                                                                                                                                    |
| `for x in collection {}`                                                                   | 遍历 **迭代器 (iterators)** 的语法糖。{{ book(page="ch13-02-iterators.html") }} {{ std(page="std/iter/index.html") }} {{ ref(page="expressions/loop-expr.html#iterator-loops") }}                                                                                                                                                                                                                                                                                             |
| <less-important> {{ tab() }} {{ expands_to()}}  `collection.into_iter()` </less-important> | <less-important>实际上，首先将任何 **`IntoIterator`** {{ std(page="std/iter/trait.IntoIterator.html") }} 类型转换为适当的迭代器。</less-important>                                                                                                                                                                                                                                                                                                                            |
| <less-important> {{ tab() }} {{ expands_to()}}  `iterator.next()` </less-important>        | <less-important>然后在适当的 **`Iterator`** {{ std(page="std/iter/trait.Iterator.html") }} 上 `x = next()` 直到耗尽（第一个 `None`）。</less-important>                                                                                                                                                                                                                                                                                                                       |
| `if x {} else {}`                                                                          | 当表达式为真时的**条件分支** {{ ref(page="expressions/if-expr.html") }}。                                                                                                                                                                                                                                                                                                                                                                                                     |
| `'label: {}`                                                                               | **块标签 (block label)**，{{ rfc(page="2046-label-break-value.html" )}}  可与 `break` 一起使用以退出此块。{{ edition(ed="1.65+")}}                                                                                                                                                                                                                                                                                                                                            |
| `'label: loop {}`                                                                          | 类似的**循环标签 (loop label)**，{{ ex(page="flow_control/loop/nested.html") }} {{ ref(page="expressions/loop-expr.html#loop-labels")}} 在嵌套循环中用于流控制很有用。                                                                                                                                                                                                                                                                                                        |
| `break`                                                                                    | **Break 表达式** {{ ref(page="expressions/loop-expr.html#break-expressions") }}，用于退出一个带标签的块或循环。                                                                                                                                                                                                                                                                                                                                                               |
| {{ tab() }} `break 'label x`                                                               | 从名为 `'label` 的块或循环中断出，并使其值为 `x`。                                                                                                                                                                                                                                                                                                                                                                                                                            |
| {{ tab() }} `break 'label`                                                                 | 同上，但不产生任何值。                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| {{ tab() }} `break x`                                                                      | 使 `x` 成为最内层循环的值（仅在实际的 `loop` 中）。                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `continue `                                                                                | **Continue 表达式** {{ ref(page="expressions/loop-expr.html#continue-expressions") }}，进入此循环的下一次迭代。                                                                                                                                                                                                                                                                                                                                                               |
| `continue 'label`                                                                          | 同上，但不是此循环，而是标记为 'label 的外层循环。                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `x?`                                                                                       | 如果 `x` 是 [Err](https://doc.rust-lang.org/std/result/enum.Result.html#variant.Err) 或 [None](https://doc.rust-lang.org/std/option/enum.Option.html#variant.None)，则**返回并传播**。{{ book(page="ch09-02-recoverable-errors-with-result.html#propagating-errors") }} {{ ex(page="error/result/enter_question_mark.html") }} {{ std(page="std/result/index.html#the-question-mark-operator-") }} {{ ref(page="expressions/operator-expr.html#the-question-mark-operator")}} |
| `x.await`                                                                                  | **获取 future、轮询、让出**的语法糖。{{ ref(page="expressions/await-expr.html#await-expressions") }}  {{ edition(ed="'18") }} 仅在 `async` 内部使用。                                                                                                                                                                                                                                                                                                                         |
| <less-important> {{ tab() }} {{ expands_to()}} `x.into_future()` </less-important>         | <less-important> 实际上，首先将任何 **`IntoFuture`** {{ std(page="std/future/trait.IntoFuture.html") }} 类型转换为适当的 future。</less-important>                                                                                                                                                                                                                                                                                                                            |
| <less-important> {{ tab() }} {{ expands_to()}} `future.poll()` </less-important>           | <less-important> 然后在适当的 **`Future`** {{ std(page="std/future/trait.Future.html") }} 上 `poll()`，如果为 **`Poll::Pending`**，则让出流程。{{ std(page="std/task/enum.Poll.html") }} </less-important>                                                                                                                                                                                                                                                                    |
| `return x`                                                                                 | 从函数**提前返回 (early return)** {{ ref(page="expressions/return-expr.html" ) }}。更惯用的做法是以表达式结束。                                                                                                                                                                                                                                                                                                                                                               |
| {{ tab() }} `{ return }`                                                                   | 在普通的 `{}` 块内，`return` 会退出外围函数。                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| {{ tab() }} <code>&vert;&vert; { return }</code>                                           | 在闭包内，`return` 仅退出该闭包，即闭包类似于一个函数。                                                                                                                                                                                                                                                                                                                                                                                                                       |
| {{ tab() }} `async { return }`                                                             | 在 `async` 内部，`return` **仅**{{ ref(page="expressions/block-expr.html#control-flow-operators") }} {{ bad() }} 退出该 `{}`, 即 `async {}` 类似于一个函数。                                                                                                                                                                                                                                                                                                                  |
| `f()`                                                                                      | 调用可调用实体 `f`（例如，函数、闭包、函数指针、`Fn` 等）。                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `x.f()`                                                                                    | 调用成员函数，要求 `f` 的第一个参数是 `self`、`&self` 等。                                                                                                                                                                                                                                                                                                                                                                                                                    |
| {{ tab() }} `X::f(x)`                                                                      | 与 `x.f()` 相同。除非 `impl Copy for X {}`，否则 `f` 只能调用一次。                                                                                                                                                                                                                                                                                                                                                                                                           |
| {{ tab() }} `X::f(&x)`                                                                     | 与 `x.f()` 相同。                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| {{ tab() }} `X::f(&mut x)`                                                                 | 与 `x.f()` 相同。                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| {{ tab() }} `S::f(&x)`                                                                     | 与 `x.f()` 相同，如果 `X` [解引用](https://doc.rust-lang.org/std/ops/trait.Deref.html)到 `S`，即 `x.f()` 会找到 `S` 的方法。                                                                                                                                                                                                                                                                                                                                                  |
| {{ tab() }} `T::f(&x)`                                                                     | 与 `x.f()` 相同，如果 `X impl T`，即 `x.f()` 会找到在作用域内的 `T` 的方法。                                                                                                                                                                                                                                                                                                                                                                                                  |
| `X::f()`                                                                                   | 调用关联函数，例如 `X::new()`。                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| {{ tab() }} `<X as T>::f()`                                                                | 调用为 `X` 实现的 trait 方法 `T::f()`。                                                                                                                                                                                                                                                                                                                                                                                                                                       |

</fixed-2-column>



### 代码组织 {#organizing-code}

将项目分割成更小的单元并最小化依赖。

<fixed-2-column>

| 示例                         | 解释                                                                                                                                                                                                                                                                                                                        |
| ---------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `mod m {}`                   | 定义一个**模块 (module)**，{{ book(page="ch07-02-defining-modules-to-control-scope-and-privacy.html") }} {{ ex(page="mod.html#modules") }} {{ ref(page="items/modules.html#modules") }} 从 `{}` 内部获取定义。{{ below(target="#project-anatomy") }}                                                                        |
| `mod m;`                     | 定义一个模块，从 `m.rs` 或 `m/mod.rs` 获取定义。{{ below(target="#project-anatomy") }}                                                                                                                                                                                                                                      |
| `a::b`                       | 命名空间**路径 (path)** {{ ex(page="mod/use.html") }} {{ ref(page="paths.html")}} 指向 `a`（`mod`、`enum` 等）中的元素 `b`。                                                                                                                                                                                                |
| {{ tab() }} `::b`            | 在**crate 根** {{ edition(ed="'15") }} {{ ref(page="glossary.html#crate")}} 或**外部 prelude** 中搜索 `b`；{{ edition(ed="'18") }} {{ ref(page="names/preludes.html#extern-prelude")}} **全局路径**。{{ ref(page="paths.html#path-qualifiers")}} {{ deprecated() }}                                                         |
| {{ tab() }} `crate::b`       | 在 crate 根中搜索 `b`。{{ edition(ed="'18") }}                                                                                                                                                                                                                                                                              |
| {{ tab() }} `self::b`        | 在当前模块中搜索 `b`。                                                                                                                                                                                                                                                                                                      |
| {{ tab() }} `super::b`       | 在父模块中搜索 `b`。                                                                                                                                                                                                                                                                                                        |
| `use a::b;`                  | 在此作用域内直接**使用 (use)** {{ ex(page="mod/use.html#the-use-declaration") }} {{ ref(page="items/use-declarations.html") }} `b`，不再需要 `a`。                                                                                                                                                                          |
| `use a::{b, c};`             | 同上，但将 `b` 和 `c` 引入作用域。                                                                                                                                                                                                                                                                                          |
| `use a::b as x;`             | 将 `b` 引入作用域但命名为 `x`，如 `use std::error::Error as E`。                                                                                                                                                                                                                                                            |
| `use a::b as _;`             | 将 `b` 匿名引入作用域，对于名称冲突的 trait 很有用。                                                                                                                                                                                                                                                                        |
| `use a::*;`                  | 引入 `a` 中的所有内容，仅当 `a` 是某种**prelude**时推荐使用。{{ std(page="std/prelude/index.html#other-preludes")}}  {{ link(url="https://stackoverflow.com/questions/36384840/what-is-the-prelude" ) }}                                                                                                                    |
| `pub use a::b;`              | 将 `a::b` 引入作用域并从此处重新导出。                                                                                                                                                                                                                                                                                      |
| `pub T`                      | “如果父路径是公开的，则公开”的**可见性 (visibility)** {{ book(page="ch07-02-defining-modules-to-control-scope-and-privacy.html") }} {{ ref(page="visibility-and-privacy.html")}} 作用于 `T`。                                                                                                                               |
| {{ tab() }} `pub(crate) T`   | 最多<sup>1</sup>在当前 crate 中可见。                                                                                                                                                                                                                                                                                       |
| {{ tab() }} `pub(super) T`   | 最多<sup>1</sup>在父模块中可见。                                                                                                                                                                                                                                                                                            |
| {{ tab() }} `pub(self) T`    | 最多<sup>1</sup>在当前模块中可见（默认，与没有 `pub` 相同）。                                                                                                                                                                                                                                                               |
| {{ tab() }} `pub(in a::b) T` | 最多<sup>1</sup>在祖先 `a::b` 中可见。                                                                                                                                                                                                                                                                                      |
| `extern crate a;`            | 声明对外部**crate**的依赖；{{ book(page="ch02-00-guessing-game-tutorial.html#using-a-crate-to-get-more-functionality") }} {{ ref(page="items/extern-crates.html#extern-crate-declarations") }} {{ deprecated() }} 在 {{ edition(ed="'18") }} 中只需 `use a::b`。                                                            |
| `extern "C" {}`              | *声明*来自 **FFI** 的外部依赖和 ABI（例如 `"C"`）。{{ book(page="ch19-01-unsafe-rust.html#using-extern-functions-to-call-external-code") }} {{ ex(page="std_misc/ffi.html#foreign-function-interface") }} {{ nom(page="ffi.html#calling-foreign-functions") }} {{ ref(page="items/external-blocks.html#external-blocks") }} |
| `extern "C" fn f() {}`       | *定义*一个要导出到 FFI 的函数，其 ABI 为 `"C"`。                                                                                                                                                                                                                                                                            |

</fixed-2-column>

<footnotes>

<sup>1</sup> 子模块中的项总是可以访问任何项，无论是否 `pub`。

</footnotes>


### 类型别名与转换 {#type-aliases-and-casts}

类型的简写名称，以及将一种类型转换为另一种类型的方法。

<fixed-2-column>

| 示例                           | 解释                                                                                                                                                                                                                                                                                  |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `type T = S;`                  | 创建一个**类型别名 (type alias)**，{{ book(page="ch19-04-advanced-types.html#creating-type-synonyms-with-type-aliases") }} {{ ref(page="items/type-aliases.html#type-aliases") }} 即 `S` 的另一个名称。                                                                               |
| `Self`                         | **实现类型**的类型别名，{{ ref(page="types.html#self-types") }} 例如 `fn new() -> Self`。                                                                                                                                                                                             |
| `self`                         | `fn f(self) {}` 中的**方法主语 (method subject)** {{ book(page="ch05-03-method-syntax.html#method-syntax") }} {{ ref(page="items/associated-items.html#methods")}}，类似于 `fn f(self: Self) {}`。                                                                                    |
| {{ tab() }}  `&self`           | 同上，但指代被借用的 self，等同于 `f(self: &Self)`。                                                                                                                                                                                                                                  |
| {{ tab() }}  `&mut self`       | 同上，但可变借用，等同于 `f(self: &mut Self)`。                                                                                                                                                                                                                                       |
| {{ tab() }}  `self: Box<Self>` | [**任意 self 类型 (arbitrary self type)**](https://github.com/withoutboats/rfcs/blob/arbitray-receivers/text/0000-century-of-the-self-type.md)，为智能指针添加方法（`my_box.f_of_self()`）。                                                                                          |
| `<S as T>`                     | **消除歧义 (disambiguate)** {{ book(page="ch19-03-advanced-traits.html#fully-qualified-syntax-for-disambiguation-calling-methods-with-the-same-name") }} {{ ref(page="expressions/call-expr.html#disambiguating-function-calls") }} 将类型 `S` 视为 trait `T`，例如 `<S as T>::f()`。 |
| `a::b as c`                    | 在 `use` 符号时，将 `S` 导入为 `R`，例如 `use a::S as R`。                                                                                                                                                                                                                            |
| `x as u32`                     | 原始类型**转换 (cast)**，{{ ex(page="types/cast.html#casting") }} {{ ref(page="expressions/operator-expr.html#type-cast-expressions") }} 可能会截断并有点出人意料。<sup>1</sup> {{ nom(page="casts.html") }}                                                                          |

</fixed-2-column>

<footnotes>

<sup>1</sup> 参见下文的[**类型转换**](#type-conversions)以了解所有类型之间的转换方式。

</footnotes>



### 宏与属性 {#macros-attributes}

在实际编译发生前展开的代码生成结构。

<fixed-2-column>

| 示例       | 解释                                                                                                                                                                |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `m!()`     | **宏 (macro)** {{ book(page="ch19-06-macros.html") }} {{std(page="std/index.html#macros")}} {{ ref(page="macros.html") }} 调用，也可是 `m!{}`、`m![]`（取决于宏）。 |
| `#[attr]`  | 外部**属性 (attribute)**，{{ex(page="attribute.html")}} {{ref(page="attributes.html")}} 用于注解后面的项。                                                          |
| `#![attr]` | 内部属性，用于注解*上方*的、包围的项。                                                                                                                              |

</fixed-2-column>

{{ tablesep() }}

<fixed-2-column class="color-header special_example">

| 宏内部 <sup>1</sup>   | 解释                                                                                                                                            |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| `$x:ty`               | 宏捕获，`:ty` **片段指定符 (fragment specifier)** {{ ref(page="macros-by-example.html#metavariables") }} <sup>,2</sup> 声明了 `$x` 可以是什么。 |
| `$x`                  | 宏替换，例如使用上面捕获的 `$x:ty`。                                                                                                            |
| `$(x),*`              | 宏**重复 (repetition)** {{ ref(page="macros-by-example.html#repetitions") }} *零次或多次*。                                                     |
| {{ tab() }} `$(x),+`  | 同上，但*一次或多次*。                                                                                                                          |
| {{ tab() }} `$(x)?`   | 同上，但*零次或一次*（分隔符不适用）。                                                                                                          |
| {{ tab() }} `$(x)<<+` | 实际上，除 `,` 之外的分隔符也被接受。这里是 `<<`。                                                                                              |

</fixed-2-column>

<footnotes>

<sup>1</sup> 适用于 **“示例宏 (macros by example)” **。{{ ref(page="macros-by-example.html") }} <br>
<sup>2</sup> 参见下文的[**工具指令**](#tooling-directives)以了解所有片段指定符。

</footnotes>



### 模式匹配 {#pattern-matching}

存在于 `match` 或 `let` 表达式，或函数参数中的结构。


<fixed-2-column>

| 示例                                                    | 解释                                                                                                                                                                                                                                                                        |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `match m {}`                                            | 启动**模式匹配 (pattern matching)**，{{ book(page="ch06-02-match.html") }} {{ ex(page="flow_control/match.html") }} {{ ref(page="expressions/match-expr.html") }} 然后使用匹配臂，参见下表。                                                                                |
| `let S(x) = get();`                                     | 值得注意的是，`let` 也会**解构 (destructures)** {{ ex(page="flow_control/match/destructuring.html") }}，类似于下表。                                                                                                                                                        |
| {{ tab() }} `let S { x } = s;`                          | 只有 `x` 会绑定到值 `s.x`。                                                                                                                                                                                                                                                 |
| {{ tab() }} `let (_, b, _) = abc;`                      | 只有 `b` 会绑定到值 `abc.1`。                                                                                                                                                                                                                                               |
| {{ tab() }} `let (a, ..) = abc;`                        | 忽略“其余部分”也有效。                                                                                                                                                                                                                                                      |
| {{ tab() }} `let (.., a, b) = (1, 2);`                  | 特定绑定优先于“其余部分”，这里 `a` 是 `1`，`b` 是 `2`。                                                                                                                                                                                                                     |
| {{ tab() }} `let s @ S { x } = get();`                  | 将 `s` 绑定到 `S`，同时将 `x` 绑定到 `s.x`，**模式绑定 (pattern binding)**，{{ book(page="ch18-03-pattern-syntax.html#-bindings") }} {{ ex(page="flow_control/match/binding.html#binding") }} {{ ref(page="patterns.html#identifier-patterns") }} 参见下文 {{ esoteric() }} |
| {{ tab() }} `let w @ t @ f = get();`                    | 将 `get()` 结果的 3 个副本分别存储在 `w`、`t`、`f` 中。{{ esoteric() }}                                                                                                                                                                                                     |
| {{ tab() }} <code>let (&vert;x&vert; x) = get();</code> | 病态的或模式，{{ below(target="#pattern-matching")}} **不是**闭包。{{ bad() }} 与 `let x = get();` 相同。{{ esoteric() }}                                                                                                                                                   |
| `let Ok(x) = f();`                                      | 如果模式可以被**反驳 (refuted)**，则**无法**工作 {{ bad() }}，{{ ref(page="expressions/if-expr.html#if-let-expressions") }} 请改用 `let else` 或 `if let`。                                                                                                                 |
| `let Ok(x) = f();`                                      | 但如果替代方案不可构造，则可以工作，例如 `f` 返回 `Result<T, !>` {{ edition(ed="1.82+") }}                                                                                                                                                                                  |
| `let Ok(x) = f() else {};`                              | 尝试赋值，{{ rfc(page="3137-let-else.html") }} 如果不匹配则执行 `else {}`，其中必须包含 `break`、`return`、`panic!` 等。{{ edition(ed="1.65+")}} {{ hot() }}                                                                                                                |
| `if let Ok(x) = f() {}`                                 | 如果模式可以被赋值（例如 `enum` 变体），则进入分支，是语法糖。<sup>*</sup>                                                                                                                                                                                                  |
| <code>if let &hellip; && let &hellip; { }</code>        | **Let 链**，{{ ref(page="expressions/if-expr.html#r-expr.if.chains.bindings")}} 无需嵌套即可使用多个绑定。{{ edition(ed="'24") }}                                                                                                                                           |
| `while let Ok(x) = f() {}`                              | 等效；此处持续调用 `f()`，只要模式可以被赋值，就运行 `{}`。                                                                                                                                                                                                                 |
| `fn f(S { x }: S)`                                      | 函数参数也像 `let` 一样工作，此处 `x` 绑定到 `f(s)` 的 `s.x`。{{ esoteric() }}                                                                                                                                                                                              |

</fixed-2-column>


<footnotes>

<sup>*</sup> 脱糖为 `match get() { Some(x) => {}, _ => () }`。

</footnotes>



{{ tablesep() }}

`match` 表达式中的模式匹配臂。这些臂的左侧也可以在 `let` 表达式中找到。

<fixed-2-column class="color-header special_example">

| 匹配臂内部                                               | 解释                                                                                                                                                                                                                                                         |
| -------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `E::A => {}`                                             | 匹配枚举变体 `A`，参见**模式匹配**。{{ book(page="ch06-02-match.html") }} {{ ex(page="flow_control/match.html") }} {{ ref(page="expressions/match-expr.html") }}                                                                                             |
| `E::B ( .. ) => {}`                                      | 匹配枚举元组变体 `B`，忽略任何索引。                                                                                                                                                                                                                         |
| `E::C { .. } => {}`                                      | 匹配枚举结构体变体 `C`，忽略任何字段。                                                                                                                                                                                                                       |
| `S { x: 0, y: 1 } => {}`                                 | 匹配具有特定值的结构体（仅匹配 `s.x` 为 `0` 且 `s.y` 为 `1` 的 `s`）。                                                                                                                                                                                       |
| `S { x: a, y: b } => {}`                                 | 匹配具有*任何*{{ bad() }}值的结构体，并将 `s.x` 绑定到 `a`，`s.y` 绑定到 `b`。                                                                                                                                                                               |
| {{ tab() }} `S { x, y } => {}`                           | 同上，但是简写，将 `s.x` 和 `s.y` 分别绑定为 `x` 和 `y`。                                                                                                                                                                                                    |
| `S { .. } => {}`                                         | 匹配具有任何值的结构体。                                                                                                                                                                                                                                     |
| `D => {}`                                                | 如果 `D` 在 `use` 中，则匹配枚举变体 `E::D`。                                                                                                                                                                                                                |
| `D => {}`                                                | 匹配任何东西，并绑定到 `D`；如果 `D` 不在 `use` 中，则可能是 `E::D` 的假朋友{{ bad() }}。                                                                                                                                                                    |
| `_ => {}`                                                | 正确的通配符，匹配任何东西 / “所有其余的”。                                                                                                                                                                                                                  |
| <code>0 &vert; 1 => {}</code>                            | 模式替代，**或模式 (or-patterns)**。{{ rfc( page ="2535-or-patterns.html") }}                                                                                                                                                                                |
| {{ tab() }}  <code>E::A &vert; E::Z => {}</code>         | 同上，但作用于枚举变体。                                                                                                                                                                                                                                     |
| {{ tab() }}  <code>E::C {x} &vert; E::D {x} => {}</code> | 同上，但如果所有变体都有 `x`，则绑定 `x`。                                                                                                                                                                                                                   |
| {{ tab() }}  <code>Some(A &vert; B) => {}</code>         | 同上，也可以匹配深度嵌套的替代项。                                                                                                                                                                                                                           |
| {{ tab() }}  <code>&vert;x&vert; x => {}</code>          | **病态的或模式**，{{ above(target="#pattern-matching")}}{{bad()}} 前导的 <code>&vert;</code> 被忽略，只是 <code>x &vert; x</code>，因此是 <code>x</code>。{{esoteric()}}                                                                                     |
| {{ tab() }}  <code>&vert;x => {}</code>                  | 类似地，前导的 <code>&vert;</code> 被忽略。{{esoteric() }}                                                                                                                                                                                                   |
| `(a, 0) => {}`                                           | 匹配元组，`a` 为任何值，第二个为 `0`。                                                                                                                                                                                                                       |
| `[a, 0] => {}`                                           | **切片模式**，{{ ref(page="patterns.html#slice-patterns") }} {{ link(url="https://doc.rust-lang.org/edition-guide/rust-2018/slice-patterns.html") }} 匹配数组，`a` 为任何值，第二个为 `0`。                                                                  |
| {{ tab() }} `[1, ..] => {}`                              | 匹配以 `1` 开头的数组，其余为任何值；**子切片模式 (subslice pattern)**。{{ ref(page="patterns.html#rest-patterns") }} {{ rfc(page="2359-subslice-pattern-syntax.html") }}                                                                                    |
| {{ tab() }} `[1, .., 5] => {}`                           | 匹配以 `1` 开头，以 `5` 结尾的数组。                                                                                                                                                                                                                         |
| {{ tab() }} `[1, x @ .., 5] => {}`                       | 同上，但也将 `x` 绑定到表示中间部分的切片（参见模式绑定）。                                                                                                                                                                                                  |
| {{ tab() }} `[a, x @ .., b] => {}`                       | 同上，但匹配任何第一个、最后一个，并分别绑定为 `a`、`b`。                                                                                                                                                                                                    |
| `1 .. 3 => {}`                                           | **范围模式**，{{ book(page="ch18-03-pattern-syntax.html#matching-ranges-of-values-with-") }} {{ ref(page="patterns.html#range-patterns") }} 此处匹配 `1` 和 `2`；部分不稳定。{{ experimental() }}                                                            |
| {{ tab() }} `1 ..= 3 => {}`                              | 包含范围模式，匹配 `1`、`2` 和 `3`。                                                                                                                                                                                                                         |
| {{ tab() }} `1 .. => {}`                                 | 开放范围模式，匹配 `1` 和任何更大的数。                                                                                                                                                                                                                      |
| `x @ 1..=5 => {}`                                        | 将匹配项绑定到 `x`；**模式绑定**，{{ book(page="ch18-03-pattern-syntax.html#-bindings") }} {{ ex(page="flow_control/match/binding.html#binding") }} {{ ref(page="patterns.html#identifier-patterns") }} 此处 `x` 将是 `1` &hellip; `5`。                     |
| {{ tab() }} `Err(x @ Error {..}) => {}`                  | 也适用于嵌套，此处 `x` 绑定到 `Error`，在下面与 `if` 一起使用时特别有用。                                                                                                                                                                                    |
| `S { x } if x > 10 => {}`                                | 模式**匹配守卫 (match guards)**，{{ book(page="ch18-03-pattern-syntax.html#extra-conditionals-with-match-guards")}} {{ ex(page="flow_control/match/guard.html#guards")}} {{ ref(page="expressions/match-expr.html#match-guards") }} 条件也必须为真才能匹配。 |

</fixed-2-column>

### 泛型与约束 {#generics-constraints}

泛型与类型构造器、trait 和函数相结合，为您的用户提供更大的灵活性。

<fixed-2-column>

| 示例                                    | 解释                                                                                                                                                                                                                                                                                                           |
| --------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `struct S<T> …`                         | 带有类型参数（此处 `T` 是占位符）的**泛型 (generic)** {{ book(page="ch10-01-syntax.html") }} {{ ex(page="generics.html") }} 类型。                                                                                                                                                                             |
| `S<T> where T: R`                       | **Trait 约束 (trait bound)**，{{ book(page="ch10-02-traits.html#using-trait-bounds-to-conditionally-implement-methods") }} {{ ex(page="generics/bounds.html") }} {{ ref(page="trait-bounds.html#trait-and-lifetime-bounds" ) }} 限制允许的 `T`，保证 `T` 具有 trait `R`。                                      |
| {{ tab() }} `where T: R, P: S`          | **独立的 trait 约束**，此处一个用于 `T`，一个用于（未显示的）`P`。                                                                                                                                                                                                                                             |
| {{ tab() }} `where T: R, S`             | 编译错误，{{ bad() }} 您可能想要下面的复合约束 `R + S`。                                                                                                                                                                                                                                                       |
| {{ tab() }} `where T: R + S`            | **复合 trait 约束 (compound trait bound)**，{{ book(page="ch10-02-traits.html#specifying-multiple-trait-bounds-with-the--syntax") }} {{ ex(page="generics/multi_bounds.html") }} `T` 必须同时满足 `R` 和 `S`。                                                                                                 |
| {{ tab() }} `where T: R + 'a`           | 同上，但带有生命周期。`T` 必须满足 `R`，如果 `T` 有生命周期，则必须比 `'a` 活得长。                                                                                                                                                                                                                            |
| {{ tab() }} `where T: ?Sized`           | 选择退出一个预定义的 trait 约束，此处是 `Sized`。{{ todo() }}                                                                                                                                                                                                                                                  |
| {{ tab() }} `where T: 'a`               | 类型**生命周期约束 (lifetime bound)**；{{ ex(page="scope/lifetime/lifetime_bounds.html") }} 如果 T 有引用，它们必须比 `'a` 活得长。                                                                                                                                                                            |
| {{ tab() }} `where T: 'static`          | 同上；并*不*意味着值 `t` *将*{{ bad() }}活 `'static`，只意味着它*可以*。                                                                                                                                                                                                                                       |
| {{ tab() }} `where 'b: 'a`              | 生命周期 `'b` 必须至少活得和（即*超过*）`'a` 一样长。                                                                                                                                                                                                                                                          |
| {{ tab() }} `where u8: R<T>`            | 也可以创建涉及*其他*类型的条件语句。{{ esoteric() }}                                                                                                                                                                                                                                                           |
| `S<T: R>`                               | 简写约束，几乎与上面相同，写起来更短。                                                                                                                                                                                                                                                                         |
| `S<const N: usize>`                     | **泛型常量约束 (generic const bound)**；{{ ref(page="items/generics.html#const-generics") }} 类型 `S` 的用户可以提供常量值 `N`。                                                                                                                                                                               |
| {{ tab() }} `S<10>`                     | 在使用时，常量约束可以作为原始值提供。                                                                                                                                                                                                                                                                         |
| {{ tab() }} `S<{5+5}>`                  | 表达式必须放在花括号中。                                                                                                                                                                                                                                                                                       |
| `S<T = R>`                              | **默认参数**；{{ book(page="ch19-03-advanced-traits.html#default-generic-type-parameters-and-operator-overloading") }} 使 `S` 更易于使用，但保持了灵活性。                                                                                                                                                     |
| {{ tab() }} `S<const N: u8 = 0>`        | 常量的默认参数；例如，在 `f(x: S) {}` 中参数 `N` 为 `0`。                                                                                                                                                                                                                                                      |
| {{ tab() }} `S<T = u8>`                 | 类型的默认参数，例如，在 `f(x: S) {}` 中参数 `T` 为 `u8`。                                                                                                                                                                                                                                                     |
| `S<'_>`                                 | 推断的**匿名生命周期**；要求编译器在明显的情况下 *“自己搞定”*。                                                                                                                                                                                                                                                |
| `S<_>`                                  | 推断的**匿名类型**，例如 `let x: Vec<_> = iter.collect()`                                                                                                                                                                                                                                                      |
| `S::<T>`                                | **Turbofish** {{ std(page="std/iter/trait.Iterator.html#method.collect")}} 调用点类型消歧，例如 `f::<u32>()`。                                                                                                                                                                                                 |
| {{ tab() }} `E::<T>::A`                 | 泛型枚举可以在其类型 `E` 上接收其类型参数 &hellip;                                                                                                                                                                                                                                                             |
| {{ tab() }} `E::A::<T>`                 | &hellip; 或在变体上（此处为 `A`）；允许 `Ok::<R, E>(r)` 等。                                                                                                                                                                                                                                                   |
| `trait T<X> {}`                         | 一个泛型于 `X` 的 trait。可以有多个 `impl T for S`（每个 `X` 一个）。                                                                                                                                                                                                                                          |
| `trait T { type X; }`                   | 定义**关联类型 (associated type)** {{ book(page="ch19-03-advanced-traits.html#specifying-placeholder-types-in-trait-definitions-with-associated-types") }} {{ ref(page="items/associated-items.html#associated-types") }} {{ rfc(page="0195-associated-items.html") }} `X`。只有一个 `impl T for S` 是可能的。 |
| `trait T { type X<G>; }`                | 定义**泛型关联类型 (GAT)**，{{ rfc(page="1598-generic_associated_types.html") }} `X` 可以是泛型的 `Vec<>`。                                                                                                                                                                                                    |
| `trait T { type X<'a>; }`               | 定义一个泛型于生命周期的 GAT。                                                                                                                                                                                                                                                                                 |
| {{ tab() }} `type X = R;`               | 在 `impl T for S { type X = R; }` 中设置关联类型。                                                                                                                                                                                                                                                             |
| {{ tab() }} `type X<G> = R<G>;`         | GAT 同样，例如 `impl T for S { type X<G> = Vec<G>; }`。                                                                                                                                                                                                                                                        |
| `impl<T> S<T> {}`                       | **泛型地**为 `S<T>` 中的任何 `T` 实现 `fn`，{{ ref(page="items/implementations.html#generic-implementations") }} 此处 `T` 是类型参数。                                                                                                                                                                         |
| `impl S<T> {}`                          | **固有地**为精确的 `S<T>` 实现 `fn`，{{ ref(page="items/implementations.html#inherent-implementations") }} 此处 `T` 是特定类型，例如 `u8`。                                                                                                                                                                    |
| `fn f() -> impl T`                      | **存在类型 (existential types)**（又名 [_RPIT_](https://santiagopastorino.com/2022/10/20/what-rpits-rpitits-and-afits-and-their-relationship/)），{{ book(page="ch10-02-traits.html#returning-types-that-implement-traits") }} 返回一个调用者未知的、`impl T` 的 `S`。                                         |
| {{ tab() }} `-> impl T + 'a`            | 表明隐藏类型至少活得和 `'a` 一样长。{{ rfc(page="3498-lifetime-capture-rules-2024.html#capturing-lifetimes") }}                                                                                                                                                                                                |
| {{ tab() }} `-> impl T + use<'a>`       | 反而表明隐藏类型捕获了生命周期 `'a`，**使用约束 (use bound)**。{{ link(url="https://blog.rust-lang.org/2024/09/05/impl-trait-capture-rules.html") }} {{ todo() }}                                                                                                                                              |
| {{ tab() }} `-> impl T + use<'a, R>`    | 也表明隐藏类型可能从 `R` 捕获了生命周期。                                                                                                                                                                                                                                                                      |
| {{ tab() }} `-> S<impl T>`              | `impl T` 部分也可以在类型参数内部使用。                                                                                                                                                                                                                                                                        |
| `fn f(x: &impl T)`                      | 通过“**impl traits**”的 trait 约束，{{ book(page="ch10-02-traits.html#trait-bound-syntax") }} 类似于下面的 `fn f<S: T>(x: &S)`。                                                                                                                                                                               |
| `fn f(x: &dyn T)`                       | 通过 **动态分发 (dynamic dispatch)** 调用 `f`，{{ book(page="ch17-02-trait-objects.html#using-trait-objects-that-allow-for-values-of-different-types") }} {{ ref(page="types.html#trait-objects") }} `f` 将不会为 `x` 实例化。                                                                                 |
| `fn f<X: T>(x: X)`                      | 函数泛型于 `X`，`f` 将为每个 `X` 实例化（‘[单态化](https://en.wikipedia.org/wiki/Monomorphization)’）。                                                                                                                                                                                                        |
| `fn f() where Self: R;`                 | 在 `trait T {}` 中，使 `f` 仅在已知也 `impl R` 的类型上可访问。                                                                                                                                                                                                                                                |
| {{ tab() }} `fn f() where Self: Sized;` | 使用 `Sized` 可以使 `f` 不进入 trait 对象的虚函数表，从而启用 `dyn T`。                                                                                                                                                                                                                                        |
| {{ tab() }} `fn f() where Self: R {}`   | 其他 `R` 在默认函数中有用（非默认的反正也需要实现）。                                                                                                                                                                                                                                                          |
</fixed-2-column>



### 高阶项 {{ esoteric() }} {#higher-ranked-items}

*实际的*类型和 trait，对某些东西进行抽象，通常是生命周期。

<fixed-2-column>

| 示例                                    | 解释                                                                                                                                                                                         |
| --------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `for<'a>`                               | **高阶约束 (higher-ranked bounds)** 的标记。{{ nom(page="hrtb.html")}} {{ ref(page="trait-bounds.html#higher-ranked-trait-bounds")}} {{ esoteric() }}                                        |
| {{ tab() }} `trait T: for<'a> R<'a> {}` | 任何 `impl T` 的 `S` 都必须对任何生命周期满足 `R`。                                                                                                                                          |
| `fn(&'a u8)`                            | 函数指针类型，持有可使用**特定**生命周期 `'a` 调用的函数。                                                                                                                                   |
| `for<'a> fn(&'a u8)`                    | **高阶类型**<sup>1</sup> {{ link(url="https://github.com/rust-lang/rust/issues/56105") }}，持有可使用**任何**生命周期调用的函数；是上述类型的子类型{{ below(target="#type-conversions") }}。 |
| {{ tab() }} `fn(&'_ u8)`                | 同上；自动展开为类型 `for<'a> fn(&'a u8)`。                                                                                                                                                  |
| {{ tab() }} `fn(&u8)`                   | 同上；自动展开为类型 `for<'a> fn(&'a u8)`。                                                                                                                                                  |
| `dyn for<'a> Fn(&'a u8)`                | 高阶（trait 对象）类型，工作方式类似于上面的 `fn`。                                                                                                                                          |
| {{ tab() }} `dyn Fn(&'_ u8)`            | 同上；自动展开为类型 `dyn for<'a> Fn(&'a u8)`。                                                                                                                                              |
| {{ tab() }} `dyn Fn(&u8)`               | 同上；自动展开为类型 `dyn for<'a> Fn(&'a u8)`。                                                                                                                                              |

<footnotes>

 <sup>1</sup> 是的，`for<>` 是类型的一部分，这就是为什么下面要写 `impl T for for<'a> fn(&'a u8)`。

</footnotes>

</fixed-2-column>


<div class="color-header special_example">
{{ tablesep() }}

| 实现 Trait                          | 解释                                                               |
| ----------------------------------- | ------------------------------------------------------------------ |
| `impl<'a> T for fn(&'a u8) {}`      | 对于函数指针，当调用接受**特定**生命周期 `'a` 时，实现 trait `T`。 |
| `impl T for for<'a> fn(&'a u8) {}`  | 对于函数指针，当调用接受**任何**生命周期时，实现 trait `T`。       |
| {{ tab() }} `impl T for fn(&u8) {}` | 同上，简写版本。                                                   |

</div>


### 字符串与字符 {#strings-chars}

Rust 有多种方式创建文本值。


<fixed-2-column>

| 示例                       | 解释                                                                                                                                                                                                   |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `"..."`                    | **字符串字面量 (string literal)**，{{ ref(page="tokens.html#string-literals")}}<sup>, 1</sup> 一个 UTF-8 的 `&'static str`，{{ std(page="std/primitive.str.html") }} 支持以下转义：                    |
| {{ tab() }} `"\n\r\t\0\\"` | **常见转义** {{ ref(page="tokens.html#ascii-escapes") }}，例如 `"\n"` 变成*换行符*。                                                                                                                   |
| {{ tab() }} `"\x36"`       | **ASCII 转义** {{ ref(page="tokens.html#ascii-escapes") }}，最高到 `7f`，例如 `"\x36"` 会变成 `6`。                                                                                                    |
| {{ tab() }} `"\u{7fff}"`   | **Unicode 转义** {{ ref(page="tokens.html#unicode-escapes") }}，最多 6 位，例如 `"\u{7fff}"` 变成 `翿`。                                                                                               |
| `r"..."`                   | **原始字符串字面量 (raw string literal)**。{{ ref(page="tokens.html#raw-string-literals")}}<sup>, 1</sup> UTF-8，但不会解释上面的任何转义。                                                            |
| `r#"..."#`                 | 原始字符串字面量，UTF-8，但也可以包含 `"`。`#` 的数量可以变化。                                                                                                                                        |
| `c"..."`                   | **C 字符串字面量 (C string literal)**，{{ ref(page="tokens.html#c-string-literals")}} 一个以 NUL 结尾的 `&'static CStr`，{{ std(page="std/ffi/struct.CStr.html") }} 用于 FFI。{{ edition(ed="1.77+")}} |
| `cr"..."`, `cr#"..."#`     | 原始 C 字符串字面量，是上述的类似组合。                                                                                                                                                                |
| `b"..."`                   | **字节字符串字面量 (byte string literal)**；{{ ref(page="tokens.html#byte-and-byte-string-literals")}}<sup>, 1</sup> 构造一个只含 ASCII 的 `&'static [u8; N]`。                                        |
| `br"..."`, `br#"..."#`     | 原始字节字符串字面量，是上述的类似组合。                                                                                                                                                               |
| `b'x'`                     | ASCII **字节字面量 (byte literal)**，{{ ref(page="tokens.html#byte-literals")}} 一个单独的 `u8` 字节。                                                                                                 |
| `'🦀'`                      | **字符字面量 (character literal)**，{{ ref(page="tokens.html#character-and-string-literals")}} 一个固定 4 字节的 Unicode **'char'**。{{ std(page="std/primitive.char.html") }}                         |

<footnotes>

<sup>1</sup> 支持多行。只需记住 `Debug`{{ below(target="#string-output") }}（例如 `dbg!(x)` 和 `println!("{x:?}")`）可能会将其渲染为 `\n`，而 `Display`{{ below(target="#string-output") }}（例如 `println!("{x}")`）会*正确地*渲染它。

</footnotes>


</fixed-2-column>



### 文档 {#documentation}

调试器都恨他。用这个奇怪的技巧避免 bug。


<fixed-2-column>

| 示例       | 解释                                                                                                                                                                                                                                                 |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `///`      | 外部行**文档注释**，<sup>1</sup> {{ book(page="ch14-02-publishing-to-crates-io.html#making-useful-documentation-comments") }} {{ ex(page="meta/doc.html#documentation") }} {{ ref(page="comments.html#doc-comments")}} 在类型、trait、函数等上使用。 |
| `//!`      | 内部行文档注释，主要用于文件顶部。                                                                                                                                                                                                                   |
| `//`       | 行注释，用于记录代码流程或*内部实现*。                                                                                                                                                                                                               |
| `/* … */`  | 块注释。<sup>2</sup> {{ deprecated() }}                                                                                                                                                                                                              |
| `/** … */` | 外部块文档注释。<sup>2</sup> {{ deprecated() }}                                                                                                                                                                                                      |
| `/*! … */` | 内部块文档注释。<sup>2</sup> {{ deprecated() }}                                                                                                                                                                                                      |

</fixed-2-column>

<footnotes>

<sup>1</sup> [工具指令](#tooling-directives)概述了您可以在文档注释中做什么。<br>
<sup>2</sup> 由于用户体验不佳，通常不鼓励使用。如果可能，请使用等效的行注释并利用 IDE 支持。

</footnotes>



### 杂项 {#miscellaneous}

这些符号不适合任何其他类别，但了解它们仍然很有用。

<fixed-2-column>

| 示例                                     | 解释                                                                                                                                                                                                                                                 |
| ---------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `!`                                      | 总是为空的**never 类型**。{{ book(page="ch19-04-advanced-types.html#the-never-type-that-never-returns") }} {{ ex(page="fn/diverging.html#diverging-functions") }} {{ std(page="std/primitive.never.html") }} {{ ref(page="types.html#never-type") }} |
| {{ tab() }} `fn f() -> ! {}`             | 永不返回的函数；与任何类型兼容，例如 `let x: u8 = f();`                                                                                                                                                                                              |
| {{ tab() }} `fn f() -> Result<(), !> {}` | 必须返回 `Result` 但表明它永远不会 `Err` 的函数。{{ experimental() }}                                                                                                                                                                                |
| {{ tab() }} `fn f(x: !) {}`              | 存在但永远不能被调用的函数。不太有用。{{ esoteric() }} {{ experimental() }}                                                                                                                                                                          |
| `_`                                      | 未命名的**通配符**{{ ref(page="patterns.html#wildcard-pattern")}}变量绑定，例如 <code>&vert;x, _&vert; {}</code>。                                                                                                                                   |
| {{ tab() }} `let _ = x;`                 | 未命名赋值是空操作，**不会**{{ bad() }}移出 `x` 或保留作用域！                                                                                                                                                                                       |
| {{ tab() }} `_ = x;`                     | 你可以将*任何东西*赋值给 `_` 而无需 `let`，即 `_ = ignore_rval();` {{ hot() }}                                                                                                                                                                       |
| `_x`                                     | 不会产生*未使用变量*警告的变量绑定。                                                                                                                                                                                                                 |
| `1_234_567`                              | 用于视觉清晰度的数字分隔符。                                                                                                                                                                                                                         |
| `1_u8`                                   | **数字字面量**的类型指定符{{ ex(page="types/literals.html#literals") }} {{ ref(page="tokens.html#number-literals") }}（也可是 `i8`、`u16` 等）。                                                                                                     |
| `0xBEEF`, `0o777`, `0b1001`              | 十六进制（`0x`）、八进制（`0o`）和二进制（`0b`）整数字面量。                                                                                                                                                                                         |
| `12.3e4`, `1E-8`                         | 浮点数字面量的**科学记数法**。{{ref(page="tokens.html#floating-point-literals")}}                                                                                                                                                                    |
| `r#foo`                                  | 用于版本兼容性的**原始标识符 (raw identifier)** {{ book(page="appendix-01-keywords.html#raw-identifiers") }} {{ ex(page="compatibility/raw_identifiers.html#raw-identifiers") }}。{{ esoteric() }}                                                   |
| `'r#a`                                   | 用于版本兼容性的**原始生命周期标签 (raw lifetime label)** {{ todo() }}。{{ esoteric() }}                                                                                                                                                             |
| `x;`                                     | **语句 (statement)** {{ ref(page="statements.html")}} 终止符，区别于**表达式 (expressions)** {{ ex(page="expression.html") }} {{ ref(page="expressions.html")}}                                                                                      |

</fixed-2-column>




### 常见运算符

Rust 支持您所期望的大多数运算符（`+`, `*`, `%`, `=`, `==` 等），包括**重载**。{{ std(page="std/ops/index.html")}} 由于它们在 Rust 中的行为没有不同，我们在此不列出它们。


---

<magic>

# 幕后探秘

可能会对你的心智造成可怕影响的神秘知识，强烈推荐。

## 抽象机 {#the-abstract-machine}

与 `C` 和 `C++` 一样，Rust 基于一个*抽象机*。


<tabs>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-abstract-machine-1" name="tab-group-abstract-machine" checked>
<label for="tab-abstract-machine-1"><b>概述</b></label>
<panel><div>


<div style="text-align: center;">

<mini-zoo class="zoo" style="text-align: center;">
    <entry>
        <machine class="bad">Rust</machine>
    </entry>
    <code style="text-align:center;">→</code>
    <entry>
        <machine class="bad">CPU</machine>
    </entry>
    <br/>
    <note>{{bad()}} 误导性的。</note>
</mini-zoo>

<mini-zoo class="zoo" style="text-align: center; margin-left: 80px;">
    <entry>
        <machine class="good">Rust</machine>
    </entry>
    <code style="text-align:center">→</code>
    <entry style="width: 120px;">
        <machine class="good">抽象机</machine>
    </entry>
    <code style="text-align:center">→</code>
    <entry>
        <machine class="good">CPU</machine>
    </entry>
    <br/>
    <note>正确的。</note>
</mini-zoo>

</div>

{{ tablesep() }}

除了极少数例外，你永远不被“允许”去思考实际的 CPU。你是在为一个*抽象的* CPU 编写代码。然后 Rust（在某种程度上）理解你想要什么，并将其转换为实际的 RISC-V / x86 / … 机器码。


{{ tablesep() }}


这个*抽象机*
- 不是一个运行时，也没有任何运行时开销，而是一个*计算模型抽象*，
- 包含诸如内存区域（*栈*等）、执行语义等概念，
- *知道*并*看到*你的 CPU 可能不关心的东西，
- 实际上是你和编译器之间的契约，
- 并**利用以上所有特性进行优化**。


</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-abstract-machine-2" name="tab-group-abstract-machine">
<label for="tab-abstract-machine-2"><b>误解</b></label>
<panel><div>

<div class="color-header abstract-machine">

左边是人们可能错误地认为如果 Rust 直接面向 CPU *应该能侥幸成功*的事情。右边是如果你违反了抽象机（AM）的契约，实际上会干扰到的事情。

{{ tablesep() }}

| 没有 AM                                          | 有 AM                                                                                          |
| ------------------------------------------------ | ---------------------------------------------------------------------------------------------- |
| `0xffff_ffff` 会是一个有效的 `char`。{{ bad() }} | AM 可能会利用 *“无效”* 的位模式来打包不相关的数据。                                            |
| `0xff` 和 `0xff` 是相同的指针。{{ bad() }}       | AM 的指针可以有**来源 (provenance)** {{ std(page="std/ptr/index.html#provenance")}} 用于优化。 |
| 对指针 `0xff` 的任何读/写总是没问题。{{ bad() }} | AM 可能会发出缓存友好的操作，因为 *“不可能有读取”* 。                                          |
| 读取未初始化的内存只会得到随机值。{{ bad() }}    | AM *“知道”* 读取不可能，可能会移除所有相关代码。                                               |
| 数据竞争只会得到随机值。{{ bad() }}              | AM 可能会拆分读/写，产生*不可能*的值。{{ below(target="#atomics-cache") }}                     |
| 空引用只是某个寄存器中的 `0x0`。{{ bad() }}      | 在引用中持有 `0x0` 会召唤克苏鲁。                                                              |

{{ tablesep() }}

> 这个表格只是为了概述 AM 的作用。与 C 或 C++ 不同，Rust 永远不会让你做错事，除非你用 `unsafe` 强制它。{{ below(target="#unsafe-unsound-undefined") }}

</div>
</div></panel></tab>


</tabs>

<!--  -->
<!-- > Practically this means: -->
<!-- > - before assuming your **CPU** will do `A` when writing `B` you need positive proof **via documentation**(!), -->
<!-- > - if you don't have that any physical behavior is _coincidental_, -->
<!-- > - violate the abtract machine's contract and the optimizer makes your CPU do something **entirely else** &mdash; **undefined behavior**.{{ below(target="#unsafe-unsound-undefined")}} -->
<!--  -->


## 语法糖 {#language-sugar}

如果有些事情“在你仔细思考后觉得不应该能工作”但它却能工作，那可能就是因为下面这些原因之一。


<div class="color-header language-sugar">


| 名称                                                                                                                                                                                                                   | 描述                                                                                                                                       |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| **类型强制转换 (Coercions)** {{ nom(page="coercions.html") }}                                                                                                                                                          | *弱化*类型以匹配签名，例如，`&mut T` 转为 `&T`；参见*类型转换* {{ below(target="#type-conversions") }}                                     |
| **解引用 (Deref)** {{ nom(page="vec-deref.html") }} {{ link(url="https://stackoverflow.com/questions/28519997/what-are-rusts-exact-auto-dereferencing-rules") }}                                                       | [解引用](https://doc.rust-lang.org/std/ops/trait.Deref.html) `x: T` 直到 `*x`, `**x`, &hellip; 与某个目标 `S` 兼容。                       |
| **预导入 (Prelude)** {{ std(page="std/prelude/index.html") }}                                                                                                                                                          | 自动导入基本项，例如 `Option`, `drop()`, …                                                                                                 |
| **重新借用 (Reborrow)** {{ link(url="https://quinedot.github.io/rust-learning/st-reborrow.html") }}                                                                                                                    | 由于 `x: &mut T` 不能被复制；因此移动一个新的 `&mut *x` 来代替。                                                                           |
| **生命周期省略 (Lifetime Elision)** {{ book(page="ch10-03-lifetime-syntax.html#lifetime-elision") }} {{ nom(page="lifetime-elision.html#lifetime-elision") }} {{ ref(page="lifetime-elision.html#lifetime-elision") }} | 允许你写 `f(x: &T)`，而不是 `f<'a>(x: &'a T)`，以求简洁。                                                                                  |
| **生命周期扩展 (Lifetime Extensions)** {{ link(url="https://blog.m-ou.se/super-let/") }}  {{ ref(page="destructors.html#temporary-lifetime-extension") }}                                                              | 在 `let x = &tmp().f` 和类似情况下，将临时值保留到该行之后。                                                                               |
| **方法解析 (Method Resolution)** {{ ref(page="expressions/method-call-expr.html") }}                                                                                                                                   | 解引用或借用 `x` 直到 `x.f()` 工作。                                                                                                       |
| **匹配人体工程学 (Match Ergonomics)** {{ rfc(page="2005-match-ergonomics.html") }}                                                                                                                                     | 重复解引用[被匹配表达式 (scrutinee)](https://doc.rust-lang.org/stable/reference/glossary.html#scrutinee) 并向绑定添加 `ref` 和 `ref mut`。 |
| **右值静态提升 (Rvalue Static Promotion)** {{ rfc(page="1414-rvalue_static_promotion.html") }}  {{ esoteric() }}                                                                                                       | 使对常量的引用变为 `'static`，例如 `&42`, `&None`, `&mut []`。                                                                             |
| **双重定义 (Dual Definitions)** {{ rfc(page="1506-adt-kinds.html#tuple-structs") }} {{ esoteric() }}                                                                                                                   | 定义一个（例如 `struct S(u8)`）会隐式定义另一个（例如 `fn S`）。                                                                           |
| **Drop 隐藏流 (Drop Hidden Flow)** {{ ref(page="destructors.html") }} {{ esoteric() }}                                                                                                                                 | 在块 `{ ... }` 结束或 `_` 赋值时，可能会调用 `T::drop()`。{{ std(page="std/ops/trait.Drop.html") }}                                        |
| **Drop 不可调用 (Drop Not Callable)** {{ std(page="std/ops/trait.Drop.html") }} {{ esoteric() }}                                                                                                                       | 编译器禁止显式调用 `T::drop()`，必须使用 `mem::drop()`。{{ std(page="std/mem/fn.drop.html") }}                                             |
| **自动 Trait (Auto Traits)** {{ ref(page="special-types-and-traits.html#auto-traits") }}                                                                                                                               | 如果可能，总是为你的类型、闭包、future 实现。                                                                                              |


</div>

{{ tablesep() }}

> **个人观点** {{ opinionated() }} &mdash; 这些特性让你*使用* Rust 更容易，但却阻碍了你*学习*它。如果你想建立*真正的理解*，花些额外的时间去探索它们。


## 内存与生命周期 {#memory-lifetimes}


一个关于移动、引用和生命周期的图文指南。


<tabs class="lifetimes">

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-lt-1" name="tab-lt" checked>
<label for="tab-lt-1"><b>类型与移动</b></label>
<panel>
<div>


<lifetime-section>
<lifetime-example>
    <section-header>应用程序内存</section-header>
    <memory-row>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2 hide" style="left: 57px;">S(1)</value>
        </values>
        <labels>
            <label class="" style="right: 10px;">&nbsp;</label>
        </labels>
        <subtext>应用程序内存</subtext>
    </memory-row>
</lifetime-example>
<explanation>

- 在底层，应用程序内存只是一组字节数组。
- 运行环境通常会将其分段，其中包括：
    - **栈 (stack)**（小而低开销的内存，<sup>1</sup> 大多数*变量*放在这里），
    - **堆 (heap)**（大而灵活的内存，但总是通过像 `Box<T>` 这样的栈代理来处理），
    - **静态区 (static)**（最常用作 `&str` 中 `str` 部分的存放地），
    - **代码区 (code)**（你的函数二进制码所在的地方）。
- 最棘手的部分与**栈如何演变**有关，这是**我们的重点**。

<footnotes>

<sup>1</sup> 对于固定大小的值，栈的管理非常简单：*在你需要时多拿几个字节，一旦你离开就丢弃*。然而，向这些*短暂的*位置分发指针，正是*生命周期*存在的本质；也是本章其余部分的主题。

</footnotes>

</explanation>
</lifetime-section>



<lifetime-section>
<lifetime-example class="not-first">
    <section-header>变量</section-header>
    <memory-row>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2 hide" style="left: 57px;">S(1)</value>
            <value class="t byte2" style="left: 97.5px;">S(1)</value>
        </values>
        <labels>
            <label class="byte2 hide" style="left: 57px;"><code>a</code></label>
            <label class="byte2" style="left: 97.5px;"><code>t</code></label>
        </labels>
        <subtext>变量</subtext>
        <!-- <subtext><code>let t = S(1);</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
let t = S(1);
```

- 保留一个名为 `t` 的内存位置，其类型为 `S`，里面存储的值为 `S(1)`。
- 如果用 `let` 声明，该位置存在于栈上。<sup>1</sup>
- 注意**语言上的模糊性**，在术语**_变量_**中，它可以指：
    1. 源文件中位置的**名称**（“重命名那个变量”），
    1. 编译后应用中的**位置**，`0x7`（“告诉我那个变量的地址”），
    1. 其中包含的**值**，`S(1)`（“给那个变量加一”）。
- 特别地，对于编译器，`t` 可以表示 **`t` 的位置**，这里是 `0x7`，和 **`t` 内的值**，这里是 `S(1)`。

<footnotes>

<sup>1</sup> 参见上文，{{ above(target="#data-structures" ) }} 对于完全同步的代码是真的，但 `async` 栈帧可能会通过运行时将其放在堆上。

</footnotes>


</explanation>
</lifetime-section>


<lifetime-section>
<lifetime-example class="not-first">
    <section-header>移动语义</section-header>
    <memory-row>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2" style="left: 57px;">S(1)</value>
        </values>
        <labels>
            <label class="byte2" style="left: 57px;"><code>a</code></label>
            <label class="byte2" style="left: 97.5px;"><code>t</code></label>
        </labels>
        <subtext>移动</subtext>
        <!-- <subtext><code>let a = t;</code></subtext> -->
    </memory-row>
</lifetime-example>

<explanation>

```
let a = t;
```

- 这将**移动** `t` 内的值到 `a` 的位置，如果 `S` 是 `Copy` 类型，则会复制它。
- 移动后，位置 `t` **无效**，不能再被读取。
    - 技术上讲，该位置的位并不是真的*空的*，而是*未定义的*。
    - 如果你仍然可以（通过 `unsafe`）访问 `t`，它们可能仍然*看起来*像有效的 `S`，但
    任何试图将它们用作有效 `S` 的尝试都是未定义行为。{{ below(target="#unsafe-unsound-undefined") }}
- 我们在这里不明确讨论 `Copy` 类型。它们会稍微改变规则，但不多：
    - 它们不会被 drop。
    - 它们永远不会留下一个“空的”变量位置。

</explanation>
</lifetime-section>



<lifetime-section>
<lifetime-example class="not-first">
    <section-header>类型安全</section-header>
    <memory-row>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <failed style="left: 231.5px;"><value class="atomic byte4">M { … }</value></failed>
            <denied style="left: 141px;">⛔</denied>
        </values>
        <labels>
            <label class="byte2" style="left: 57px;"><code></code></label>
            <label class="byte2" style="left: 170px;"><code>c</code></label>
        </labels>
        <subtext>类型安全</subtext>
        <!-- <subtext><code>let c: S = M::new();</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>


```
let c: S = M::new();
```

- **变量的类型**有几个重要的作用，它：
    1. 规定了底层位应该如何被解释，
    1. 只允许对这些位进行定义良好的操作，
    1. 防止随机的其他值或位被写入该位置。
- 这里赋值编译失败，因为 `M::new()` 的字节不能被转换为 `S` 类型的形式。
- **类型之间的转换通常总是会失败**，**除非有明确的规则允许**（强制转换、类型转换等）。

</explanation>
</lifetime-section>


<lifetime-section>
<lifetime-example class="not-first">
    <section-header>作用域与 Drop</section-header>
    <memory-row>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <drop><value class="t byte2" style="left: 57px;">S(1)</value><droparrow style="left:37px;">▼</droparrow></drop>
            <value class="t byte2 hide" style="left: 87.5px;">C(2)</value>
            <drop><value class="t byte2" style="left: 128px;">S(2)</value><droparrow style="left:107px;">▼</droparrow></drop>
            <failed style="left: -27.5px;"><value class="t byte2" style="left: 128px;">S(3)</value></failed>
        </values>
        <labels>
            <label class="byte2" style="left: 57px;"><code></code></label>
            <label class="byte2" style="left: 97.5px;"><code>t</code></label>
            <!-- <label class="byte2" style="left: 136.5px;"><code>c</code></label> -->
        </labels>
        <subtext>作用域与 Drop</subtext>
        <!-- <subtext><code>{ let a = ...; }</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
{
    let mut c = S(2);
    c = S(3);  // <- 在赋值前对 `c` 调用 Drop。
    let t = S(1);
    let a = t;
}   // <- `a`, `t`, `c` 的作用域在此结束，对 `a`, `c` 调用 drop。
```

- 一旦一个未被移出的变量的“名称”离开其（drop-）**作用域**，其包含的值将被**drop**。
    - 经验法则：执行到达变量名称离开其定义的 `{}` 块的点。
    - 细节上更复杂，尤其是临时值等。
- 当新值赋给现有变量位置时，也会调用 Drop。
- 在这种情况下，**`Drop::drop()`** 会在该值的位置上被调用。
    - 在上面的例子中，`drop()` 在 `a` 和 `c` 上被调用了两次，但没有在 `t` 上调用。
- 大多数非 `Copy` 的值在大多数时候都会被 drop；例外包括 `mem::forget()`、`Rc` 循环、`abort()`。

</explanation>
</lifetime-section>


</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-lt-2" name="tab-lt">
<label for="tab-lt-2"><b>调用栈</b></label>
<panel><div>

<lifetime-section>
<lifetime-example>
    <section-header>栈帧</section-header>
    <memory-row>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2" style="left: 57px;">S(1)</value>
        </values>
        <labels>
            <label class="byte2" style="left: 57px;"><code>a</code></label>
            <label class="byte2" style="left: 97.5px;"><code>x</code></label>
        </labels>
        <subtext>函数边界</subtext>
        <!-- <subtext><code>fn f(x: S) {}</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
fn f(x: S) { … }

let a = S(1); // <- 我们在这里
f(a);
```

- 当一个**函数被调用**时，参数（和返回值）的内存会在栈上被保留。<sup>1</sup>
- 这里在 `f` 被调用前，`a` 中的值被移动到栈上一个“约定好的”位置，在 `f` 期间，它就像一个“局部变量” `x` 一样工作。

<footnotes>

<sup>1</sup> 实际位置取决于调用约定，实际上可能根本不会在栈上，但这不改变心智模型。

</footnotes>

</explanation>
</lifetime-section>


<lifetime-section>
<lifetime-example class="not-first">
    <memory-row>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2" style="left: 131px;">S(1)</value>
        </values>
        <labels>
            <label class="byte2" style="left: 57px;"><code>a</code></label>
            <label class="byte2" style="left: 97.5px;"><code>x</code></label>
            <label class="byte2" style="left: 136px;"><code>x</code></label>
        </labels>
        <subtext>嵌套函数</subtext>
        <!-- <subtext><code>fn f(x: S) { ... f(x) ... }</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
fn f(x: S) {
    if once() { f(x) } // <- 我们在这里（递归前）
}

let a = S(1);
f(a);
```

- **递归调用**函数，或调用其他函数，同样会扩展栈帧。
- 嵌套太多的调用（尤其通过无界递归）会导致栈增长，并最终溢出，终止应用程序。

</explanation>
</lifetime-section>


<lifetime-section>

<lifetime-example class="not-first">
    <section-header>变量的有效性</section-header>
    <memory-row>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t" style="opacity: 0.4;"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2" style="left: 131px;">S(1)</value>
            <value class="atomic byte4" style="left: 190px;">M { }</value>
        </values>
        <labels>
            <label class="byte2" style="left: 57px;"><code>a</code></label>
            <label class="byte2" style="left: 97.5px;"><code>x</code></label>
            <label class="byte2" style="left: 174px;"><code>m</code></label>
        </labels>
        <subtext>内存复用</subtext>
        <!-- <subtext><code>f(x); let m = M::new();</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
fn f(x: S) {
    if once() { f(x) }
    let m = M::new() // <- 我们在这里（递归后）
}

let a = S(1);
f(a);
```

- 之前持有某种类型的栈内存会在函数调用之间（甚至在函数内部）被复用。
- 这里，对 `f` 的递归产生了第二个 `x`，在递归之后，这块内存被部分地用于 `m`。

> 到目前为止的关键要点是，有多种方式可以使之前持有某个类型有效值的内存位置在此期间不再持有。
> 正如我们稍后将看到的，这对指针有影响。

</explanation>
</lifetime-section>

</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-lt-3" name="tab-lt">
<label for="tab-lt-3"><b>引用与指针</b></label>
<panel><div>

<lifetime-section>
<lifetime-example>
    <section-header class="arrowed">引用类型</section-header>
    <memory-row>
        <arrows>
            <arrow style="left: 62px; width: 176px;">&nbsp;<tip>▼</tip></arrow>
        </arrows>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2" style="left: 57px;">S(1)</value>
            <value class="ptr byte4" style="left: 171px;">0x3</value>
        </values>
        <labels>
            <label class="byte2" style="left: 57px;"><code>a</code></label>
            <label class="byte4" style="left: 171px;"><code>r</code></label>
        </labels>
        <subtext>引用作为指针</subtext>
        <!-- <subtext><code>let r = &mut a;</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
let a = S(1);
let r: &S = &a;
```

- 一个**引用类型**，如 `&S` 或 `&mut S`，可以持有某个 `s` 的**位置**。
- 这里，类型为 `&S`、绑定为 `r` 的变量，持有变量 `a` 的*位置*（`0x3`），该位置的类型必须是 `S`，通过 `&a` 获得。
- 如果你将变量 `c` 视为*特定位置*，那么引用 **`r` 就是一个*位置的交换机***。
- 引用的类型，像所有其他类型一样，通常可以被推断，所以我们从现在开始可能会省略它：
    ```
    let r: &S = &a;
    let r = &a;
    ```
<!-- - 引用本身**从不**关心它们指向的位置内的*值*。 -->

</explanation>
</lifetime-section>


<lifetime-section>
<lifetime-example class="not-first">
    <section-header class="arrowed">（可变）引用</section-header>
    <memory-row>
        <arrows>
            <arrow style="left: 62px; width: 176px;">&nbsp;<tip>▼</tip></arrow>
        </arrows>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2" style="left: 57px;">S(2)</value>
            <value class="ptr byte4" style="left: 171px;">0x3</value>
            <value class="t byte2" style="left: 213px;">S(1)</value>
        </values>
        <labels>
            <label class="byte2" style="left: 57px;"><code>a</code></label>
            <label class="byte4" style="left: 171px;"><code>r</code></label>
            <label class="byte4" style="left: 193px;"><code>d</code></label>
        </labels>
        <subtext>访问非自有内存</subtext>
        <!-- <subtext><code>let d = r.clone(); *r = S(2);</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
let mut a = S(1);
let r = &mut a;
let d = r.clone();  // 从 r-目标 克隆是有效的。
*r = S(2);          // 将新的 S 值设置到 r-目标是有效的。
```


- 引用可以**读取**（`&S`）也可以**写入**（`&mut S`）它们指向的位置。
- *解引用* `*r` 意味着使用**`r` 指向的位置**（*不是* `r` 本身的*位置*或*值*）。
- 在这个例子中，克隆 `d` 是从 `*r` 创建的，`S(2)` 被写入到 `*r`。
    - 我们假设 `S` 实现了 `Clone`，并且 `r.clone()` 克隆的是 `r` 的目标，而不是 `r` 本身。
    - 在赋值 `*r = …` 时，位置中的旧值也会被 drop（上图中未显示）。

</explanation>
</lifetime-section>


<lifetime-section>
<lifetime-example class="not-first">
    <memory-row>
        <arrows>
            <arrow style="left: 62px; width: 176px;">&nbsp;<tip>▼</tip></arrow>
        </arrows>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2 hide" style="left: 57px;">S(2)</value>
            <value class="ptr byte4" style="left: 171px;">0x3</value>
            <value class="atomic byte4" style="top:-36px; left: 20px;">M { x }</value>
            <denied style="left: -71px; top:-36px;">⛔</denied>
            <denied style="left: -131px;">⛔</denied>
        </values>
        <labels>
            <label class="byte2" style="left: 57px;"><code>a</code></label>
            <label class="byte4" style="left: 171px;"><code>r</code></label>
            <label class="byte4" style="left: 193px;"><code>d</code></label>
        </labels>
        <subtext>引用守护被引用者</subtext>
        <!-- <subtext><code>let d = *r; *r = M::new();</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
let mut a = …;
let r = &mut a;
let d = *r;       // 移出值无效，`a` 会变空。
*r = M::new();    // 存储非 S 值无效，没有意义。
```

- 虽然绑定保证总是*持有*有效数据，但引用保证总是*指向*有效数据。
- 特别是 `&mut T` 必须提供与变量相同的保证，甚至更多，因为它们不能溶解目标：
    - 它们**不允许写入无效**数据。
    - 它们**不允许移出**数据（这会使目标变空而所有者不知道）。

</explanation>
</lifetime-section>




<lifetime-section>
<lifetime-example class="not-first">
    <memory-row>
        <arrows>
            <arrow style="left: 62px; width: 176px; border-color: red;">&nbsp;<tip style="color: red">▼</tip></arrow>
        </arrows>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2 hide" style="left: 57px;">C(2)</value>
            <value class="ptr byte4 unsafe" style="left: 171px;">0x3</value>
        </values>
        <labels>
            <label class="byte2 hide" style="left: 57px;"><code>c</code></label>
            <label class="byte4" style="left: 171px;"><code>p</code></label>
        </labels>
        <subtext>裸指针</subtext>
        <!-- <subtext><code>let p: *const S = ...;</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
let p: *const S = questionable_origin();
```

- 与引用相比，指针几乎不提供任何保证。
- 它们可能指向无效或不存在的数据。
- 解引用它们是 `unsafe` 的，将无效的 `*p` 当作有效的是未定义行为。{{ below(target="#unsafe-unsound-undefined") }}

</explanation>
</lifetime-section>

</div></panel></tab>




<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-lt-10" name="tab-lt">
<label for="tab-lt-10"><b>生命周期基础</b></label>
<panel><div>


<lifetime-section>
<lifetime-example>
    <memory-row>
        <memory-backdrop class="past" style="padding-left: 7px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop class="past" style="padding-left: 3px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2 hide" style="left: 57px;">C(2)</value>
            <value class="ptr byte4 hide" style="left: 171px;">0x3</value>
        </values>
        <labels>
            <!-- <label class="byte2" style="left: 37px;"><code>'a</code></label>
            <label class="byte4" style="left: 59px;"><code>'b: 'c</code></label>
            <label class="byte2" style="left: 81px;"><code>'c</code></label>
            <label class="byte4" style="left: 139px;"><code>'d</code></label> -->
        </labels>
        <subtext>事物的“生命周期”</subtext>
        <!-- <subtext><code>f(); g(); h();</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

- 程序中的每个实体都有其相关的（时间/空间）范围，即其*存活*期间。
- 粗略地说，这个*存活时间*可以是<sup>1</sup>
    1. 一个**项可用**的**代码行（LOC）**（例如，一个模块名）。
    1. 一个*位置*被值**初始化**和该位置被**放弃**之间的**代码行**。
    1. 一个位置首次以**某种方式被使用**和该**使用停止**之间的**代码行**。
    1. 一个*值*被创建和该值被 drop 之间的**代码行（或实际时间）**。
- 在本节的其余部分，我们将上述各项称为：
    1. 该项的**作用域**，此处不相关。
    1. 该变量或位置的**作用域**。
    1. 该使用的**生命周期**<sup>2</sup>。
    1. 该值的**生命周期**，在讨论打开的文件描述符时可能有用，但此处也不相关。
- 同样，代码中的生命周期参数，例如 `r: &'a S`，
    - 关心的是任何**`r` *指向*的位置**需要被访问或锁定的代码行；
    - 与 `r` 本身的“存在时间”（作为代码行）无关（当然，它需要存在得更短，就是这样）。
- `&'static S` 意味着地址必须在*所有代码行期间*都有效。

> <sup>1</sup> 文档中有时在区分各种*作用域*和*生命周期*时存在模糊。
> 我们在这里试图 pragmatic，但欢迎提出建议。
>
> <sup>2</sup> *Live lines* 可能是更合适的术语……

</explanation>
</lifetime-section>




<lifetime-section>
<lifetime-example class="not-first">
    <memory-row>
        <memory-backdrop class="past" style="padding-left: 7px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop class="past" style="padding-left: 3px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <arrows>
            <arrow style="left: 192px; width: 120px;">&nbsp;<tip>▼</tip></arrow>
        </arrows>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2 hide" style="left: 38px;">S(0)</value>
            <value class="t byte2 hide" style="left: 79px;">S(1)</value>
            <value class="t byte2" style="left: 119px;">S(2)</value>
            <value class="ptr byte4" style="left: 177px;">0xa</value>
        </values>
        <labels>
            <label class="byte2 hide" style="left: 37px;"><code>a</code></label>
            <label class="byte2 hide" style="left: 78px;"><code>b</code></label>
            <label class="byte2" style="left: 118px;"><code>c</code></label>
            <label class="byte4" style="left: 177px;"><code>r</code></label>
        </labels>
        <subtext><code>r: &'c S</code> 的含义</subtext>
        <!-- <subtext><code>r: &mut 'c S</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

- 假设你从某个地方得到了一个 `r: &'c S`，这意味着：
    - `r` 持有一个 `S` 的地址，
    - `r` 指向的任何地址必须并且将至少存在 `'c` 这么久，
    - 变量 `r` 本身的寿命不能长于 `'c`。



</explanation>
</lifetime-section>



<lifetime-section>
<lifetime-example class="not-first">
    <memory-row>
        <memory-backdrop class="past" style="padding-left: 7px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop class="past" style="padding-left: 3px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <arrows>
            <arrow style="left: 118px; width: 193px;">&nbsp;<tip>▼</tip></arrow>
        </arrows>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2" style="left: 38px;">S(0)</value>
            <value class="t byte2" style="left: 79px;">S(3)</value>
            <value class="t byte2" style="left: 119px;">S(2)</value>
            <value class="ptr byte4" style="left: 177px;">0x6</value>
            <denied style="left: -125px; top:-25px;">⛔</denied>
        </values>
        <labels>
            <label class="byte2" style="left: 37px;"><code>a</code></label>
            <label class="byte2" style="left: 78px;"><code>b</code></label>
            <label class="byte2" style="left: 118px;"><code>c</code></label>
            <label class="byte4" style="left: 177px;"><code>r</code></label>
        </labels>
        <subtext>生命周期的类型特性</subtext>
        <!-- <subtext><code>r = &mut b;</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
{
    let b = S(3);
    {
        let c = S(2);
        let r: &'c S = &c;      // 不太行，因为我们不能在函数体内命名局部变量的生命周期，
        {                       // 但下一页的函数也适用完全相同的原则。
            let a = S(0);

            r = &a;             // `a` 的位置存活的代码行不够 -> 不行。
            r = &b;             // `b` 的位置存活了 `c` 的所有代码行甚至更多 -> 行。
        }
    }
}
```

- 假设你从某个地方得到了一个 `mut r: &mut 'c S`。
    - 也就是说，一个可以持有可变引用的可变位置。
- 如前所述，该引用必须守护目标内存。
- 然而，**`'c` 部分**，就像一个类型，也**守护着允许进入 `r` 的东西**。
- 这里将 `&b`（`0x6`）赋给 `r` 是有效的，但 `&a`（`0x3`）则不行，因为只有 `&b` 的寿命等于或长于 `&c`。

</explanation>
</lifetime-section>




<lifetime-section>
<lifetime-example class="not-first">
    <memory-row>
        <memory-backdrop class="past" style="padding-left: 7px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop class="past" style="padding-left: 3px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <arrows>
            <arrow style="left: 118px; width: 193px;">&nbsp;<tip>▼</tip></arrow>
        </arrows>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t borrowed"></byte>
            <byte class="t borrowed"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2 hide" style="left: 38px;">S(0)</value>
            <value class="t byte2" style="left: 79px;">&nbsp;</value>
            <value class="t byte2 hide" style="left: 119px;">S(2)</value>
            <value class="ptr byte4" style="left: 177px;">0x6</value>
            <failed style="left: -40px;"><value class="t bytes">S(4)</value></failed>
            <denied style="left: -83px;">⛔</denied>
        </values>
        <labels>
            <label class="byte2 hide" style="left: 37px;"><code>a</code></label>
            <label class="byte2" style="left: 78px;"><code>b</code></label>
            <label class="byte2 hide" style="left: 118px;"><code>c</code></label>
            <label class="byte4 hide" style="left: 177px;"><code></code></label>
        </labels>
        <subtext>借用状态</subtext>
    </memory-row>
</lifetime-example>
<explanation>

```
let mut b = S(0);
let r = &mut b;

b = S(4);   // 将会失败，因为 `b` 处于借用状态。

print_byte(r);
```

- 一旦通过 `&b` 或 `&mut b` 获取了变量的地址，该变量就被标记为**被借用 (borrowed)**。
- 在被借用期间，地址的内容不能再通过原始绑定 `b` 进行修改。
- 一旦通过 `&b` 或 `&mut b` 获取的地址停止使用（就代码行而言），原始绑定 `b` 就可以再次使用了。


</explanation>
</lifetime-section>

</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-lt-11" name="tab-lt">
<label for="tab-lt-11"><b>函数中的生命周期</b></label>
<panel>
<div>


<lifetime-section>
<lifetime-example>
    <memory-row>
        <memory-backdrop class="past" style="padding-left: 7px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop class="past" style="padding-left: 3px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t borrowed"></byte>
            <byte class="t borrowed"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t borrowed"></byte>
            <byte class="t borrowed"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2 hide" style="left: 38px;">S(0)</value>
            <value class="t byte2" style="left: 79px;">S(1)</value>
            <value class="t byte2" style="left: 119px;">S(2)</value>
            <value class="ptr byte4" style="left: 177px;">?</value>
            <value class="ptr byte4" style="left: 201px;">0x6</value>
            <value class="ptr byte4" style="left: 224px;">0xa</value>
        </values>
        <labels>
            <label class="byte2 hide" style="left: 37px;"><code>a</code></label>
            <label class="byte4" style="left: 59px;"><code>b</code></label>
            <label class="byte2" style="left: 81px;"><code>c</code></label>
            <label class="byte4" style="left: 139px;"><code>r</code></label>
            <label class="byte4" style="left: 165px;"><code>x</code></label>
            <label class="byte4" style="left: 188px;"><code>y</code></label>
        </labels>
        <subtext>函数参数</subtext>
        <!-- <subtext><code>let r = f(&b, &c);</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
fn f(x: &S, y:&S) -> &u8 { … }

let b = S(1);
let c = S(2);

let r = f(&b, &c);
```

- 当调用接收并返回引用的函数时，会发生两件有趣的事情：
    - 使用的局部变量被置于借用状态，
    - 但在编译时不知道将返回哪个地址。



</explanation>
</lifetime-section>




<lifetime-section>
<lifetime-example class="not-first">
    <memory-row>
        <memory-backdrop class="past" style="padding-left: 7px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop class="past" style="padding-left: 3px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t maybe-borrowed"></byte>
            <byte class="t maybe-borrowed"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t maybe-borrowed"></byte>
            <byte class="t maybe-borrowed"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2 hide" style="left: 38px;">S(0)</value>
            <value class="t byte2" style="left: 79px;">S(1)</value>
            <value class="t byte2" style="left: 119px;">S(2)</value>
            <value class="ptr byte4" style="left: 177px;">?</value>
            <value class="ptr byte4 hide" style="left: 201px;">0x6</value>
            <value class="ptr byte4 hide" style="left: 224px;">0xa</value>
        </values>
        <labels>
            <label class="byte2" style="left: 37px;"><code>a</code></label>
            <label class="byte4" style="left: 59px;"><code>b</code></label>
            <label class="byte2" style="left: 81px;"><code>c</code></label>
            <label class="byte4" style="left: 139px;"><code>r</code></label>
            <label class="byte4 hide" style="left: 165px;"><code>x</code></label>
            <label class="byte4 hide" style="left: 188px;"><code>y</code></label>
        </labels>
        <subtext>“借用”传播的问题</subtext>
        <!-- <subtext><code>let a = b;</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
let b = S(1);
let c = S(2);

let r = f(&b, &c);

let a = b;   // 我可以这样做吗？
let a = c;   // 哪个才是*真正*被借用的？

print_byte(r);
```

- 由于 `f` 只能返回一个地址，因此并非在所有情况下 `b` 和 `c` 都需要保持锁定。
- 在许多情况下，我们可以获得生活质量的提升。
    - 特别是，当我们知道某个参数*不可能*再被用于返回值时。


</explanation>
</lifetime-section>



<lifetime-section>
<lifetime-example class="not-first">
    <memory-row>
        <memory-backdrop class="past" style="padding-left: 7px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop class="past" style="padding-left: 3px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <arrows>
            <arrow style="left: 210px; width: 102px;">&nbsp;<tip>▼</tip></arrow>
        </arrows>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t borrowed"></byte>
            <byte class="t borrowed"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2" style="left: 38px;">S(1)</value>
            <value class="t byte2 hide" style="left: 79px;">S(1)</value>
            <value class="t byte2" style="left: 119px;">S(2)</value>
            <value class="ptr byte4" style="left: 177px;">y + _</value>
            <value class="ptr byte4 hide" style="left: 201px;">0x6</value>
            <value class="ptr byte4 hide" style="left: 224px;">0xa</value>
        </values>
        <labels>
            <label class="byte2" style="left: 37px;"><code>a</code></label>
            <label class="byte4" style="left: 59px;"><code>b</code></label>
            <label class="byte2" style="left: 81px;"><code>c</code></label>
            <label class="byte4" style="left: 139px;"><code>r</code></label>
            <label class="byte4 hide" style="left: 165px;"><code>x</code></label>
            <label class="byte4 hide" style="left: 188px;"><code>y</code></label>
        </labels>
        <subtext>生命周期传播借用状态</subtext>
        <!-- <subtext><code>f(x: &'x S, y: &'y S) -> &'y u8</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
fn f<'b, 'c>(x: &'b S, y: &'c S) -> &'c u8 { … }

let b = S(1);
let c = S(2);

let r = f(&b, &c); // 我们知道返回的引用是基于 `c` 的，它必须保持锁定，
                   // 而 `b` 可以自由移动。

let a = b;

print_byte(r);
```

- 签名中的生命周期参数，如上面的 `'c`，解决了这个问题。
- 它们的主要目的是：
    - **在函数外部**，解释输出地址是基于哪个输入地址生成的，
    - **在函数内部**，保证只有寿命至少为 `'c` 的地址被赋值。
- 实际的生命周期 `'b`、`'c` 由编译器在**调用点**根据开发者提供的被借用变量透明地选择。
- 它们**不**等于 `b` 或 `c` 的*作用域*（即从初始化到销毁的代码行），而只是其作用域的一个最小子集，称为*生命周期*，即基于 `b` 和 `c` 需要被借用多长时间来执行此调用并使用获得的结果的最小代码行集。
- 在某些情况下，比如如果 `f` 有 `'c: 'b`，我们仍然无法区分，两者都需要保持锁定。

</explanation>
</lifetime-section>




<lifetime-section>
<lifetime-example class="not-first">
    <memory-row>
        <memory-backdrop class="past" style="padding-left: 7px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte class="atomic"></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop class="past" style="padding-left: 3px;">
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2" style="left: 38px;">S(2)</value>
            <value class="t byte2 hide" style="left: 79px;">S(1)</value>
            <value class="t byte2 hide" style="left: 119px;">S(2)</value>
            <value class="ptr byte4 hide" style="left: 177px;">y + 1</value>
            <value class="ptr byte4 hide" style="left: 201px;">0x6</value>
            <value class="ptr byte4 hide" style="left: 224px;">0xa</value>
        </values>
        <labels>
            <label class="byte2" style="left: 37px;"><code>a</code></label>
            <label class="byte4 hide" style="left: 59px;"><code>b</code></label>
            <label class="byte2" style="left: 81px;"><code>c</code></label>
            <label class="byte4 hide" style="left: 139px;"><code>r</code></label>
            <label class="byte4 hide" style="left: 165px;"><code>x</code></label>
            <label class="byte4 hide" style="left: 188px;"><code>y</code></label>
        </labels>
        <!-- <subtext><code>{ let r = ... }</code></subtext> -->
        <subtext>解锁</subtext>
    </memory-row>
</lifetime-example>
<explanation>

```
let mut c = S(2);

let r = f(&c);
let s = r;
                    // <- 不是这里，`s` 延长了 `c` 的锁定。

print_byte(s);

let a = c;          // <- 但是在这里，不再使用 `r` 或 `s`。


```
- 一旦任何可能指向它的引用的最后一次使用结束，变量位置就会再次被*解锁*。

</explanation>
</lifetime-section>

</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-lt-12" name="tab-lt">
<label for="tab-lt-12"><b>高级 {{ esoteric() }}</b></label>
<panel>
<div>




<lifetime-section>
<lifetime-example>
    <memory-row>
        <arrows>
            <arrow style="left: 53px; width: 92px;">&nbsp;<tip>▼</tip></arrow>
            <arrow style="left: 57px; width: 104px;">&nbsp;<tip>▼</tip></arrow>
            <arrow style="left: -155px; width: 320px; top: -5px; border-style: dashed;">&nbsp;</arrow>
        </arrows>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte class="ptr"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <value class="t byte2" style="left: 38px;">S(1)</value>
            <value class="ptr byte4" style="left: 80px;">0x2</value>
            <value class="ptr byte4" style="left: 120px;">0x6</value>
            <value class="ptr byte4" style="left: 162px;">0x2</value>
        </values>
        <labels>
            <label class="byte2" style="left: 37px;"><code>a</code></label>
            <label class="byte4" style="left: 79px;"><code>ra</code></label>
            <label class="byte2" style="left: 139px;"><code>rb</code></label>
            <label class="byte2" style="left: 216px;"><code>rval</code></label>
        </labels>
        <subtext>引用的引用</subtext>
        <!-- <subtext><code>f(x: &'x S, y: &'y S) -> &'y u8</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
// 返回短 ('b) 引用
fn f1sr<'b, 'a>(rb: &'b     &'a     S) -> &'b     S { *rb }
fn f2sr<'b, 'a>(rb: &'b     &'a mut S) -> &'b     S { *rb }
fn f3sr<'b, 'a>(rb: &'b mut &'a     S) -> &'b     S { *rb }
fn f4sr<'b, 'a>(rb: &'b mut &'a mut S) -> &'b     S { *rb }

// 返回短 ('b) 可变引用。
// f1sm<'b, 'a>(rb: &'b     &'a     S) -> &'b mut S { *rb } // M
// f2sm<'b, 'a>(rb: &'b     &'a mut S) -> &'b mut S { *rb } // M
// f3sm<'b, 'a>(rb: &'b mut &'a     S) -> &'b mut S { *rb } // M
fn f4sm<'b, 'a>(rb: &'b mut &'a mut S) -> &'b mut S { *rb }

// 返回长 ('a) 引用。
fn f1lr<'b, 'a>(rb: &'b     &'a     S) -> &'a     S { *rb }
// f2lr<'b, 'a>(rb: &'b     &'a mut S) -> &'a     S { *rb } // L
fn f3lr<'b, 'a>(rb: &'b mut &'a     S) -> &'a     S { *rb }
// f4lr<'b, 'a>(rb: &'b mut &'a mut S) -> &'a     S { *rb } // L

// 返回长 ('a) 可变引用。
// f1lm<'b, 'a>(rb: &'b     &'a     S) -> &'a mut S { *rb } // M
// f2lm<'b, 'a>(rb: &'b     &'a mut S) -> &'a mut S { *rb } // M
// f3lm<'b, 'a>(rb: &'b mut &'a     S) -> &'a mut S { *rb } // M
// f4lm<'b, 'a>(rb: &'b mut &'a mut S) -> &'a mut S { *rb } // L

// 现在假设我们有一个 `ra`
let mut ra: &'a mut S = …;

let rval = f1sr(&&*ra);       // OK
let rval = f2sr(&&mut *ra);
let rval = f3sr(&mut &*ra);
let rval = f4sr(&mut ra);

//  rval = f1sm(&&*ra);       // 会很糟，因为 rval 将是从
//  rval = f2sm(&&mut *ra);   // 破碎的可变性链中获得的可变引用。
//  rval = f3sm(&mut &*ra);   //
let rval = f4sm(&mut ra);

let rval = f1lr(&&*ra);
//  rval = f2lr(&&mut *ra);   // 如果这行得通，我们现在就有 `rval` 和 `ra`……
let rval = f3lr(&mut &*ra);
//  rval = f4lr(&mut ra);     // ……（可变地）别名了下面的计算中的 `S`。

//  rval = f1lm(&&*ra);       // 与上面相同，因可变链原因失败。
//  rval = f2lm(&&mut *ra);   //                    "
//  rval = f3lm(&mut &*ra);   //                    "
//  rval = f4lm(&mut ra);     // 与上面相同，因别名原因失败。

// 某个我们使用 `ra` 和 `rval` 的虚构地方，两者都存活。
compute(ra, rval);
```

<footnotes>

此处 (`M`) 表示因可变性错误编译失败，(`L`) 表示生命周期错误。
此外，解引用 `*rb` 并非严格必要，只是为了清晰起见而添加。

</footnotes>

- `f_sr` 情况总是有效，短引用（只活 `'b`）总是可以产生。
- `f_sm` 情况通常失败，因为需要一个*可变链*到 `S` 才能返回 `&mut S`。
- `f_lr` 情况可能失败，因为从 `&'a mut S` 返回 `&'a S` 给调用者意味着现在将存在两个对同一 `S` 的引用（一个可变），这是非法的。
- `f_lm` 情况总是因上述原因的组合而失败。

> 注意：这个例子是关于 `f` 函数，而不是 `compute`。你可以假设
> 它被定义为 `fn compute(x: &S, y: &S) {}`。在这种情况下，`ra` 参数
> 将被自动强制转换{{ below(target="#type-conversions") }}从 `&mut S` 到 `&S`，因为你不能有
> 一个共享引用和一个可变引用指向同一个目标。



</explanation>
</lifetime-section>


<lifetime-section>
<lifetime-example class="not-first">
    <memory-row>
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte class="t"></byte>
            <byte class="t"></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
        </memory-backdrop>
        <values>
            <drop><value class="t byte2" style="left: 38px;">S(1)</value><droparrow style="left:17px;">▼</droparrow></drop>
        </values>
        <labels>
            <label class="byte2" style="left: 37px;"><code>_</code></label>
            <!-- <label class="byte2" style="left: 136.5px;"><code>c</code></label> -->
        </labels>
        <subtext>Drop 和 <code>_</code></subtext>
        <!-- <subtext><code>{ let a = ...; }</code></subtext> -->
    </memory-row>
</lifetime-example>
<explanation>

```
{
    let f = |x, y| (S(x), S(y)); // 返回两个'可 Drop' 的函数。

    let (    x1, y) = f(1, 4);  // S(1) - 作用域   S(4) - 作用域
    let (    x2, _) = f(2, 5);  // S(2) - 作用域   S(5) - 立即
    let (ref x3, _) = f(3, 6);  // S(3) - 作用域   S(6) - 作用域

    println!("…");
}
```

<footnotes>

此处 `作用域` 意味着包含的值存活到作用域结束，即超过 `println!()`。

</footnotes>

- 产生可移动值的函数或表达式必须由被调用方处理。
- 存储在“正常”绑定中的值会保留到作用域结束，然后被 drop。
- 存储在 `_` 绑定中的值通常会立即被 drop。
- 然而，有时引用（例如 `ref x3`）可以使值（例如元组 `(S(3), S(6))`）保留更长时间，因此作为该元组一部分的 `S(6)` 只能在对其兄弟 `S(3)` 的引用消失后才能被 drop。



</explanation>
</lifetime-section>



</div></panel></tab>
</tabs>


<footnotes>

↕️ 点击展开示例。

</footnotes>



{{ tablesep() }}


</magic>


---


# 内存布局

常见类型的字节表示。


## 基本类型 {#basic-types}

语言核心内置的基本类型。



#### 布尔型 {{ ref(page="types/boolean.html") }} 与数值类型 {{ ref(page="types/numeric.html") }}

<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>bool</code></name>
    <visual class="bool">
        <byte><code></code></byte>
    </visual>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>u8</code>, <code>i8</code></name>
    <visual class="bytes">
        <byte><code></code></byte>
    </visual>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced" >
    <name><code>u16</code>, <code>i16</code></name>
    <visual class="bytes">
        <byte><code></code></byte>
        <byte><code></code></byte>
    </visual>
</datum>


<!-- NEW ENTRY -->
<datum  class="spaced">
    <name><code>u32</code>, <code>i32</code></name>
    <visual class="bytes">
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
    </visual>
</datum>


<!-- NEW ENTRY -->
<datum  class="spaced">
    <name><code>u64</code>, <code>i64</code></name>
    <visual class="bytes">
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
    </visual>
</datum>


<!-- NEW ENTRY -->
<datum  class="spaced">
    <name><code>u128</code>, <code>i128</code></name>
    <visual class="bytes">
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
    </visual>
</datum>



<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>usize</code>, <code>isize</code></name>
    <visual class="sized">
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte style="border-color: #888;"><code></code></byte>
        <byte style="border-color: #888;"><code></code></byte>
        <byte style="border-color: #aaa;"><code></code></byte>
        <byte style="border-color: #aaa;"><code></code></byte>
        <byte style="border-color: #aaa;"><code></code></byte>
        <byte style="border-color: #aaa;"><code></code></byte>
    </visual>
    <zoom>
        与平台上的 <code>ptr</code> 大小相同。
    </zoom>
</datum>



<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>f16</code> {{ experimental() }} </name>
    <visual class="float">
        <byte><code></code></byte>
        <byte><code></code></byte>
    </visual>
</datum>



<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>f32</code></name>
    <visual class="float">
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
    </visual>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>f64</code></name>
    <visual class="float">
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
    </visual>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>f128</code> {{ experimental() }} </name>
    <visual class="float">
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
    </visual>
</datum>



<br/>


{{ tablesep() }}


<!-- 在小屏幕上创建一个水平滚动区域以保持布局 -->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

<tabs>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-numeric-1" name="tab-group-numeric" checked>
<label for="tab-numeric-1"><b>无符号类型</b></label>
<panel><div>



| 类型    | 最大值                                                |
| ------- | ----------------------------------------------------- |
| `u8`    | `255`                                                 |
| `u16`   | `65_535`                                              |
| `u32`   | `4_294_967_295`                                       |
| `u64`   | `18_446_744_073_709_551_615`                          |
| `u128`  | `340_282_366_920_938_463_463_374_607_431_768_211_455` |
| `usize` | 取决于平台指针大小，与 `u16`、`u32` 或 `u64` 相同。   |


</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-numeric-3" name="tab-group-numeric">
<label for="tab-numeric-3"><b>有符号类型</b></label>
<panel><div>



| 类型    | 最大值                                                |
| ------- | ----------------------------------------------------- |
| `i8`    | `127`                                                 |
| `i16`   | `32_767`                                              |
| `i32`   | `2_147_483_647`                                       |
| `i64`   | `9_223_372_036_854_775_807`                           |
| `i128`  | `170_141_183_460_469_231_731_687_303_715_884_105_727` |
| `isize` | 取决于平台指针大小，与 `i16`、`i32` 或 `i64` 相同。   |

{{ tablesep() }}

| 类型    | 最小值                                                 |
| ------- | ------------------------------------------------------ |
| `i8`    | `-128`                                                 |
| `i16`   | `-32_768`                                              |
| `i32`   | `-2_147_483_648`                                       |
| `i64`   | `-9_223_372_036_854_775_808`                           |
| `i128`  | `-170_141_183_460_469_231_731_687_303_715_884_105_728` |
| `isize` | 取决于平台指针大小，与 `i16`、`i32` 或 `i64` 相同。    |


</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-numeric-6" name="tab-group-numeric">
<label for="tab-numeric-6"><b>浮点类型</b></label>
<panel><div>


| 类型                        | 最大值                    | 最小正值                   | 最大无损整数<sup>1</sup> |
| --------------------------- | ------------------------- | -------------------------- | ------------------------ |
| `f16` {{ experimental() }}  | 65504.0                   | 6.10 ⋅ 10 <sup>-5</sup>    | `2048`                   |
| `f32`                       | 3.40 ⋅ 10 <sup>38</sup>   | 3.40 ⋅ 10 <sup>-38</sup>   | `16_777_216`             |
| `f64`                       | 1.79 ⋅ 10 <sup>308</sup>  | 2.23 ⋅ 10 <sup>-308</sup>  | `9_007_199_254_740_992`  |
| `f128` {{ experimental() }} | 1.19 ⋅ 10 <sup>4932</sup> | 3.36 ⋅ 10 <sup>-4932</sup> | 2.07 ⋅ 10 <sup>34</sup>  |

<footnotes>

<sup>1</sup> 最大整数 `M`，使得所有其他整数 `0 <= X <= M` 都能在该类型中无损表示。换句话说，可能存在更大的整数仍能无损表示（例如 `f16` 的 `65504`），但直到该值，无损表示是有保证的。

</footnotes>

{{ tablesep() }}

> 浮点值为视觉清晰度而近似。负数极限是值乘以 -1。

</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-numeric-2" name="tab-group-numeric">
<label for="tab-numeric-2"><b>浮点内部{{ esoteric() }}</b></label>
<panel><div>


`f32` 的示例位表示<sup>*</sup>：

<!-- NEW ENTRY -->
<datum style="opacity:0.7; margin-bottom:10px;">
    <visual class="float">
    <bitgroup>
        <bit><code>S</code></bit>
    </bitgroup>
    <bitgroup>
        <bit><code>E</code></bit>
        <bit><code>E</code></bit>
        <bit><code>E</code></bit>
        <bit><code>E</code></bit>
        <bit><code>E</code></bit>
        <bit><code>E</code></bit>
        <bit><code>E</code></bit>
        <bit><code>E</code></bit>
    </bitgroup>
    <bitgroup>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
        <bit><code>F</code></bit>
    </bitgroup>
    </visual>
</datum>

{{ tablesep() }}

解释：

| f32        | S (1) | E (8)    | F (23) | 值                                     |
| ---------- | ----- | -------- | ------ | -------------------------------------- |
| 规格化数   | ±     | 1 到 254 | 任意   | ±(1.F)<sub>2</sub> * 2<sup>E-127</sup> |
| 非规格化数 | ±     | 0        | 非零   | ±(0.F)<sub>2</sub> * 2<sup>-126</sup>  |
| 零         | ±     | 0        | 0      | ±0                                     |
| 无穷大     | ±     | 255      | 0      | ±∞                                     |
| NaN        | ±     | 255      | 非零   | NaN                                    |

{{ tablesep() }}

同样，对于 <code>f64</code> 类型，它看起来像这样：

| f64        | S (1) | E (11)    | F (52) | 值                                      |
| ---------- | ----- | --------- | ------ | --------------------------------------- |
| 规格化数   | ±     | 1 到 2046 | 任意   | ±(1.F)<sub>2</sub> * 2<sup>E-1023</sup> |
| 非规格化数 | ±     | 0         | 非零   | ±(0.F)<sub>2</sub> * 2<sup>-1022</sup>  |
| 零         | ±     | 0         | 0      | ±0                                      |
| 无穷大     | ±     | 2047      | 0      | ±∞                                      |
| NaN        | ±     | 2047      | 非零   | NaN                                     |

<footnotes>
    <sup>*</sup> 浮点类型遵循 <a href="https://en.wikipedia.org/wiki/IEEE_754-2008_revision">IEEE 754-2008</a> 标准，并取决于平台的字节序。
</footnotes>

</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-numeric-4" name="tab-group-numeric">
<label for="tab-numeric-4"><b>转换陷阱</b> {{ bad() }}</label>
<panel><div class="">


| 转换<sup>1</sup>      | 得到  | 注意                                     |
| --------------------- | ----- | ---------------------------------------- |
| `3.9_f32 as u8`       | `3`   | 截断，考虑先用 `x.round()`。             |
| `314_f32 as u8`       | `255` | 取最接近的可用数。                       |
| `f32::INFINITY as u8` | `255` | 同上，将 `INFINITY` 视为*非常大*的数。   |
| `f32::NAN as u8`      | `0`   | -                                        |
| `_314 as u8`          | `58`  | 截断多余的位。                           |
| `_257 as i8`          | `1`   | 截断多余的位。                           |
| `_200 as i8`          | `-56` | 截断多余的位，最高有效位可能也表示负数。 |

</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-numeric-5" name="tab-group-numeric">
<label for="tab-numeric-5"><b>算术陷阱</b> {{ bad() }}</label>
<panel><div class="">

| 操作<sup>1</sup>               | 得到            | 注意                                                                                               |
| ------------------------------ | --------------- | -------------------------------------------------------------------------------------------------- |
| `200_u8 / 0_u8`                | 编译错误。      | -                                                                                                  |
| `200_u8 / _0` <sup>d, r</sup>  | Panic。         | 常规数学运算可能 panic；此处：除以零。                                                             |
| `200_u8 + 200_u8`              | 编译错误。      | -                                                                                                  |
| `200_u8 + _200` <sup>d</sup>   | Panic。         | 考虑使用 `checked_`、`wrapping_` 等。{{ std(page="std/primitive.isize.html#method.checked_add") }} |
| `200_u8 + _200` <sup>r</sup>   | `144`           | 在 release 模式下会溢出。                                                                          |
| `-128_i8 * -1`                 | 编译错误。      | 会溢出（`128_i8` 不存在）。                                                                        |
| `-128_i8 * _1neg` <sup>d</sup> | Panic。         | -                                                                                                  |
| `-128_i8 * _1neg` <sup>r</sup> | `-128`          | 在 release 模式下溢出回 `-128`。                                                                   |
| `1_u8 / 2_u8`                  | `0`             | 其他整数除法会截断。                                                                               |
| `0.8_f32 + 0.1_f32`            | `0.90000004`    | -                                                                                                  |
| `1.0_f32 / 0.0_f32`            | `f32::INFINITY` | -                                                                                                  |
| `0.0_f32 / 0.0_f32`            | `f32::NAN`      | -                                                                                                  |
| `x < f32::NAN`                 | `false`         | `NAN` 比较总是返回 false。                                                                         |
| `x > f32::NAN`                 | `false`         | `NAN` 比较总是返回 false。                                                                         |
| `f32::NAN == f32::NAN`         | `false`         | 使用 `f32::is_nan()` {{ std(page="std/primitive.f32.html#method.is_nan") }} 代替。                 |

</div></panel></tab>


<!-- End tabs -->
</tabs>

<!-- End overflow prevention -->
</div></div>


<footnotes>

<sup>1</sup> 表达式 `_100` 表示任何可能包含值 `100` 的东西，例如 `100_i32`，但对编译器是不透明的。<br/>
<sup>d</sup> Debug 构建。<br/>
<sup>r</sup> Release 构建。<br/>

</footnotes>


{{ tablesep() }}



#### 文本类型 {{ ref(page="types/textual.html") }}


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>char</code></name>
    <visual class="char">
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
        <byte><code></code></byte>
    </visual>
    <description>任何 Unicode 标量值。</description>
</datum>



<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>str</code></name>
    <visual>
        <note>…</note>
        <byte class="bytes"><code>U</code></byte>
        <byte class="bytes"><code>T</code></byte>
        <byte class="bytes"><code>F</code></byte>
        <byte class="bytes"><code>-</code></byte>
        <byte class="bytes"><code>8</code></byte>
        <note>… 不定次数</note>
    </visual>
    <description>很少单独出现，通常以 <code>&str</code> 形式出现。</description>
</datum>


{{ tablesep() }}

<tabs>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-textual-3" name="tab-group-textual" checked>
<label for="tab-textual-3"><b>基础</b></label>
<panel><div>

| 类型   | 描述                                                                                                                  |
| ------ | --------------------------------------------------------------------------------------------------------------------- |
| `char` | 总是 4 字节，只持有一个 Unicode **标量值** {{ link(url="https://www.unicode.org/glossary/#unicode_scalar_value") }}。 |
| `str`  | 一个未知长度的 `u8` 数组，保证持有 **UTF-8 编码的代码点**。                                                           |

</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-textual-1" name="tab-group-textual">
<label for="tab-textual-1"><b>用法</b></label>
<panel><div>



<!-- 注意：

- `char` 总是 4 字节，只持有一个 Unicode **标量值** {{ link(url="https://www.unicode.org/glossary/#unicode_scalar_value") }}，因此可能浪费空间。
- `str` 是一个未知长度的字节数组，保证持有 **UTF-8 编码的代码点**（但更难索引）。
 -->

| 字符               | 描述                                                                                               |
| ------------------ | -------------------------------------------------------------------------------------------------- |
| `let c = 'a';`     | 通常 `char`（Unicode 标量）可以与你对*字符*的直觉相吻合。                                          |
| `let c = '❤';`     | 它也可以持有许多 Unicode 符号。                                                                    |
| `let c = '❤️';`     | 但不总是。给定的 emoji 是**两个** `char`（见编码）并且**不能**{{ bad() }}被 `c` 持有。<sup>1</sup> |
| `c = 0xffff_ffff;` | 另外，char **不允许**{{ bad() }}持有任意的位模式。                                                 |

<footnotes>
    <sup>1</sup> 有趣的是，由于<a href="https://en.wikipedia.org/wiki/Zero-width_joiner">零宽度连接符</a> (⨝)，用户*感知到的字符*可能变得更加不可预测：👨‍👩‍👧 实际上是 5 个 char 👨⨝👩⨝👧，渲染引擎可以自由地将它们融合成一个，或分开显示为三个，这取决于它们的能力。
</footnotes>


{{ tablesep() }}

| 字符串          | 描述                                                    |
| --------------- | ------------------------------------------------------- |
| `let s = "a";`  | `str` 通常不会直接持有，而是作为 `&str`，如此处的 `s`。 |
| `let s = "❤❤️";` | 它可以持有任意文本，每个字符长度可变，并且难以索引。    |


</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-textual-2" name="tab-group-textual">
<label for="tab-textual-2"><b>编码</b>{{ esoteric() }}</label>
<panel><div>


`let s = "I ❤ Rust"; ` <br>
`let t = "I ❤️ Rust";`

| 变体                   | 内存表示<sup>2<sup>                                                                                                                                                                                          |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `s.as_bytes()`         | `49` `20` <span class="force-code-color same-black"><b>`e2 9d a4`</b> </span> `20 52 75 73 74` <sup>3<sup>                                                                                                   |
| `t.as_bytes()`         | `49` `20` <span class="force-code-color same-black"><b>`e2 9d a4`</b> </span> <span class="force-code-color same-red"><b>`ef b8 8f`</b></span> `20 52 75 73 74` <sup>4<sup>                                  |
| `s.chars()`<sup>1<sup> | `49 00 00 00 20 00 00 00` <span class="force-code-color same-black"><b>`64 27 00 00` </b></span> `20 00 00 00 52 00 00 00 75 00 00 00 73 00` &hellip;                                                        |
| `t.chars()`<sup>1<sup> | `49 00 00 00 20 00 00 00` <span class="force-code-color same-black"><b>`64 27 00 00`</b></span> <span class="force-code-color same-red"><b>`0f fe 01 00`</b></span> `20 00 00 00 52 00 00 00 75 00` &hellip; |

{{ tablesep() }}

<footnotes>
    <sup>1</sup> 结果然后被收集到一个数组中，并转换为字节。<br>
    <sup>2</sup> 值以十六进制给出，在 x86 平台上。<br>
    <sup>3</sup> 注意 <code>❤</code>，其 <a href="https://codepoints.net/U+2764">Unicode 代码点为 (U+2764)</a>，在 <code>char</code> 内部表示为 <span class="force-code-color same-black"><b>64 27 00 00</b></span>，但在 <code>str</code> 中被 <a href="https://en.wikipedia.org/wiki/UTF-8#Description">UTF-8 编码为</a> <span class="force-code-color same-black"><b>e2 9d a4</b></span>。<br>
    <sup>4</sup> 还要注意 emoji <a href="https://emojipedia.org/red-heart/">红心 <code>❤️</code></a> 是 <code>❤</code> 和 <a href="https://codepoints.net/U+FE0F">U+FE0F 变体选择器</a>的组合，因此 `t` 的字符数比 `s` 多。
</footnotes>

{{ tablesep() }}


<footnotes>

> <sup>⚠️</sup> 由于似乎是浏览器 bug，Safari 和 Edge 在脚注 3 和 4 中渲染心形有误，尽管它们能在上面的 `s` 和 `t` 中正确地区分它们。

</footnotes>

</div></panel></tab>


<!-- End tabs -->
</tabs>


{{ tablesep() }}


## 自定义类型 {#custom-types}

用户可定义的基本类型。实际的<b>布局</b> {{ ref(page="type-layout.html") }} 取决于<b>表示 (representation)</b>；{{ ref(page="type-layout.html#representations") }} 可能存在填充。


<!-- NEW ENTRY -->
<datum class="spaced">
    <name class="nogrow"><code>T</code></name>
    <name class="hidden">x</name>
    <visual>
       <framed class="any t"><code>T</code></framed>
    </visual>
    <description>有大小的类型。</description>
</datum>

<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>T: ?Sized</code></name>
    <visual>
       <framed class="any unsized"><code>T</code></framed>
    </visual>
    <description>可能无大小。</description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>[T; n]</code></name>
    <visual>
       <framed class="any t"><code>T</code></framed>
       <framed class="any t"><code>T</code></framed>
       <framed class="any t"><code>T</code></framed>
       <note>… n 次</note>
    </visual>
    <description>包含 <code>n</code> 个元素的固定数组。</description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>[T]</code></name>
    <visual>
       <note>…</note>
       <framed class="any t"><code>T</code></framed>
       <framed class="any t"><code>T</code></framed>
       <framed class="any t"><code>T</code></framed>
       <note>… 不定次数</note>
    </visual>
    <description><b>切片类型</b>，包含未知数量的元素。既不是<br> <code>Sized</code>（也不携带 <code>len</code> 信息），并且最<br>常以引用 <code>&[T]</code> 的形式存在。{{ below(target="#references-pointers-ui") }}</description>
</datum>

<!-- NEW ENTRY -->
<datum style="margin-right:70px; position: relative; width: 70px;">
    <name class="nogrow"><code>struct S;</code></name>
    <name class="hidden"><code>;</code></name>
    <visual style="width: 15px;" class="zst">
        <code></code>
    </visual>
    <description>零大小类型。 </description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>(A, B, C)</code></name>
    <visual style="width: 182px;">
       <framed class="any"><code>A</code></framed>
       <framed class="any" style="width: 100px;"><code>B</code></framed>
       <framed class="any" style="width: 50px;"><code>C</code></framed>
    </visual>
    <andor>或可能是</andor>
    <visual style="width: 182px;">
       <framed class="any" style="width: 100px;"><code>B</code></framed>
       <framed class="any"><code>A</code></framed>
       <framed class="any" style="width: 50px;"><code>C</code></framed>
    </visual>
    <description>除非强制指定表示（例如通过<br><code>#[repr(C)]</code>），否则类型布局<br>未指定。</description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>struct S { b: B, c: C } </code></name>
    <visual style="width: 166px;">
       <framed class="any" style="width: 100px;"><code>B</code></framed>
       <framed class="any" style="width: 50px;"><code>C</code></framed>
    </visual>
    <andor>或可能是</andor>
    <visual>
       <framed class="any" style="width: 50px;"><code>C</code></framed>
       <pad><code style="">↦</code></pad>
       <framed class="any" style="width: 100px;"><code>B</code></framed>
    </visual>
    <description>编译器也可能添加填充。</description>
</datum>



<blockquote>
<footnotes>

另请注意，两个具有完全相同字段的类型 `A(X, Y)` 和 `B(X, Y)` 仍然可以有不同的布局；在没有表示保证的情况下，切勿使用 `transmute()` {{ std(page="std/mem/fn.transmute.html") }}。

</footnotes>
</blockquote>



{{ tablesep() }}

这些**和类型 (sum types)** 持有其子类型之一的值：

<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>enum E { A, B, C }</code></name>
    <visual class="enum" style="text-align: left;">
        <pad><code>标签</code></pad>
        <framed class="any">
            <code>A</code>
        </framed>
    </visual>
    <andor>互斥或</andor>
    <visual class="enum" style="text-align: left;">
        <pad><code>标签</code></pad>
        <framed class="any" style="width: 100px;">
            <code>B</code>
        </framed>
    </visual>
    <andor>互斥或</andor>
    <visual class="enum" style="text-align: left;">
        <pad><code>标签</code></pad>
        <framed class="any" style="width: 50px;">
            <code>C</code>
        </framed>
    </visual>
    <description>
        安全地持有 A 或 B 或 C，也<br>称为‘带标签的联合体’，尽管<br>编译器可能会将标签压缩<br>到‘未使用’的位中。
    </description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>union { … }</code></name>
    <visual style="text-align: left;">
        <framed class="any">
            <code>A</code>
        </framed>
    </visual>
    <andor>不安全或</andor>
    <visual style="text-align: left;">
        <framed class="any" style="width: 100px;">
            <code>B</code>
        </framed>
    </visual>
    <andor>不安全或</andor>
    <visual style="text-align: left;">
        <framed class="any" style="width: 50px;">
            <code>C</code>
        </framed>
    </visual>
    <description>
        可以不安全地重新解释<br>内存。结果可能<br>是未定义的。
    </description>
</datum>



## 引用与指针 {#references-pointers-ui}

引用提供对第三方内存的安全访问，裸指针提供`unsafe`访问。
相应的 `mut` 类型与其不可变对应项具有相同的数据布局。


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>&'a T</code></name>
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <payload>
            <code>meta</code><sub>2/4/8</sub>
        </payload>
    </visual>
    <memory-entry>
        <memory-link style="left:46%;">|</memory-link>
        <memory class="anymem">
            <framed class="any unsized"><code>T</code></framed>
        </memory>
    </memory-entry>
    <description>必须指向某个有效的 <code>t</code>（类型为 <code>T</code>），<br> 且任何这样的目标必须至少存在<br> <code>'a</code> 时间。</description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>*const T</code></name>
    <visual class="unsafe">
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <payload>
            <code>meta</code><sub>2/4/8</sub>
        </payload>
    </visual>
    <zoom>
        无保证。
    </zoom>
</datum>

<br/>


### 指针元数据 {#pointer-meta}

许多引用和指针类型可以携带一个额外的字段，即**指针元数据 (pointer metadata)**。{{ std(page="nightly/std/ptr/trait.Pointee.html#pointer-metadata") }}
它可以是目标的元素或字节长度，或指向一个<i>虚函数表 (vtable)</i>的指针。带元数据的指针称为**胖指针 (fat)**，否则称为**瘦指针 (thin)**。

<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>&'a T</code></name>
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
    </visual>
    <memory-entry>
        <memory-link style="left:46%;">|</memory-link>
        <memory class="anymem">
            <framed class="any t"><code>T</code></framed>
        </memory>
    </memory-entry>
    <description>对于有大小的目标<br>没有元数据。<br>（指针是瘦的）。</description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>&'a T</code></name>
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <sized>
            <code>len</code><sub>2/4/8</sub>
        </sized>
    </visual>
    <memory-entry>
        <memory-link style="left:46%;">|</memory-link>
        <memory class="anymem">
            <framed class="any unsized"><code>T</code></framed>
        </memory>
    </memory-entry>
    <description>如果 <code>T</code> 是 DST <code>struct</code>，例如<br> <code>S { x: [u8] }</code>，
    元数据字段 <code>len</code> 是<br>动态大小内容的数量。</description>
</datum>



<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>&'a [T]</code></name>
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <sized>
            <code>len</code><sub>2/4/8</sub>
        </sized>
    </visual>
    <memory-entry class="double">
        <memory-link style="left:24%;">|</memory-link>
        <memory class="anymem">
            …
            <framed class="any" style="width: 30px;"><code>T</code></framed>
            <framed class="any" style="width: 30px;"><code>T</code></framed>
            …
        </memory>
    </memory-entry>
    <description>常规的<b>切片引用</b>（即切片类型 <code>[T]</code> 的<br>引用类型）{{ above (target="#custom-types") }} <br>如果 <code>'a</code> 被省略，通常写作 <code>&[T]</code>。</description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>&'a str</code></name>
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <sized>
            <code>len</code><sub>2/4/8</sub>
        </sized>
    </visual>
    <memory-entry class="double">
        <memory-link style="left:24%;">|</memory-link>
        <memory class="anymem">
            …
            <byte class="bytes"><code>U</code></byte>
            <byte class="bytes"><code>T</code></byte>
            <byte class="bytes"><code>F</code></byte>
            <byte class="bytes"><code>-</code></byte>
            <byte class="bytes"><code>8</code></byte>
            …
        </memory>
    </memory-entry>
    <description><b>字符串切片引用</b>（即字符串类型 <code>str</code> 的<br>引用类型），<br>其元数据 <code>len</code> 是字节长度。</description>
</datum>

<br>

<!-- NEW ENTRY -->
<datum class="spaced" style="padding-bottom: 165px; position: relative;">
    <name><code>&'a dyn Trait</code></name>
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <ptr>
            <code>ptr</code><sub>2/4/8</sub>
        </ptr>
    </visual>
    <memory-entry>
        <memory-link style="left:49%;">|</memory-link>
        <memory class="anymem">
            <framed class="any unsized"><code>T</code></framed>
        </memory>
    </memory-entry>
    <memory-entry style="width:220px; position: absolute;">
        <memory-link style="left:22%;">|</memory-link>
        <memory class="static-vtable" style="width: 210px;">
            <table>
                <tr class="vtable"><td><code>*Drop::drop(&mut T)</code></td></tr>
                <tr class="vtable"><td><code>size</code></td></tr>
                <tr class="vtable"><td><code>align</code></td></tr>
                <tr class="vtable"><td><code>*Trait::f(&T, …)</code></td></tr>
                <tr class="vtable"><td><code>*Trait::g(&T, …)</code></td></tr>
            </table>
        </memory>
        <description>元数据指向虚函数表，其中 <code>*Drop::drop()</code>、<code>*Trait::f()</code> 等是指向它们各自为 <code>T</code> 的 <code>impl</code> 的指针。</description>
    </memory-entry>

</datum>


## 闭包 {#closures-data}

具有自动管理数据块的即席函数，该数据块**捕获** {{ ref(page="types/closure.html#capture-modes") }}<sup>, 1</sup> 定义闭包的环境。例如，如果你有：

```rust
let y = ...;
let z = ...;

with_closure(move |x| x + y.f() + z); // y 和 z 被移动到闭包实例（类型为 C1）中
with_closure(     |x| x + y.f() + z); // y 和 z 被闭包实例（类型为 C2）引用
```

那么传递给 `with_closure()` 的生成的匿名闭包类型 `C1` 和 `C2` 将如下所示：

<!-- NEW ENTRY -->
<datum class="doublespaced">
    <name><code>move |x| x + y.f() + z</code></name>
    <visual>
       <framed class="any" style="width: 100px;"><code>Y</code></framed>
       <framed class="any" style="width: 50px;"><code>Z</code></framed>
    </visual>
    <zoom>匿名闭包类型 C1</zoom>
    <!-- <description>也产生匿名的 <br><code>f<sub>c1</sub> (c: C1, x: T)</code>。细节取决于<br>允许哪个 <code>FnOnce</code>, <code>FnMut</code>, <code>Fn</code>。</description> -->
</datum>


<!-- NEW ENTRY -->
<datum class="">
    <name><code>|x| x + y.f() + z</code></name>
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
    </visual>
    <zoom>匿名闭包类型 C2</zoom>
    <memory-entry>
        <memory-link style="left:44%;">|</memory-link>
        <memory class="anymem">
            <framed class="any" style="width: 30px;"><code>Y</code></framed>
        </memory>
    </memory-entry>
    <memory-entry>
        <memory-link style="left:44%;">|</memory-link>
        <memory class="anymem">
            <framed class="any" style="width: 30px;"><code>Z</code></framed>
        </memory>
    </memory-entry>
    <!-- <description>类似，但通过引用<br>捕获上下文。细节可能<br>因涉及的类型而异。</description> -->
</datum>

<!-- 因为下面的描述太杂乱了，所以做了一点小 hack。 -->
<!-- <datum>
    <name>&nbsp;</name>
    <description>
    也产生匿名的 <code>fn</code>，例如 <code>f_c1 (C1, X)</code> 或 <br>
    <code>f_c2 (&C2, X)</code>。细节取决于支持哪个 <code>FnOnce</code>, <code>FnMut</code>, <code>Fn</code> ...<br>
    ，基于捕获类型的属性。
    </description>
</datum> -->

<blockquote>
<footnotes>

也产生匿名的 `fn`，例如 <code>f<sub>c1</sub>(C1, X)</code> 或 <code>f<sub>c2</sub>(&C2, X)</code>。细节取决于支持哪个 <code>FnOnce</code>、<code>FnMut</code>、<code>Fn</code> ...，这基于捕获类型的属性。

</footnotes>
</blockquote>


<footnotes>

<sup>1</sup> 简单来说，闭包是一个方便编写的“迷你函数”，它接受参数，*并且*需要一些局部变量来完成其工作。因此，它是一个类型（包含所需的局部变量）和一个函数。*“捕获环境”*是一种花哨的说法，用来描述闭包类型如何持有这些局部变量，要么是*通过移动的值*，要么是*通过指针*。有关各种含义，请参见**API 中的闭包** {{ below(target="#closures-in-apis") }}。

</footnotes>


## 标准库类型 {#standard-library-types}


Rust 的标准库将上述原始类型组合成具有特殊语义的有用类型，例如：



<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>Option&lt;T&gt;</code> {{ std(page="std/option/enum.Option.html") }}</name>
    <visual class="enum" style="text-align: left;">
        <pad><code>标签</code></pad>
    </visual>
    <andor>或</andor>
    <visual class="enum">
        <pad><code>标签</code></pad>
        <framed class="any" style="width: 100px;">
            <code>T</code>
        </framed>
    </visual>
    <description>对于某些 T，标签可能被省略，<br>例如 <code>NonNull</code>。{{ std(page="std/ptr/struct.NonNull.html") }}</description>
</datum>



<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>Result&lt;T, E&gt;</code> {{ std(page="std/result/enum.Result.html") }}</name>
    <visual class="enum" style="text-align: left;">
        <pad><code>标签</code></pad>
        <framed class="any" style="width: 50px;">
            <code>E</code>
        </framed>
    </visual>
    <andor>或</andor>
    <visual class="enum" style="text-align: left;">
        <pad><code>标签</code></pad>
        <framed class="any" style="width: 100px;">
            <code>T</code>
        </framed>
    </visual>
    <description>要么是某个错误 <code>E</code>，要么是<br><code>T</code> 类型的值。</description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>ManuallyDrop&lt;T&gt;</code> {{ std(page="std/mem/struct.ManuallyDrop.html") }}</name>
    <visual>
           <framed class="any unsized"  style="width: 100px;"><code>T</code></framed>
    </visual>
    <description>阻止 <code>T::drop()</code> 被<br>调用。</description>
</datum>

<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>AtomicUsize</code> {{ std(page="std/sync/atomic/index.html") }}</name>
    <visual class="atomic">
        <ptr class="atomic">
            <code>usize</code><sub>2/4/8</sub>
        </ptr>
    </visual>
    <description>其他原子类型类似。</description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>MaybeUninit&lt;T&gt;</code><span style="position: absolute;"> {{ std(page="std/mem/union.MaybeUninit.html") }}</span></name>
    <visual class="enum">
        <framed class="uninit" style="width: 100px;">
            <code>未̼̟̔͛定̥͕͐͞义̛̲͔̦̳̑̓̐</code>
        </framed>
    </visual>
    <andor>不安全或</andor>
    <visual class="enum">
        <framed class="any" style="width: 100px;">
            <code>T</code>
        </framed>
    </visual>
    <description>未初始化的内存或<br>某个 <code>T</code>。处理未初始化<br>数据的唯一合法方式。</description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>PhantomData&lt;T&gt;</code> {{ std(page="std/marker/struct.PhantomData.html") }}</name>
    <visual style="width: 15px;" class="zst">
        <code></code>
    </visual>
    <description>零大小的辅助类型，用于持有<br>否则未使用的生命周期。</description>
</datum>



<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>Pin&lt;P&gt;</code> {{ std(page="std/pin/struct.Pin.html") }}</name>
    <visual style="width: 90px;">
        <framed class="any" style="width: 80px;">
           <code>P</code>
        </framed>
    </visual>
    <memory-entry class="double">
        <memory-link style="left:24%;">|</memory-link>
        <memory class="anymem pinned" style="opacity: 0.8; font-size: 11pt;">
            <span style="position:absolute; right: -14px; top: -16px;">📌</span>
            <framed class="any" style="width: 130px;"><code>P::Deref</code></framed>
        </memory>
    </memory-entry>
    <!-- <description>Signals <code>*p</code> this <code>P</code> pins<br>will never(!) move again<br> unless it's <code>Unpin</code>.{{ std(page="std/marker/trait.Unpin.html") }}</description> -->
    <description>表示 <code>P</code> 的目标被“永远”固定<br>即使超过 <code>Pin</code> 的生命周期。内部值<br>不可移出（但可移入新值），<br>除非是 <code>Unpin</code>。{{ std(page="std/marker/trait.Unpin.html") }}</description>
</datum>

> {{bad()}} 所有描述仅用于**说明**目的。
> 这些字段应存在于最新的 `stable` 版本中，但 Rust 对其布局不做任何保证，除非文档允许，否则您不得
> 尝试*不安全地*访问任何内容。

{{ tablesep() }}


#### Cell 类型


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>UnsafeCell&lt;T&gt;</code> {{ std(page="std/cell/struct.UnsafeCell.html") }}</name>
    <visual class="cell">
           <framed class="any unsized"><code>T</code></framed>
    </visual>
    <description>允许别名可变性的<br>神奇类型。</description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>Cell&lt;T&gt;</code> {{ std(page="std/cell/struct.Cell.html") }}</name>
    <visual>
           <framed class="any unsized celled"><code>T</code></framed>
    </visual>
    <description>允许 <code>T</code><br>移入和<br>移出。</description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>RefCell&lt;T&gt;</code> {{ std(page="std/cell/struct.RefCell.html") }}</name>
    <visual>
        <sized class="celled"><code>borrowed</code></sized>
        <framed class="any unsized celled"><code>T</code></framed>
    </visual>
    <description>也支持 <code>T</code> 的动态<br>
    借用。与 <code>Cell</code> 一样，<br>
    这是 <code>Send</code>，但不是 <code>Sync</code>。</description>
</datum>



<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>OnceCell&lt;T&gt;</code> {{ std(page="std/cell/struct.OnceCell.html") }}</name>
    <div class="celled" style="border-radius: 8px;">
    <visual class="enum" style="text-align: left;">
        <pad><code>标签</code></pad>
    </visual>
    <andor>或</andor>
    <visual class="enum">
        <pad><code>标签</code></pad>
        <framed class="any" style="width: 80px;">
            <code>T</code>
        </framed>
    </visual>
    </div>
    <description>最多初始化一次。</description>
</datum>


<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>LazyCell&lt;T, F&gt;</code> {{ std(page="std/cell/struct.LazyCell.html") }}</name>
    <div class="celled" style="border-radius: 8px;">
    <visual class="enum">
        <pad><code>标签</code></pad>
        <framed class="any" style="width: 80px;">
            <code>Uninit&lt;F&gt;</code>
        </framed>
    </visual>
    <andor>或</andor>
    <visual class="enum">
        <pad><code>标签</code></pad>
        <framed class="any" style="width: 80px;">
            <code>Init&lt;T&gt;</code>
        </framed>
    </visual>
    <andor>或</andor>
    <visual class="enum">
        <pad><code>标签</code></pad>
        <framed class="any" style="width: 80px;">
            <code>Poisoned</code>
        </framed>
    </visual>
    </div>
    <description>在首次访问时初始化。</description>
</datum>



{{ tablesep() }}


#### 保序集合



<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>Box&lt;T&gt;</code> {{ std(page="std/boxed/struct.Box.html") }}</name>
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <payload>
            <code>meta</code><sub>2/4/8</sub>
        </payload>
    </visual>
    <memory-entry>
        <memory-link style="left:49%;">|</memory-link>
        <memory class="heap">
        <framed class="any unsized"><code>T</code></framed>
        </memory>
    </memory-entry>
    <description>对于某些 <code>T</code>，栈代理可能携带<br>元数据{{ above (target="#custom-types") }}（例如 <code>Box<[T]></code>）。</description>
</datum>

<spacer>
</spacer>

<!-- NEW ENTRY -->
<datum>
    <name><code>Vec&lt;T&gt;</code> {{ std(page="std/vec/struct.Vec.html") }}</name>
    <!-- 由于某种原因，我们需要为移动设备设置宽度，以防止换行 -->
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <sized>
            <code>len</code><sub>2/4/8</sub>
        </sized>
        <sized>
            <code>capacity</code><sub>2/4/8</sub>
        </sized>
    </visual>
    <memory-entry class="double">
        <memory-link style="left:25%;">|</memory-link>
        <memory class="heap capacity">
            <div>
                <framed class="any t"><code>T</code></framed>
                <framed class="any t"><code>T</code></framed>
                <note>… len</note>
            </div>
            <capacity>← <note>capacity</note> →</capacity>
        </memory>
    </memory-entry>
    <description>常规的<i>可增长数组</i>向量，包含单一类型。</description>
</datum>

<spacer>
</spacer>


<!-- NEW ENTRY -->
<datum>
    <name><code>LinkedList&lt;T&gt;</code> {{ std(page="std/collections/struct.LinkedList.html") }}{{ esoteric() }} </name>
    <!-- 由于某种原因，我们需要为移动设备设置宽度，以防止换行 -->
    <visual>
        <ptr>
           <code>head</code><sub>2/4/8</sub>
        </ptr>
        <ptr>
           <code>tail</code><sub>2/4/8</sub>
        </ptr>
        <sized>
            <code>len</code><sub>2/4/8</sub>
        </sized>
    </visual>
    <memory-entry style="width: 265px; left:0%; display: block;">
        <memory-link style="left:25%;">|</memory-link>
        <memory-link style="left:50%;">|</memory-link>
        <memory class="heap capacity">
            <ptr>
            <code>next</code><sub>2/4/8</sub>
            </ptr>
            <ptr>
            <code>prev</code><sub>2/4/8</sub>
            </ptr>
            <framed class="any t"><code>T</code></framed>
        </memory>
    </memory-entry>
    <description>元素 <code>head</code> 和 <code>tail</code> 要么是 <code>null</code>，要么指向堆上的节点。<br> 每个节点可以指向其 <code>prev</code> 和 <code>next</code> 节点。<br>吞噬你的缓存（看看这东西！）；除非你<br>显然必须使用，否则不要用。{{ bad() }} </description>
</datum>


<spacer>
</spacer>



<!-- NEW ENTRY -->
<datum>
    <name><code>VecDeque&lt;T&gt;</code> {{ std(page="std/collections/struct.VecDeque.html") }}</name>
    <!-- 由于某种原因，我们需要为移动设备设置宽度，以防止换行 -->
    <visual>
        <sized>
            <code>head</code><sub>2/4/8</sub>
        </sized>
        <sized>
            <code>len</code><sub>2/4/8</sub>
        </sized>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <sized>
            <code>capacity</code><sub>2/4/8</sub>
        </sized>
    </visual>
    <memory-entry></memory-entry>
    <memory-entry></memory-entry>
    <memory-entry class="double">
        <memory-link style="left:25%;">|</memory-link>
        <memory class="heap capacity">
            <div>
                <!-- <framed class="any t"><code>T<sub>x</sub></code></framed> -->
                <framed class="any t"><code>T</code></framed>
                <!-- <framed class="any t"><code>T</code></framed> -->
                <note>… 空 …</note>
                <framed class="any t"><code>T&#x2063;<sup>H</sup></code></framed>
            </div>
            <capacity>← <note>capacity</note> →</capacity>
        </memory>
    </memory-entry>
    <description>索引 <code>head</code> 在作为环形缓冲区的数组中选择。这意味着内容可能<br>不连续，并且中间为空，如上所示。</description>
</datum>



{{ tablesep() }}

#### 其他集合


<!-- NEW ENTRY -->
<datum>
    <name><code>HashMap&lt;K, V&gt;</code> {{ std(page="std/collections/struct.HashMap.html") }}</name>
    <!-- 由于某种原因，我们需要为移动设备设置宽度，以防止换行 -->
    <visual>
        <sized>
            <code>bmask</code><sub>2/4/8</sub>
        </sized>
        <ptr>
           <code>ctrl</code><sub>2/4/8</sub>
        </ptr>
        <sized>
            <code>left</code><sub>2/4/8</sub>
        </sized>
        <sized>
            <code>len</code><sub>2/4/8</sub>
        </sized>
    </visual>
    <memory-entry></memory-entry>
    <memory-entry style="width: 265px; left:-5%">
        <memory-link style="left:25%;">|</memory-link>
        <memory class="heap oversimplified">
            <framed class="any t"><code>K:V</code></framed>
            <framed class="any t"><code>K:V</code></framed>
            …
            <framed class="any t"><code>K:V</code></framed>
            …
            <framed class="any t"><code>K:V</code></framed>
            <capacity><note style="font-weight: bolder;">过于简化！</note></capacity>
        </memory>
    </memory-entry>
    <description>根据哈希值将键和值存储在堆上，<a href="https://www.youtube.com/watch?v=ncHmEUmJZf4">SwissTable</a> <br> 实现通过 <a href="https://github.com/rust-lang/hashbrown">hashbrown</a>。<code>HashSet</code> {{ std(page="std/collections/struct.HashSet.html") }} 与 <code>HashMap</code> 相同，<br>只是类型 <code>V</code> 消失了。堆视图被严重简化了。{{bad()}} </description>
</datum>


<spacer>
</spacer>

<!-- NEW ENTRY -->
<datum>
    <name><code>BinaryHeap&lt;T&gt;</code> {{ std(page="std/collections/struct.BinaryHeap.html") }}</name>
    <!-- 由于某种原因，我们需要为移动设备设置宽度，以防止换行 -->
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <sized>
            <code>capacity</code><sub>2/4/8</sub>
        </sized>
        <sized>
            <code>len</code><sub>2/4/8</sub>
        </sized>
    </visual>
    <memory-entry style="width: 265px">
        <memory-link style="left:20%;">|</memory-link>
        <memory class="heap capacity">
            <div>
                <framed class="any t"><code>T&#x2063;<sup style="color:black; font-weight: bolder;">0</sup></code></framed>
                <framed class="any t" style="background-color: #f9b172;"><code>T&#x2063;<sup style="color:black; font-weight: bolder;">1</sup></code></framed>
                <framed class="any t" style="background-color: #f9b172;"><code>T&#x2063;<sup style="color:black; font-weight: bolder;">1</sup></code></framed>
                <framed class="any t" style="background-color: #f9d372;"><code>T&#x2063;<sup style="color:black; font-weight: bolder;">2</sup></code></framed>
                <framed class="any t" style="background-color: #f9d372;"><code>T&#x2063;<sup style="color:black; font-weight: bolder;">2</sup></code></framed>
                <note>… len</note>
            </div>
            <capacity>← <note>capacity</note> →</capacity>
        </memory>
    </memory-entry>
    <description>堆存储为数组，每层有 <code>2<sup>N</sup></code> 个元素。每个 <code>T</code> <br>
    在下一层可以有两个子节点。每个 <code>T</code> 都比其<br>
    子节点大。</description>
</datum>



#### 自有字符串


<!-- NEW ENTRY -->
<datum>
    <name><code>String</code> {{ std(page="std/string/struct.String.html") }}</name>
    <!-- 由于某种原因，我们需要为移动设备设置宽度，以防止换行 -->
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <sized>
            <code>capacity</code><sub>2/4/8</sub>
        </sized>
        <sized>
            <code>len</code><sub>2/4/8</sub>
        </sized>
    </visual>
    <memory-entry class="double">
        <memory-link style="left:25%;">|</memory-link>
        <memory class="heap">
            <div>
                <byte class="bytes"><code>U</code></byte>
                <byte class="bytes"><code>T</code></byte>
                <byte class="bytes"><code>F</code></byte>
                <byte class="bytes"><code>-</code></byte>
                <byte class="bytes"><code>8</code></byte>
                <note>… len</note>
            </div>
            <capacity>← <note>capacity</note> →</capacity>
        </memory>
    </memory-entry>
    <description>注意 <code>String</code> 与 <code>&str</code> 和 <code>&[char]</code> 的区别。</description>
</datum>

<spacer>
</spacer>

<!-- NEW ENTRY -->
<datum>
    <name><code>CString</code> {{ std(page="std/ffi/struct.CString.html") }}</name>
    <!-- 由于某种原因，我们需要为移动设备设置宽度，以防止换行 -->
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <sized>
            <code>len</code><sub>2/4/8</sub>
        </sized>
    </visual>
    <memory-entry class="double">
        <memory-link style="left:25%;">|</memory-link>
        <memory class="heap">
            <div>
                <byte class="bytes"><code>A</code></byte>
                <byte class="bytes"><code>B</code></byte>
                <byte class="bytes"><code>C</code></byte>
                <note>… len …</note>
                <byte class="bytes"><code>∅</code></byte>
            </div>
        </memory>
    </memory-entry>
    <description>以 NUL 结尾，但中间没有 NUL。</description>
</datum>


<spacer>
</spacer>

<!-- NEW ENTRY -->
<datum>
    <name><code>OsString</code> {{ std(page="std/ffi/struct.OsString.html") }}</name>
    <!-- 由于某种原因，我们需要为移动设备设置宽度，以防止换行 -->
    <visual>
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <sized>
            <code>capacity</code><sub>2/4/8</sub>
        </sized>
        <sized>
            <code>len</code><sub>2/4/8</sub>
        </sized>
    </visual>
    <memory-entry class="double">
        <memory-link style="left:25%;">|</memory-link>
        <memory class="heap">
            <div>
                <byte class="bytes"><code> </code></byte>
                <byte class="bytes"><code> </code></byte>
                /
                <word class="bytes"><code> </code></word>
                <word class="bytes"><code> </code></word>
            </div>
        </memory>
    </memory-entry>
    <description>封装了操作系统如何<br>表示路径。</description>
</datum>


{{ tablesep() }}

#### 共享所有权

如果类型不包含用于 `T` 的 `Cell`，这些类型通常与上述 `Cell` 类型之一结合使用，以允许事实上的共享可变性。

<!-- NEW ENTRY -->
<datum>
    <name><code>Rc&lt;T&gt;</code> {{ std(page="std/rc/struct.Rc.html") }}</name>
    <visual style="width: 180px;">
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <payload>
            <code>meta</code><sub>2/4/8</sub>
        </payload>
    </visual>
    <div>
        <memory-entry class="quad">
            <memory-link style="left:15%;">|</memory-link>
            <memory class="heap">
                <sized class="celled"><code>strng</code><sub>2/4/8</sub></sized>
                <sized class="celled"><code>weak</code><sub>2/4/8</sub></sized>
                <framed class="any unsized"><code>T</code></framed>
            </memory>
        </memory-entry>
    </div>
    <description>在同一线程中共享 <code>T</code> 的所有权。需要嵌套 <code>Cell</code>
    <br>或 <code>RefCell</code> 来允许修改。既不是 <code>Send</code> 也不是 <code>Sync</code>。</description>
</datum>


<!-- NEW ENTRY -->
<datum>
    <name><code>Arc&lt;T&gt;</code> {{ std(page="std/sync/struct.Arc.html") }}</name>
    <visual style="width: 180px;">
        <ptr>
           <code>ptr</code><sub>2/4/8</sub>
        </ptr>
        <payload>
            <code>meta</code><sub>2/4/8</sub>
        </payload>
    </visual>
    <div style="width: 0px;">
        <memory-entry class="quad">
            <memory-link style="left:15%;">|</memory-link>
            <memory class="heap">
                <sized class="atomicx"><code>strng</code><sub>2/4/8</sub></sized>
                <sized class="atomicx"><code>weak</code><sub>2/4/8</sub></sized>
                <framed class="any unsized"><code>T</code></framed>
            </memory>
        </memory-entry>
    </div>
    <description>同上，但如果包含的<br>
    <code>T</code> 本身是 <code>Send</code> 和 <code>Sync</code>，则允许在线程间共享。</description>
</datum>

<br>

<!-- NEW ENTRY -->
<datum>
    <name><code>Mutex&lt;T&gt;</code> {{ std(page="std/sync/struct.Mutex.html") }} / <code>RwLock&lt;T&gt;</code> {{ std(page="std/sync/struct.RwLock.html") }}</name>
    <visual style="width: 230px;">
        <payload><code>inner</code></payload>
        <sized class="atomicx"><code>poison</code><sub>2/4/8</sub></sized>
        <framed class="any unsized celled"><code>T</code></framed>
    </visual>
    <description>内部字段取决于平台。需要放在<br> <code>Arc</code> 中才能在解耦的线程间共享，<br>或者通过 <code>scope()</code> {{ std(page="std/thread/fn.scope.html") }} 用于作用域线程。
    </description>
</datum>

<spacer>
</spacer>
<spacer>
</spacer>

<!-- NEW ENTRY -->
<datum class="spaced">
    <name><code>Cow&lt;'a, T&gt;</code> {{ std(page="std/borrow/enum.Cow.html") }}</name>
    <visual class="enum" style="text-align: left;">
        <pad><code>标签</code></pad>
        <framed class="any unsized" style="width: 100px; text-align: center;">
            <code>T::Owned</code>
        </framed>
    </visual>
    <andor>或</andor>
    <visual class="enum" style="text-align: left;">
        <pad><code>标签</code></pad>
        <framed class="ptr" style="width: 50px;">
           <code>ptr</code><sub>2/4/8</sub>
        </framed>
    </visual>
    <div>
        <memory-entry style="width: 40px;"></memory-entry>
        <memory-entry>
            <memory-link style="left:15%;">|</memory-link>
            <memory class="anymem">
                <framed class="any unsized"><code>T</code></framed>
            </memory>
        </memory-entry>
    </div>
    <description>持有一个对某个 <code>T</code> 的只读引用，<br>或者拥有其 <code>ToOwned</code> {{ std( page = "std/borrow/trait.ToOwned.html") }} <br>的等价物。</description>
</datum>




---


# 标准库


## 一行代码 {#one-liners}

一些常见但容易忘记的代码片段。更多信息请参见 **Rust Cookbook** {{ link(url="https://rust-lang-nursery.github.io/rust-cookbook/") }}。


<!--
非常欢迎对此部分的PR。想法是：
- 目前应该只包含 `std`，不含第三方库（也许 `rand` 是个例外？）
- “大多数人”都应该遇到过这个问题
- 不仅仅是“显而易见”的结构体上的一个简单方法（例如，通过 `x.sort()` 对切片进行排序可能太明显了。）
-->

<!-- 在小屏幕上创建一个水平滚动区域以保持布局 -->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">


<tabs>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-api-2" name="tab-api-sized" checked>
<label for="tab-api-2"><b>字符串</b></label>
<panel><div class="color-header one-liners cheats">

| 意图                                                                                                                                                      | 代码片段                                     |
| --------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------- |
| 连接字符串（任何实现了 `Display`{{ below(target="#string-output") }} 的类型）。{{ std(page="std/fmt/index.html") }} <sup>1</sup>  {{ edition(ed="'21") }} | `format!("{x}{y}")`                          |
| 追加字符串（任何 `Display` 到任何 `Write`）。{{ edition(ed="'21") }} {{ std(page="std/fmt/index.html#write") }}                                           | `write!(x, "{y}")`                           |
| 按分隔符模式分割。{{ std(page="std/str/pattern/trait.Pattern.html") }} {{ link(url="https://stackoverflow.com/a/38138985") }}                             | `s.split(pattern)`                           |
| {{ tab() }} … 使用 `&str`                                                                                                                                 | `s.split("abc")`                             |
| {{ tab() }} … 使用 `char`                                                                                                                                 | `s.split('/')`                               |
| {{ tab() }} … 使用闭包                                                                                                                                    | `s.split(char::is_numeric)`                  |
| 按空白分割。{{ std(page="std/primitive.str.html#method.split_whitespace") }}                                                                              | `s.split_whitespace()`                       |
| 按换行符分割。{{ std(page="std/primitive.str.html#method.lines") }}                                                                                       | `s.lines()`                                  |
| 按正则表达式分割。{{ link(url="https://docs.rs/regex/latest/regex/struct.Regex.html#method.split") }} <sup>2</sup>                                        | ` Regex::new(r"\s")?.split("one two three")` |

<footnotes>

<sup>1</sup> 会分配内存；如果 `x` 或 `y` 之后不再使用，请考虑使用 `write!` 或 `std::ops::Add`。<br>
<sup>2</sup> 需要 [regex](https://crates.io/crates/regex) crate。

</footnotes>


</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-api-1" name="tab-api-sized">
<label for="tab-api-1"><b>I/O</b></label>
<panel><div class="color-header one-liners cheats">

| 意图                                                                  | 代码片段                                                                 |
| --------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| 创建一个新文件 {{ std(page="std/fs/struct.File.html#method.open") }}  | `File::create(PATH)?`                                                    |
| {{ tab() }}  同上，通过 OpenOptions                                   | `OpenOptions::new().create(true).write(true).truncate(true).open(PATH)?` |
| 将文件读取为 `String` {{ std(page="std/fs/fn.read_to_string.html") }} | `read_to_string(path)?`                                                  |

<!-- <footnotes>

<sup>*</sup> 这里空间有点不够，<code>t</code> 表示 true。

</footnotes> -->

</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-api-4" name="tab-api-sized">
<label for="tab-api-4"><b>宏</b></label>
<panel><div class="color-header one-liners cheats">

| 意图                                        | 代码片段                                               |
| ------------------------------------------- | ------------------------------------------------------ |
| 带可变参数的宏                              | `macro_rules! var_args { ($($args:expr),*) => {{ }} }` |
| {{ tab() }} 使用 `args`，例如多次调用 `f`。 | {{ tab() }} ` $( f($args); )*`                         |

</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-api-5" name="tab-api-sized">
<label for="tab-api-5"><b>转换 {{ hot() }}</b></label>
<panel><div class="color-header one-liners cheats">

| 起始类型                | 资源                                                                           |
| ----------------------- | ------------------------------------------------------------------------------ |
| `Option<T> -> …`        | 参见 [基于类型的速查表](https://upsuper.github.io/rust-cheatsheet/)            |
| `Result<T, R> -> …`     | 参见 [基于类型的速查表](https://upsuper.github.io/rust-cheatsheet/)            |
| `Iterator<Item=T> -> …` | 参见 [基于类型的速查表](https://upsuper.github.io/rust-cheatsheet/)            |
| `&[T] -> …`             | 参见 [基于类型的速查表](https://upsuper.github.io/rust-cheatsheet/)            |
| `Future<T> -> …`        | 参见 [Futures 速查表](https://rufflewind.com/img/rust-futures-cheatsheet.html) |

<!-- <footnotes>

<sup>*</sup> 这里空间有点不够，<code>t</code> 表示 true。

</footnotes> -->

</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-api-3" name="tab-api-sized">
<label for="tab-api-3"><b>深奥用法</b>{{ esoteric() }}</label>
<panel><div class="color-header one-liners cheats">

| 意图                                                                                                                 | 代码片段                                                                              |
| -------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| 更清晰的闭包捕获                                                                                                     | <code>wants_closure({ let c = outer.clone(); move &vert;&vert; use_clone(c) })</code> |
| 修复 ‘`try`’ 闭包中的类型推断                                                                                        | <code>iter.try_for_each(&vert;x&vert; { Ok::<(), Error>(()) })?;</code>               |
| 如果 `T` 是 Copy，则迭代*并*编辑 `&mut [T]`。                                                                        | `Cell::from_mut(mut_slice).as_slice_of_cells()`                                       |
| 获取带长度的子切片。                                                                                                 | `&original_slice[offset..][..length]`                                                 |
| 用于确保 trait `T` 是**对象安全**的金丝雀代码。{{ ref(page="items/traits.html#object-safety")}}                      | `const _: Option<&dyn T> = None;`                                                     |
| 用于统一类型的*Semver 技巧*。{{ link(url="https://github.com/dtolnay/semver-trick") }}                               | `Cargo.toml` 中的 `my_crate = "next.version"` + 重新导出类型。                        |
| 在自己的 crate 内部使用宏。{{ link(url="https://users.rust-lang.org/t/use-macro-inside-proc-macro-crate/61095/4") }} | `macro_rules! internal_macro {}` 与 `pub(crate) use internal_macro;`                  |


</div></panel></tab>


</tabs>


</div></div>



## 线程安全 {#thread-safety}

假设你在线程 1 中持有一些变量，并且想要将它们**移动**到线程 2，或者将它们的**引用**传递给线程 3。这是否被允许分别由 **`Send`**{{ std(page="std/marker/trait.Send.html") }} 和 **`Sync`**{{ std(page="std/marker/trait.Sync.html") }} 决定：

{{ tablesep() }}

<!-- 在小屏幕上创建一个水平滚动区域以保持布局 -->
<div style="overflow:auto; padding-top: 10px;">
<div style="min-width: 100%; width: 650px; ">
<div class="color-header number">


<threading-section>
    <thread-row>
        <thread-backdrop><hr></thread-backdrop>
        <values>
            <value class="both" style="left: 57px;"><thread-link>|<br>|<br>|</thread-link>&nbsp;Mutex&lt;u32&gt;</value>
            <value class="one" style="left: 97.5px;"><thread-link>|<br>|<br>|</thread-link>&nbsp;Cell&lt;u32&gt;</value>
            <value class="one" style="left: 137.5px;"><thread-link>|<br>|<br>|</thread-link>&nbsp;MutexGuard&lt;u32&gt;</value>
            <value class="none" style="left: 177.5px;"><thread-link>|<br>|<br>|</thread-link>&nbsp;Rc&lt;u32&gt;</value>
        </values>
        <subtext><blank-background>线程 1</blank-background></subtext>
    </thread-row>
    <thread-row>
        <thread-backdrop><hr></thread-backdrop>
        <values>
            <value class="both" style="left: 77px;">&nbsp;Mutex&lt;u32&gt;</value>
            <value class="one" style="left: 117.5px;">&nbsp;Cell&lt;u32&gt;</value>
            <value class="disabled" style="left: 157.5px;">&nbsp;MutexGuard&lt;u32&gt;</value>
            <value class="disabled" style="left: 197.5px;">&nbsp;Rc&lt;u32&gt;</value>
        </values>
        <subtext><blank-background>线程 2</blank-background></subtext>
    </thread-row>
    <thread-row>
        <thread-backdrop><hr></thread-backdrop>
        <values>
            <value class="both" style="left: 77px;"><b>&</b>Mutex&lt;u32&gt;</value>
            <value class="disabled" style="left: 117.5px;"><b>&</b>Cell&lt;u32&gt;</value>
            <value class="one" style="left: 157.5px;"><b>&</b>MutexGuard&lt;u32&gt;</value>
            <value class="disabled" style="left: 197.5px;"><b>&</b>Rc&lt;u32&gt;</value>
        </values>
        <subtext><blank-background>线程 3</blank-background></subtext>
    </thread-row>
</threading-section>

</div>
</div>
</div>

{{ tablesep() }}

<div class="color-header sendsync">

| 示例                  | 解释                                                                |
| --------------------- | ------------------------------------------------------------------- |
| **`Mutex<u32>`**      | 既是 `Send` 也是 `Sync`。你可以安全地将其传递或借给另一个线程。     |
| **`Cell<u32>`**       | `Send`，但不是 `Sync`。可移动，但其引用将允许并发的非原子写入。     |
| **`MutexGuard<u32>`** | `Sync`，但不是 `Send`。锁与线程绑定，但其引用的使用不允许数据竞争。 |
| **`Rc<u32>`**         | 两者都不是，因为它是一个带有非原子计数器的、易于克隆的堆代理。      |

</div>

{{ tablesep() }}

<!-- 无耻地从 https://www.reddit.com/r/rust/comments/ctdkyr/understanding_sendsync/exk8grg/ 窃取 -->
<table class="sendsync">
    <thead>
        <tr><th>Trait</th><th><code>Send</code></th><th><code>!Send</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>Sync</code></td><td><i>大多数类型</i> … <code>Arc&lt;T&gt;</code><sup>1,2</sup>, <code>Mutex&lt;T&gt;</code><sup>2</sup></td><td><code>MutexGuard&lt;T&gt;</code><sup>1</sup>, <code>RwLockReadGuard&lt;T&gt;</code><sup>1</sup></td></tr>
        <tr><td><code>!Sync</code></td><td><code>Cell&lt;T&gt;</code><sup>2</sup>, <code>RefCell&lt;T&gt;</code><sup>2</sup></td><td><code>Rc&lt;T&gt;</code>, <code>&dyn Trait</code>, <code>*const T</code><sup>3</sup></td></tr>
    </tbody>
</table>

<footnotes>

<sup>1</sup> 如果 `T` 是 `Sync`。<br>
<sup>2</sup> 如果 `T` 是 `Send`。<br>
<sup>3</sup> 如果你需要发送一个裸指针，创建一个新类型 `struct Ptr(*const u8)` 并 `unsafe impl Send for Ptr {}`。只需确保你*可以*发送它。

</footnotes>

{{ tablesep() }}

<div class="color-header sendsync">

| 何时 ...                                                                    | ... 是 Send？                                                                                      |
| --------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| `T`                                                                         | 所有包含的字段都是 `Send`，或者 `unsafe` 实现。                                                    |
| {{ tab() }}`struct S { ... }`                                               | 所有字段都是 `Send`，或者 `unsafe` 实现。                                                          |
| {{ tab() }}`struct S<T> { ... }`                                            | 所有字段都是 `Send` 并且 T 是 `Send`，或者 `unsafe` 实现。                                         |
| {{ tab() }}`enum E { ... }`                                                 | 所有变体中的所有字段都是 `Send`，或者 `unsafe` 实现。                                              |
| `&T`                                                                        | 如果 `T` 是 `Sync`。                                                                               |
| <code>&vert;&vert; {}</code>                                                | 如果所有*捕获*都是 `Send`，则闭包是 `Send`。                                                       |
| {{ tab() }} <code>&vert;x&vert; { }</code>                                  | `Send`，与 `x` 无关。                                                                              |
| {{ tab() }} <code>&vert;x&vert; { Rc::new(x) }</code>                       | `Send`，因为仍然没有捕获任何东西，尽管 `Rc` 不是 `Send`。                                          |
| {{ tab() }} <code>&vert;x&vert; { x + y }</code>                            | 仅当 `y` 是 `Send` 时才是 `Send`。                                                                 |
| <code>async { }</code>                                                      | 如果没有任何 `!Send` 类型跨越 `.await` 点，则 Future 是 `Send`。                                   |
| {{ tab() }} <code>async { Rc::new() }</code>                                | `Future` 是 `Send`，因为 `!Send` 类型 `Rc` 没有跨越 `.await`。                                     |
| {{ tab() }} <code>async { rc; x.await; rc; }</code> <sup>1</sup>            | `Future` 是 `!Send`，因为 `Rc` 跨越了 `.await` 点。                                                |
| <code>async &vert;&vert; { }</code> {{ experimental()}}                     | 异步闭包 `Send` 如果所有捕获都是 `Send`，结果的 `Future` 也是 `Send` 如果内部也没有 `!Send` 类型。 |
| {{ tab() }} <code>async &vert;x&vert; { x  + y }</code> {{ experimental()}} | 异步闭包 `Send` 如果 `y` 是 `Send`。Future `Send` 如果 `x` 和 `y` 是 `Send`。                      |

</div>

<footnotes>

<sup>1</sup> 这是一些伪代码，旨在传达要点，其思想是在一个 `.await` 点之前有一个 `Rc`，并在该点之后继续使用它。

</footnotes>


## 原子操作与缓存 {{ esoteric() }} {#atomics-cache} 

CPU 缓存、内存写入，以及原子操作如何影响它们。

<!-- 在小屏幕上创建一个水平滚动区域以保持布局 -->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">


<lifetime-section>
<lifetime-example>
    <memory-row style="cursor: default;">
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t">S</byte>
            <byte class="t">O</byte>
            <byte class="t">M</byte>
            <byte class="t">E</byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t">D</byte>
            <byte class="t">R</byte>
            <byte class="t">A</byte>
            <byte class="t">M</byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t">D</byte>
            <byte class="t">A</byte>
            <byte class="t">T</byte>
            <byte class="t">A</byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <line-comment>主内存</line-comment>
        </memory-backdrop>
    </memory-row>
</lifetime-example>
</lifetime-section>

<lifetime-section>
<lifetime-example>
    <memory-row style="cursor: default;">
        <memory-backdrop>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="cpu1">S</byte>
            <byte class="cpu1">O</byte>
            <byte class="cpu1">M</byte>
            <byte class="cpu1">E</byte>
            <container><tag>(E)</tag></container>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="cpu1">D</byte>
            <byte class="cpu1">A</byte>
            <byte class="cpu1">T</byte>
            <byte class="cpu1">A</byte>
            <container><tag>(S)</tag></container>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <line-comment>CPU1 缓存</line-comment>
        </memory-backdrop>
    </memory-row>
    <memory-row style="cursor: default;">
        <memory-backdrop style="margin-top: 4px;">
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="cpu2 borrowed">S</byte>
            <byte class="cpu2">R</byte>
            <byte class="cpu2">A</byte>
            <byte class="cpu2">M</byte>
            <container><tag>(M)</tag></container>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="cpu2">D</byte>
            <byte class="cpu2">A</byte>
            <byte class="cpu2">T</byte>
            <byte class="cpu2">A</byte>
            <container><tag>(S)</tag></container>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <line-comment>CPU2 缓存</line-comment>
        </memory-backdrop>
    </memory-row>
</lifetime-example>
</lifetime-section>

<!-- end overflow -->
</div>
</div>

<footnotes>

现代 CPU 不直接访问内存，只访问其缓存。每个 CPU 都有自己的缓存，比 RAM 快 100 倍，但小得多。它以**缓存行**的形式存在，{{ link(url="https://stackoverflow.com/questions/3928995/how-do-cache-lines-work") }} 是一些字节的*切片*窗口，用于跟踪它是否是主内存的独占 (E)、共享 (S) 或已修改 (M) {{ link(url="https://en.wikipedia.org/wiki/MESI_protocol") }} 视图。缓存之间相互通信以确保**缓存一致性 (coherence)**，{{ link(url="https://gfxcourses.stanford.edu/cs149/fall20content/media/cachecoherence/10_coherence.pdf")}} 即，“足够小”的数据将被所有其他 CPU“立即”看到，但这可能会使 CPU 停顿。

</footnotes>


<!-- 在小屏幕上创建一个水平滚动区域以保持布局 -->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

<lifetime-section>
<lifetime-example class="not-first">
    <memory-row style="cursor: default;">
        <memory-backdrop>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="cpu1">S</byte>
            <byte class="cpu1">O</byte>
            <byte class="cpu1">M</byte>
            <byte class="cpu1">E</byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="cpu1">D</byte>
            <byte class="cpu1 borrowed">X</byte>
            <byte class="cpu1">T</byte>
            <byte class="cpu1">A</byte>
            <container><tag>(M)</tag></container>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <line-comment>周期 1</line-comment>
        </memory-backdrop>
        <values class="freestanding">
            <value class="t byte2 maybe-borrowed" style="left: 96px;">O3</value>
        </values>
    </memory-row>
    <memory-row style="cursor: default;">
        <memory-backdrop style="margin-top: 4px;">
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="cpu1">S</byte>
            <byte class="cpu1">O</byte>
            <byte class="cpu1">M</byte>
            <byte class="cpu1 borrowed">4</byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="cpu2">D</byte>
            <byte class="cpu2">X</byte>
            <byte class="cpu2">T</byte>
            <byte class="cpu2">A</byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <line-comment>周期 2</line-comment>
        </memory-backdrop>
        <values class="freestanding">
            <value class="t byte2 borrowed" style="left: 96px;">23</value>
            <value class="stalled" style="left: 350px;">停顿</value>
        </values>
    </memory-row>
    <memory-row style="cursor: default;">
        <memory-backdrop style="margin-top: 4px;">
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="cpu1 borrowed">1</byte>
            <byte class="cpu1"></byte>
            <byte class="cpu1"></byte>
            <byte class="cpu1 borrowed">4</byte>
            <container><tag>(M)</tag></container>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="cpu2">D</byte>
            <byte class="cpu2">X</byte>
            <byte class="cpu2">T</byte>
            <byte class="cpu2 borrowed">Y</byte>
            <container><tag>(M)</tag></container>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <line-comment>周期 3</line-comment>
        </memory-backdrop>
        <values class="freestanding">
            <value class="t byte2 borrowed" style="left: 96px;">23</value>
        </values>
    </memory-row>
</lifetime-example>
</lifetime-section>

<!-- end overflow -->
</div>
</div>


<footnotes>

左：编译器*和*CPU 都可以自由地**重排**{{ link(url="https://en.wikipedia.org/wiki/Memory_ordering")}}并拆分读/写内存访问。即使你明确说了 `write(1); write(23); write(4)`，你的编译器也可能认为先写 `23` 是个好主意；此外，你的 CPU 可能坚持拆分写操作，先做 `3` 再做 `2`。这些步骤中的每一个都可能被 CPU2 通过 `unsafe` 的*数据竞争*观察到（甚至是*不可能的* `O3`）。重排对于锁也是致命的。右：半相关的，即使两个 CPU 不试图访问彼此的数据（例如，更新 2 个独立的变量），如果底层内存被 2 个缓存行映射（**伪共享**），它们仍然可能会经历显著的性能损失。{{ link(url="https://docs.kernel.org/kernel-hacking/false-sharing.html")}}

</footnotes>


<!-- 在小屏幕上创建一个水平滚动区域以保持布局 -->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

<lifetime-section>
<lifetime-example class="not-first">
    <memory-row style="cursor: default;">
        <memory-backdrop>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t">1</byte>
            <byte class="t">2</byte>
            <byte class="t">3</byte>
            <byte class="t">4</byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t">S</byte>
            <byte class="t">R</byte>
            <byte class="t">A</byte>
            <byte class="t">M</byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte class="t">D</byte>
            <byte class="t">X</byte>
            <byte class="t">T</byte>
            <byte class="t">Y</byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <byte></byte>
            <line-comment>主内存</line-comment>
        </memory-backdrop>
        <values class="freestanding">
            <value class="atomic byte2" style="left: 246px;">RA</value>
        </values>
    </memory-row>
    <memory-row style="cursor: default; margin-top: 40px;">
        <memory-backdrop style="margin-top: 4px;">
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="cpu2 borrowed">1</byte>
            <byte class="cpu2">R</byte>
            <byte class="cpu2">A</byte>
            <byte class="cpu2">M</byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <line-comment>周期 4</line-comment>
        </memory-backdrop>
        <values class="freestanding">
            <value class="atomic byte2" style="left: 246px;">RA</value>
        </values>
    </memory-row>
    <memory-row style="cursor: default; margin-top: 40px;">
        <memory-backdrop style="margin-top: 4px;">
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="cpu2 borrowed">1</byte>
            <byte class="cpu2">2</byte>
            <byte class="cpu2"></byte>
            <byte class="cpu2">M</byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <line-comment>周期 5</line-comment>
        </memory-backdrop>
        <values class="freestanding">
            <value class="atomic byte2 borrowed" style="left: 246px;">23</value>
        </values>
    </memory-row>
    <memory-row style="cursor: default; margin-top: 40px;">
        <memory-backdrop style="margin-top: 4px;">
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="cpu2 borrowed">1</byte>
            <byte class="cpu2">2</byte>
            <byte class="cpu2">3</byte>
            <byte class="cpu2 borrowed">4</byte>
            <container><tag>(M)</tag></container>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <byte class="hide"></byte>
            <line-comment>周期 6</line-comment>
        </memory-backdrop>
        <values class="freestanding">
            <value class="atomic byte2 borrowed" style="left: 246px;">23</value>
        </values>
    </memory-row>
</lifetime-example>
</lifetime-section>

<!-- end overflow -->
</div>
</div>


<footnotes>

原子操作通过做两件事来解决上述问题，它们 - 确保读/写/更新不会通过临时锁定其他 CPU 中的缓存行而被部分观察到， - 强制编译器和 CPU 都不要在其周围重排*“不相关”*的访问（即，充当**屏障**{{ std(page="std/sync/atomic/fn.fence.html")}}）。确保多个 CPU 对这些其他操作的相对顺序达成一致称为**内存模型一致性 (consistency)**。{{ link(url="https://gfxcourses.stanford.edu/cs149/winter19content/lectures/09_consistency/09_consistency_slides.pdf" )}} 这也带来了错失性能优化的代价。

</footnotes>


{{ tablesep() }}

> **注意** &mdash; 上述部分被大大简化了。虽然缓存一致性 (coherence) 和内存模型一致性 (consistency) 的问题是普遍存在的，但 CPU 架构在如何实现缓存和原子操作以及它们的性能影响方面差异很大。





{{ tablesep() }}

<div class="color-header atomics">

| {{ tab() }} A. 排序                                                                              | 解释                                                                    |
| ------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------- |
| **`Relaxed`** {{ std(page="std/sync/atomic/enum.Ordering.html#variant.Relaxed") }}               | 完全重排。不相关的读/写可以在原子操作周围自由地重新排序。               |
| **`Release`** {{ std(page="std/sync/atomic/enum.Ordering.html#variant.Release") }}<sup>, 1</sup> | 在写入时，确保由第三方 `Acquire` 加载的其他数据在此次写入之后可见。     |
| **`Acquire`** {{ std(page="std/sync/atomic/enum.Ordering.html#variant.Acquire") }}<sup>, 1</sup> | 在读取时，确保在第三方 `Release` 之前写入的其他数据在此次读取之后可见。 |
| **`SeqCst`** {{ std(page="std/sync/atomic/enum.Ordering.html#variant.SeqCst") }}                 | 原子操作周围不进行重排。所有不相关的读和写都保持在适当的一侧。          |

</div>

<footnotes>

<sup>1</sup> 需要明确的是，当与 2 个或更多 CPU 同步内存访问时，*所有*CPU都必须使用 `Acquire` 或 `Release`（或更强的）。写入者必须确保它希望*释放*到内存的所有其他数据都在原子信号之前，而希望*获取*这些数据的读取者必须确保它们的其他读取仅在原子信号之后完成。

</footnotes>





## 迭代器 {#iterators}

处理集合中的元素。

<tabs class="color-header iterators">

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-trait-iter-p0" name="tab-group-trait-iter" checked>
<label for="tab-trait-iter-p0"><b>基础</b></label>
<panel><div>


广义上讲，有四种集合迭代的*风格*：

| 风格                      | 描述                                                                                                                   |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `for x in c { ... }`      | *命令式*，在有副作用、相互依赖或需要提早中断流程时很有用。                                                             |
| `c.iter().map().filter()` | *函数式*，当只关心结果时通常更清晰。                                                                                   |
| `c_iter.next()`           | *底层*，通过显式调用 `Iterator::next()` {{ std(page="std/iter/trait.Iterator.html#tymethod.next") }}。{{ esoteric() }} |
| `c.get(n)`                | *手动*，绕过官方的迭代机制。                                                                                           |

{{ tablesep() }}

> **个人观点** {{ opinionated() }} &mdash; 函数式风格通常最容易理解，但如果你的 `.iter()` 链变得混乱，不要犹豫使用 `for`。在实现容器时，迭代器支持是理想的，但当赶时间时，有时只实现 `.len()` 和 `.get()` 然后继续生活可能更实用。


</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-trait-iter-1" name="tab-group-trait-iter">
<label for="tab-trait-iter-1"><b>获取</b></label>
<panel><div>



**基础**

假设你有一个类型为 `C` 的集合 `c`，你想要使用它：

* **`c.into_iter()`**<sup>1</sup>  &mdash; 将集合 `c` 转换为一个 **`Iterator`** {{ std(page="std/iter/trait.Iterator.html") }} `i` 并**消耗**<sup>2</sup> `c`。获取迭代器的*标准*方式。
* **`c.iter()`** &mdash; **一些**集合提供的便捷方法，返回一个**借用**的迭代器，不消耗 `c`。
* **`c.iter_mut()`** &mdash; 同上，但返回一个**可变借用**的迭代器，允许集合被更改。


**迭代器**

一旦你有了 `i`：

* **`i.next()`** &mdash; 返回 `Some(x)`，即 `c` 提供的下一个元素，如果完成则返回 `None`。


**For 循环**

* **`for x in c {}`** &mdash; 语法糖，调用 `c.into_iter()` 并循环 `i` 直到 `None`。



<footnotes>

<sup>1</sup> 要求为 `C` 实现 **`IntoIterator`** {{ std(page="std/iter/trait.IntoIterator.html") }}。项的类型取决于 `C` 是什么。

<sup>2</sup> 如果看起来它没有消耗 `c`，那是因为类型是 `Copy`。例如，如果你调用 `(&c).into_iter()`，它将在 `&c` 上调用 `.into_iter()`（这将消耗引用的一个*副本*并将其转换为迭代器），但原始的 `c` 保持不变。

</footnotes>

</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-trait-iter-2" name="tab-group-trait-iter">
<label for="tab-trait-iter-2"><b>创建</b></label>
<panel><div>

**基本要素**

假设你编写了一个 `struct Collection<T> {}`。你还应该实现：


* **`struct IntoIter<T> {}`** &mdash; 创建一个结构体来保存你的迭代状态（例如，一个索引），用于值迭代。
* **`impl Iterator for IntoIter<T> {}`** &mdash; 实现 `Iterator::next()` 以便它可以产生元素。

<mini-zoo class="zoo" style="">
    <entry class="wide">
        <type class="generic dotted"><code>Collection&lt;T&gt;</code></type>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="margin-right: 20px;">
    <entry class="wide">
        <type class="generic dotted"><code>IntoIter&lt;T&gt;</code></type>
        <trait-impl class="">⌾ <code style="">Iterator</code></trait-impl>
        <associated-type class="grayed"><code>Item = T;</code></associated-type>
    </entry>
</mini-zoo>

{{ tablesep() }}

> 此时，你已经有了一个可以作为 **Iterator** {{ std(page="std/iter/trait.Iterator.html") }} 的东西，但还没有办法真正获得它。下一选项卡将介绍通常如何做到这一点。


</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-trait-iter-3" name="tab-group-trait-iter">
<label for="tab-trait-iter-3"><b>For 循环</b></label>
<panel><div>

**原生循环支持**

许多用户会期望你的集合在 `for` 循环中*就能用*。你需要实现：

* **`impl IntoIterator for Collection<T> {}`** &mdash; 现在 `for x in c {}` 可以工作了。
* **`impl IntoIterator for &Collection<T> {}`** &mdash; 现在 `for x in &c {}` 可以工作了。
* **`impl IntoIterator for &mut Collection<T> {}`** &mdash; 现在 `for x in &mut c {}` 可以工作了。

<mini-zoo class="zoo" style="">
    <entry class="wide">
        <type class="generic dotted"><code>Collection&lt;T&gt;</code></type>
        <trait-impl class="">⌾ <code style="">IntoIterator</code></trait-impl>
        <associated-type class="grayed"><code>Item = T;</code></associated-type>
        <associated-type class="grayed"><code>To = IntoIter&lt;T&gt;</code></associated-type>
        <note>迭代 <code>T</code>。</note>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="">
    <entry class="wide">
        <type class="generic dotted grayed"><code>&Collection&lt;T&gt;</code></type>
        <trait-impl class="">⌾ <code style="">IntoIterator</code></trait-impl>
        <associated-type class="grayed"><code>Item = &T;</code></associated-type>
        <associated-type class="grayed"><code>To = Iter&lt;T&gt;</code></associated-type>
        <note>迭代 <code>&T</code>。</note>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="">
    <entry class="wide">
        <type class="generic dotted grayed"><code>&mut Collectn&lt;T&gt;</code></type>
        <trait-impl class="">⌾ <code style="">IntoIterator</code></trait-impl>
        <associated-type class="grayed"><code>Item = &mut T;</code></associated-type>
        <associated-type class="grayed"><code>To = IterMut&lt;T&gt;</code></associated-type>
        <note>迭代 <code>&mut T</code>。</note>
    </entry>
</mini-zoo>

{{ tablesep() }}

> 如你所见，**IntoIterator** {{ std(page="std/iter/trait.IntoIterator.html") }} trait 才是真正将你的集合与你在前一个选项卡中创建的 **IntoIter** 结构体连接起来的东西。**IntoIter** 的两个兄弟（**Iter** 和 **IterMut**）将在下一个选项卡中讨论。


</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-trait-iter-2b" name="tab-group-trait-iter">
<label for="tab-trait-iter-2b"><b>借用</b></label>
<panel><div>



**共享与可变迭代器**

此外，如果你希望你的集合在被借用时也很有用，你应该实现：

* **`struct Iter<T> {}`** &mdash; 创建一个结构体，持有 `&Collection<T>` 状态，用于共享迭代。
* **`struct IterMut<T> {}`** &mdash; 类似，但持有 `&mut Collection<T>` 状态，用于可变迭代。
* **`impl Iterator for Iter<T> {}`** &mdash; 实现共享迭代。
* **`impl Iterator for IterMut<T> {}`** &mdash; 实现可变迭代。

此外，你可能想添加一些便捷方法：

- `Collection::iter(&self) -> Iter`,
- `Collection::iter_mut(&mut self) -> IterMut`.



<mini-zoo class="zoo" style="margin-right: 20px;">
    <entry class="wide">
        <type class="generic dotted"><code>Iter&lt;T&gt;</code></type>
        <trait-impl class="">⌾ <code style="">Iterator</code></trait-impl>
        <associated-type class="grayed"><code>Item = &T;</code></associated-type>
    </entry>
</mini-zoo>


<mini-zoo class="zoo" style="margin-right: 20px;">
    <entry class="wide">
        <type class="generic dotted"><code>IterMut&lt;T&gt;</code></type>
        <trait-impl class="">⌾ <code style="">Iterator</code></trait-impl>
        <associated-type class="grayed"><code>Item = &mut T;</code></associated-type>
    </entry>
</mini-zoo>

{{ tablesep() }}

> 借用迭代器支持的代码基本上只是前几个步骤的重复，只是类型略有不同，例如 `&T` 对比 `T`。


</div></panel></tab>




<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-trait-iter-4" name="tab-group-trait-iter">
<label for="tab-trait-iter-4"><b>互操作性</b></label>
<panel><div>


**迭代器互操作性**

要允许**第三方迭代器**“收集到”你的集合中，请实现：

* **`impl FromIterator for Collection<T> {}`** &mdash; 现在 `some_iter.collect::<Collection<_>>()` 可以工作了。
* **`impl Extend for Collection<T> {}`** &mdash; 现在 `c.extend(other)` 可以工作了。

此外，还应考虑将 **`std::iter`** {{ std(page="std/iter/index.html#") }} 中的额外 trait 添加到你之前的结构体中：

<mini-zoo class="zoo" style="margin-right: 20px;">
    <entry class="wide">
        <type class="generic dotted"><code>Collection&lt;T&gt;</code></type>
        <trait-impl class="">⌾ <code style="">FromIterator</code></trait-impl>
        <trait-impl class="">⌾ <code style="">Extend</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <entry class="wide">
        <type class="generic dotted"><code>IntoIter&lt;T&gt;</code></type>
        <trait-impl class="">⌾ <code style="">DoubleEndedIt… </code></trait-impl>
        <trait-impl class="">⌾ <code style="">ExactSizeIt… </code></trait-impl>
        <trait-impl class="">⌾ <code style="">FusedIterator </code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <entry class="wide">
        <type class="generic dotted"><code>Iter&lt;T&gt;</code></type>
        <trait-impl class="">⌾ <code style="">DoubleEndedIt… </code></trait-impl>
        <trait-impl class="">⌾ <code style="">ExactSizeIt… </code></trait-impl>
        <trait-impl class="">⌾ <code style="">FusedIterator </code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <entry class="wide">
        <type class="generic dotted"><code>IterMut&lt;T&gt;</code></type>
        <trait-impl class="">⌾ <code style="">DoubleEndedIt… </code></trait-impl>
        <trait-impl class="">⌾ <code style="">ExactSizeIt… </code></trait-impl>
        <trait-impl class="">⌾ <code style="">FusedIterator </code></trait-impl>
    </entry>
</mini-zoo>



{{ tablesep() }}

> 编写集合可能是一项工作。好消息是，如果你遵循了所有这些步骤，你的集合将会感觉像是*一等公民*。


</div></panel></tab>

</tabs>



<!-- 在小屏幕上创建一个水平滚动区域以保持布局 -->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">
<div class="color-header number">


## 数字转换 {#number-conversions}


目前为止最<b style="">正确</b>的数字转换。

| ↓ 有 / 想要 →        | `u8` &hellip; `i128`            | `f32` / `f64`           | String          |
| -------------------- | ------------------------------- | ----------------------- | --------------- |
| `u8` &hellip; `i128` | `u8::try_from(x)?` <sup>1</sup> | `x as f32` <sup>3</sup> | `x.to_string()` |
| `f32` / `f64`        | `x as u8` <sup>2</sup>          | `x as f32`              | `x.to_string()` |
| `String`             | `x.parse::<u8>()?`              | `x.parse::<f32>()?`     | `x`             |


<footnotes>

<sup>1</sup> 如果类型是真子集，`from()` 可以直接工作，例如 `u32::from(my_u8)`。<br/>
<sup>2</sup> 截断（`11.9_f32 as u8` 得到 `11`）和饱和（`1024_f32 as u8` 得到 `255`）；参见下文。<br/>
<sup>3</sup> 可能会错误地表示数字（`u64::MAX as f32`）或产生 `Inf`（`u128::MAX as f32`）。

</footnotes>

{{ tablesep() }}

> 另请参见**转换**和**算术陷阱** {{ above(target="#numeric-types") }}，了解更多处理数字时可能出错的事情。


<!-- end overflow -->
</div>
</div>
</div>



## 字符串转换 {#string-conversions}


如果你**想要**一个 &hellip; 类型的字符串

<!-- 在小屏幕上创建一个水平滚动区域以保持布局 -->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">


<tabs>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-str-1" name="tab-group-str" checked>
<label for="tab-str-1"><code>String</code></label>
<panel><div class="stringconversion">

| 如果你**有**一个 `x`，类型是 &hellip; | 使用这个 &hellip;                        |
| ------------------------------------- | ---------------------------------------- |
| `String`                              | `x`                                      |
| `CString`                             | `x.into_string()?`                       |
| `OsString`                            | `x.to_str()?.to_string()`                |
| `PathBuf`                             | `x.to_str()?.to_string()`                |
| `Vec<u8>` <sup>1</sup>                | `String::from_utf8(x)?`                  |
| `&str`                                | `x.to_string()` <sup>`i`</sup>           |
| `&CStr`                               | `x.to_str()?.to_string()`                |
| `&OsStr`                              | `x.to_str()?.to_string()`                |
| `&Path`                               | `x.to_str()?.to_string()`                |
| `&[u8]` <sup>1</sup>                  | `String::from_utf8_lossy(x).to_string()` |

</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-str-2" name="tab-group-str" >
<label for="tab-str-2"><code>CString</code></label>
<panel><div class="stringconversion">

| 如果你**有**一个 `x`，类型是 &hellip; | 使用这个 &hellip;                                |
| ------------------------------------- | ------------------------------------------------ |
| `String`                              | `CString::new(x)?`                               |
| `CString`                             | `x`                                              |
| `OsString`                            | `CString::new(x.to_str()?)?`                     |
| `PathBuf`                             | `CString::new(x.to_str()?)?`                     |
| `Vec<u8>` <sup>1</sup>                | `CString::new(x)?`                               |
| `&str`                                | `CString::new(x)?`                               |
| `&CStr`                               | `x.to_owned()` <sup>`i`</sup>                    |
| `&OsStr`                              | `CString::new(x.to_os_string().into_string()?)?` |
| `&Path`                               | `CString::new(x.to_str()?)?`                     |
| `&[u8]` <sup>1</sup>                  | `CString::new(Vec::from(x))?`                    |
| `*mut c_char` <sup>2</sup>            | `unsafe { CString::from_raw(x) }`                |

</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-str-3" name="tab-group-str" >
<label for="tab-str-3"><code>OsString</code></label>
<panel><div class="stringconversion">

| 如果你**有**一个 `x`，类型是 &hellip; | 使用这个 &hellip;                                               |
| ------------------------------------- | --------------------------------------------------------------- |
| `String`                              | `OsString::from(x)` <sup>`i`</sup>                              |
| `CString`                             | `OsString::from(x.to_str()?)`                                   |
| `OsString`                            | `x`                                                             |
| `PathBuf`                             | `x.into_os_string()`                                            |
| `Vec<u8>` <sup>1</sup>                | `unsafe { OsString::from_encoded_bytes_unchecked(x) }`          |
| `&str`                                | `OsString::from(x)` <sup>`i`</sup>                              |
| `&CStr`                               | `OsString::from(x.to_str()?)`                                   |
| `&OsStr`                              | `OsString::from(x)` <sup>`i`</sup>                              |
| `&Path`                               | `x.as_os_str().to_owned()`                                      |
| `&[u8]` <sup>1</sup>                  | `unsafe { OsString::from_encoded_bytes_unchecked(x.to_vec()) }` |

</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-str-35" name="tab-group-str" >
<label for="tab-str-35"><code>PathBuf</code></label>
<panel><div class="stringconversion">

| 如果你**有**一个 `x`，类型是 &hellip; | 使用这个 &hellip;                                                              |
| ------------------------------------- | ------------------------------------------------------------------------------ |
| `String`                              | `PathBuf::from(x)` <sup>`i`</sup>                                              |
| `CString`                             | `PathBuf::from(x.to_str()?)`                                                   |
| `OsString`                            | `PathBuf::from(x)` <sup>`i`</sup>                                              |
| `PathBuf`                             | `x`                                                                            |
| `Vec<u8>` <sup>1</sup>                | `unsafe { PathBuf::from(OsString::from_encoded_bytes_unchecked(x)) }`          |
| `&str`                                | `PathBuf::from(x)` <sup>`i`</sup>                                              |
| `&CStr`                               | `PathBuf::from(x.to_str()?)`                                                   |
| `&OsStr`                              | `PathBuf::from(x)` <sup>`i`</sup>                                              |
| `&Path`                               | `PathBuf::from(x)` <sup>`i`</sup>                                              |
| `&[u8]` <sup>1</sup>                  | `unsafe { PathBuf::from(OsString::from_encoded_bytes_unchecked(x.to_vec())) }` |

</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-str-4" name="tab-group-str" >
<label for="tab-str-4"><code>Vec&lt;u8&gt;</code></label>
<panel><div class="stringconversion">

| 如果你**有**一个 `x`，类型是 &hellip; | 使用这个 &hellip;                             |
| ------------------------------------- | --------------------------------------------- |
| `String`                              | `x.into_bytes()`                              |
| `CString`                             | `x.into_bytes()`                              |
| `OsString`                            | `x.into_encoded_bytes()`                      |
| `PathBuf`                             | `x.into_os_string().into_encoded_bytes()`     |
| `Vec<u8>` <sup>1</sup>                | `x`                                           |
| `&str`                                | `Vec::from(x.as_bytes())`                     |
| `&CStr`                               | `Vec::from(x.to_bytes_with_nul())`            |
| `&OsStr`                              | `Vec::from(x.as_encoded_bytes())`             |
| `&Path`                               | `Vec::from(x.as_os_str().as_encoded_bytes())` |
| `&[u8]` <sup>1</sup>                  | `x.to_vec()`                                  |

</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-str-5" name="tab-group-str" >
<label for="tab-str-5"><code>&str</code></label>
<panel><div class="stringconversion">

| 如果你**有**一个 `x`，类型是 &hellip; | 使用这个 &hellip;          |
| ------------------------------------- | -------------------------- |
| `String`                              | `x.as_str()`               |
| `CString`                             | `x.to_str()?`              |
| `OsString`                            | `x.to_str()?`              |
| `PathBuf`                             | `x.to_str()?`              |
| `Vec<u8>` <sup>1</sup>                | `std::str::from_utf8(&x)?` |
| `&str`                                | `x`                        |
| `&CStr`                               | `x.to_str()?`              |
| `&OsStr`                              | `x.to_str()?`              |
| `&Path`                               | `x.to_str()?`              |
| `&[u8]` <sup>1</sup>                  | `std::str::from_utf8(x)?`  |

</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-str-6" name="tab-group-str" >
<label for="tab-str-6"><code>&CStr</code></label>
<panel><div class="stringconversion">

| 如果你**有**一个 `x`，类型是 &hellip; | 使用这个 &hellip;                |
| ------------------------------------- | -------------------------------- |
| `String`                              | `CString::new(x)?.as_c_str()`    |
| `CString`                             | `x.as_c_str()`                   |
| `OsString`                            | `x.to_str()?`                    |
| `PathBuf`                             | {{ todo() }}<sup>,3</sup>        |
| `Vec<u8>` <sup>1</sup><sup>,4</sup>   | `CStr::from_bytes_with_nul(&x)?` |
| `&str`                                | {{ todo() }}<sup>,3</sup>        |
| `&CStr`                               | `x`                              |
| `&OsStr`                              | {{ todo() }}                     |
| `&Path`                               | {{ todo() }}                     |
| `&[u8]` <sup>1</sup><sup>,4</sup>     | `CStr::from_bytes_with_nul(x)?`  |
| `*const c_char` <sup>1</sup>          | `unsafe { CStr::from_ptr(x) }`   |

</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-str-8" name="tab-group-str" >
<label for="tab-str-8"><code>&OsStr</code></label>
<panel><div class="stringconversion">

| 如果你**有**一个 `x`，类型是 &hellip; | 使用这个 &hellip;                                    |
| ------------------------------------- | ---------------------------------------------------- |
| `String`                              | `OsStr::new(&x)`                                     |
| `CString`                             | {{ todo() }}                                         |
| `OsString`                            | `x.as_os_str()`                                      |
| `PathBuf`                             | `x.as_os_str()`                                      |
| `Vec<u8>` <sup>1</sup>                | `unsafe { OsStr::from_encoded_bytes_unchecked(&x) }` |
| `&str`                                | `OsStr::new(x)`                                      |
| `&CStr`                               | {{ todo() }}                                         |
| `&OsStr`                              | `x`                                                  |
| `&Path`                               | `x.as_os_str()`                                      |
| `&[u8]` <sup>1</sup>                  | `unsafe { OsStr::from_encoded_bytes_unchecked(x) }`  |


</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-str-85" name="tab-group-str" >
<label for="tab-str-85"><code>&Path</code></label>
<panel><div class="stringconversion">

| 如果你**有**一个 `x`，类型是 &hellip; | 使用这个 &hellip;                                               |
| ------------------------------------- | --------------------------------------------------------------- |
| `String`                              | `Path::new(x)` <sup>`r`</sup>                                   |
| `CString`                             | `Path::new(x.to_str()?)`                                        |
| `OsString`                            | `Path::new(x.to_str()?)` <sup>`r`</sup>                         |
| `PathBuf`                             | `Path::new(x.to_str()?)` <sup>`r`</sup>                         |
| `Vec<u8>` <sup>1</sup>                | `unsafe { Path::new(OsStr::from_encoded_bytes_unchecked(&x)) }` |
| `&str`                                | `Path::new(x)` <sup>`r`</sup>                                   |
| `&CStr`                               | `Path::new(x.to_str()?)`                                        |
| `&OsStr`                              | `Path::new(x)` <sup>`r`</sup>                                   |
| `&Path`                               | `x`                                                             |
| `&[u8]` <sup>1</sup>                  | `unsafe { Path::new(OsStr::from_encoded_bytes_unchecked(x)) }`  |

</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-str-7" name="tab-group-str" >
<label for="tab-str-7"><code>&[u8]</code></label>
<panel><div class="stringconversion">

| 如果你**有**一个 `x`，类型是 &hellip; | 使用这个 &hellip;                  |
| ------------------------------------- | ---------------------------------- |
| `String`                              | `x.as_bytes()`                     |
| `CString`                             | `x.as_bytes()`                     |
| `OsString`                            | `x.as_encoded_bytes()`             |
| `PathBuf`                             | `x.as_os_str().as_encoded_bytes()` |
| `Vec<u8>` <sup>1</sup>                | `&x`                               |
| `&str`                                | `x.as_bytes()`                     |
| `&CStr`                               | `x.to_bytes_with_nul()`            |
| `&OsStr`                              | `x.as_encoded_bytes()`             |
| `&Path`                               | `x.as_os_str().as_encoded_bytes()` |
| `&[u8]` <sup>1</sup>                  | `x`                                |

</div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-str-9" name="tab-group-str" >
<label for="tab-str-9"><b>其他</b></label>
<panel><div class="stringconversion">

| 你**想要**             | 并且**有** `x`   | 使用这个 &hellip; |
| ---------------------- | ---------------- | ----------------- |
| <b>`*const c_char`</b> | <b>`CString`</b> | `x.as_ptr()`      |


</div></panel></tab>

<!-- End tabs -->
</tabs>

<!-- End overflow protection -->
</div></div>


<footnotes>

<sup>i</sup> 如果类型可以推断，可以使用简写形式 `x.into()`。<br>
<sup>r</sup> 如果类型可以推断，可以使用简写形式 `x.as_ref()`。<br>
<sup>1</sup> 你必须确保 `x` 带有字符串类型的有效表示（例如，对于 `String` 的 UTF-8 数据）。<br>
<sup>2</sup> `c_char` **必须**来自先前的 `CString`。如果它来自 FFI，请改用 `&CStr`。<br>
<sup>3</sup> 没有已知的简写，因为 `x` 将缺少结尾的 `0x0`。最好的方法可能是通过 `CString`。<br>
<sup>4</sup> 必须确保 `x` 实际上以 `0x0` 结尾。<br>

</footnotes>


## 字符串输出 {#string-output}

如何将类型转换为 `String` 或输出它们。

<tabs>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-strop-1" name="tab-group-strop" checked>
<label for="tab-strop-1"><b>API</b></label>
<panel><div class="color-header undefined-color-3">

Rust 有多种 API 可将类型转换为字符串化输出，统称为*格式化宏*：

| 宏                   | 输出     | 注意                             |
| -------------------- | -------- | -------------------------------- |
| `format!(fmt)`       | `String` | 基本的“转为 `String`”转换器。    |
| `print!(fmt)`        | 控制台   | 写入标准输出。                   |
| `println!(fmt)`      | 控制台   | 写入标准输出。                   |
| `eprint!(fmt)`       | 控制台   | 写入标准错误。                   |
| `eprintln!(fmt)`     | 控制台   | 写入标准错误。                   |
| `write!(dst, fmt)`   | 缓冲区   | 别忘了也要 `use std::io::Write;` |
| `writeln!(dst, fmt)` | 缓冲区   | 别忘了也要 `use std::io::Write;` |

{{ tablesep() }}

| 方法                                                             | 注意                                       |
| ---------------------------------------------------------------- | ------------------------------------------ |
| `x.to_string()` {{ std(page="std/string/trait.ToString.html") }} | 产生 `String`，为任何 `Display` 类型实现。 |

{{ tablesep() }}

这里的 `fmt` 是像 `"hello {}"` 这样的字符串字面量，它指定了输出（比较“格式化”选项卡）和附加参数。


</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-strop-2" name="tab-group-strop">
<label for="tab-strop-2"><b>可打印类型</b></label>
<panel><div class="color-header undefined-color-3">

在 `format!` 和类似宏中，类型通过 trait `Display` `"{}"` {{ std(page="std/fmt/trait.Display.html") }} 或 `Debug` `"{:?}"` {{ std(page="std/fmt/trait.Debug.html") }} 进行转换，不完全列表：

| 类型                 | 实现             |     |
| -------------------- | ---------------- | --- |
| `String`             | `Debug, Display` |     |
| `CString`            | `Debug`          |     |
| `OsString`           | `Debug`          |     |
| `PathBuf`            | `Debug`          |     |
| `Vec<u8>`            | `Debug`          |     |
| `&str`               | `Debug, Display` |     |
| `&CStr`              | `Debug`          |     |
| `&OsStr`             | `Debug`          |     |
| `&Path`              | `Debug`          |     |
| `&[u8]`              | `Debug`          |     |
| `bool`               | `Debug, Display` |     |
| `char`               | `Debug, Display` |     |
| `u8` &hellip; `i128` | `Debug, Display` |     |
| `f32`, `f64`         | `Debug, Display` |     |
| `!`                  | `Debug, Display` |     |
| `()`                 | `Debug`          |     |

{{ tablesep() }}

简而言之，几乎所有东西都是 `Debug`；更*特殊的*类型可能需要特殊处理或转换{{ above(target="#string-conversions" ) }}为 `Display`。

</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-strop-3" name="tab-group-strop">
<label for="tab-strop-3"><b>格式化</b></label>
<panel><div>

格式化宏中的每个参数指示符要么是空的 `{}`, `{argument}`，要么遵循基本的 [**语法**](https://doc.rust-lang.org/std/fmt/index.html#syntax)：


```
{ [argument] ':' [[fill] align] [sign] ['#'] [width [$]] ['.' precision [$]] [type] }
```

<div class="color-header undefined-color-3">

| 元素        | 含义                                                                                                                                                                                                  |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `argument`  | 数字（`0`, `1`, …）、变量{{ edition(ed="'21") }}或名称，{{ edition(ed="'18") }}例如`print!("{x}")`。                                                                                                  |
| `fill`      | 如果指定了 `width`，则用于填充空白的字符（例如 `0`）。                                                                                                                                                |
| `align`     | 如果指定了宽度，则为左（`<`）、中（`^`）或右（`>`）对齐。                                                                                                                                             |
| `sign`      | 可以是 `+`，表示总是打印符号。                                                                                                                                                                        |
| `#`         | [替代格式化](https://doc.rust-lang.org/std/fmt/index.html#sign0)，例如美化 `Debug`{{ std(page="std/fmt/trait.Debug.html") }} 格式化器 `?` 或为十六进制加前缀 `0x`。                                   |
| `width`     | 最小宽度（&geq; 0），用 `fill`（默认为空格）填充。如果以 `0` 开头，则用零填充。                                                                                                                       |
| `precision` | 数值的小数位数（&geq; 0），或非数值的最大宽度。                                                                                                                                                       |
| `$`         | 将 `width` 或 `precision` 解释为参数标识符，以允许动态格式化。                                                                                                                                        |
| **`type`**  | `Debug`{{ std(page="std/fmt/trait.Debug.html") }} (`?`) 格式化、十六进制 (`x`)、二进制 (`b`)、八进制 (`o`)、指针 (`p`)、指数 (`e`)……[查看更多](https://doc.rust-lang.org/std/fmt/index.html#traits)。 |

</div>


{{ tablesep() }}


<div class="color-header undefined-color-3">

| 格式化示例  | 解释                                                                                 |
| ----------- | ------------------------------------------------------------------------------------ |
| `{}`        | 使用 `Display`{{ std(page="std/fmt/trait.Display.html") }} 打印下一个参数。          |
| `{x}`       | 同上，但使用作用域中的变量 `x`。{{ edition(ed="'21") }}                              |
| `{:?}`      | 使用 `Debug`{{ std(page="std/fmt/trait.Debug.html") }} 打印下一个参数。              |
| `{2:#?}`    | 使用 `Debug`{{ std(page="std/fmt/trait.Debug.html") }} 格式化漂亮地打印第 3 个参数。 |
| `{val:^2$}` | 居中名为 `val` 的参数，宽度由第 3 个参数指定。                                       |
| `{:<10.3}`  | 左对齐，宽度为 10，精度为 3。                                                        |
| `{val:#x}`  | 将 `val` 参数格式化为十六进制，并带前导 `0x`（`x` 的替代格式）。                     |

</div>

{{ tablesep() }}


<div class="color-header undefined-color-3">

| 完整示例                  | 解释                                                                                                                                      |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| `println!("{}", x)`       | 使用 `Display`{{ std(page="std/fmt/trait.Display.html") }} 将 `x` 打印到标准输出并追加换行符。{{ edition(ed="'15") }} {{ deprecated() }}  |
| `println!("{x}")`         | 同上，但使用作用域中的变量 `x`。{{ edition(ed="'21") }}                                                                                   |
| `format!("{a:.3} {b:?}")` | 将 `a` 转换为 3 位数，添加空格，使用 `Debug`{{ std(page="std/fmt/trait.Debug.html") }} 格式化 `b`，返回 `String`。{{ edition(ed="'21") }} |

</div>


</div></panel></tab>


</tabs>

{{ tablesep() }}




---

# 工具链


## 项目结构 {#project-anatomy}

基本的项目布局，以及 `cargo` {{ below(target="#cargo") }} 使用的常见文件和文件夹。

<div class="color-header red">

| 条目                                                      | 代码                                                                                                                                                                                                                                                                                                                                       |
| --------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 📁 `.cargo/`                                               | **项目本地 cargo 配置**，可能包含 **`config.toml`**。{{ link( url="https://doc.rust-lang.org/cargo/reference/config.html") }} {{ esoteric() }}                                                                                                                                                                                             |
| 📁 `benches/`                                              | 你的 crate 的基准测试，通过 **`cargo bench`** 运行，默认需要 nightly。<sup>*</sup> {{ experimental() }}                                                                                                                                                                                                                                    |
| 📁 `examples/`                                             | 如何使用你的 crate 的示例，它们像外部用户一样看待你的 crate。                                                                                                                                                                                                                                                                              |
| {{ tab() }} {{ tab() }} `my_example.rs`                   | 单个示例通过 **`cargo run --example my_example`** 运行。                                                                                                                                                                                                                                                                                   |
| 📁 `src/`                                                  | 你的项目的实际源代码。                                                                                                                                                                                                                                                                                                                     |
| {{ tab() }} {{ tab() }} `main.rs`                         | 应用程序的默认入口点，这是 **`cargo run`** 使用的。                                                                                                                                                                                                                                                                                        |
| {{ tab() }} {{ tab() }} `lib.rs`                          | 库的默认入口点。`my_crate::f()` 的查找从这里开始。                                                                                                                                                                                                                                                                                         |
| 📁 `src/bin/`                                              | 放置额外二进制文件的地方，即使在库项目中也可以。                                                                                                                                                                                                                                                                                           |
| {{ tab() }} {{ tab() }} `extra.rs`                        | 额外的二进制文件，用 `cargo run --bin extra` 运行。                                                                                                                                                                                                                                                                                        |
| 📁 `tests/`                                                | 集成测试放在这里，通过 **`cargo test`** 调用。单元测试通常留在 `src/` 文件中。                                                                                                                                                                                                                                                             |
| `.rustfmt.toml`                                           | 如果你想[**自定义**](https://rust-lang.github.io/rustfmt/) **`cargo fmt`** 的工作方式。                                                                                                                                                                                                                                                    |
| `.clippy.toml`                                            | 某些 [**clippy lints**](https://rust-lang.github.io/rust-clippy/master/index.html) 的特殊配置，通过 **`cargo clippy`** 使用 {{ esoteric() }}                                                                                                                                                                                               |
| `build.rs`                                                | **预构建脚本**，{{ link(url="https://doc.rust-lang.org/cargo/reference/build-scripts.html") }} 在编译 C / FFI 等时很有用。                                                                                                                                                                                                                 |
| <code class="ignore-auto language-bash">Cargo.toml</code> | 主要的**项目清单**，{{ link(url="https://doc.rust-lang.org/cargo/reference/manifest.html") }} 定义依赖项、构件等。                                                                                                                                                                                                                         |
| <code class="ignore-auto language-bash">Cargo.lock</code> | 用于可复现的构建。对于应用程序，添加到 git；对于库，考虑不添加。{{ opinionated() }} {{ link(url="https://blog.rust-lang.org/2023/08/29/committing-lockfiles.html" )}} {{ link(url="https://web.archive.org/web/20240108203227/https://old.reddit.com/r/rust/comments/164qfjm/change_in_guidance_on_committing_lockfiles_rust/jya8ouf/" )}} |
| `rust-toolchain.toml`                                     | 定义此项目的**工具链覆盖**{{ link(url="https://rust-lang.github.io/rustup/overrides.html" )}}（通道、组件、目标）。                                                                                                                                                                                                                        |
</div>

<footnotes>

<sup>*</sup> 在 stable 上考虑使用 [Criterion](https://github.com/bheisler/criterion.rs)。

</footnotes>


{{ tablesep() }}


各种入口点的**最小示例**可能如下所示：

<tabs>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-anatomy-1" name="tab-group-anatomy" checked>
<label for="tab-anatomy-1"><b>应用程序</b></label>
<panel><div>


<!-- 在小屏幕上创建一个水平滚动区域以保持布局 -->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

```
// src/main.rs (默认应用程序入口点)

fn main() {
    println!("Hello, world!");
}
```

</div></div></div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-anatomy-2" name="tab-group-anatomy" >
<label for="tab-anatomy-2"><b>库</b></label>
<panel><div>

<!-- 在小屏幕上创建一个水平滚动区域以保持布局 -->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

```
// src/lib.rs (默认库入口点)

pub fn f() {}      // 是根中的一个公共项，所以可以从外部访问。

mod m {
    pub fn g() {}  // 从根没有公共路径（`m` 不是公共的），所以 `g`
}                  // 不能从 crate 外部访问。
```
</div></div></div></panel></tab>





<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-anatomy-3" name="tab-group-anatomy" >
<label for="tab-anatomy-3"><b>单元测试</b></label>
<panel><div>

<!-- 在小屏幕上创建一个水平滚动区域以保持布局 -->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

```
// src/my_module.rs (你项目的任何文件)

fn f() -> u32 { 0 }

#[cfg(test)]
mod test {
    use super::f;           // 需要从父模块导入项。可以访问
                            // 非公共成员。
    #[test]
    fn ff() {
        assert_eq!(f(), 0);
    }
}
```
</div></div></div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-anatomy-4" name="tab-group-anatomy" >
<label for="tab-anatomy-4"><b>集成测试</b></label>
<panel><div>

<!-- 在小屏幕上创建一个水平滚动区域以保持布局 -->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

```
// tests/sample.rs (示例集成测试)

#[test]
fn my_sample() {
    assert_eq!(my_crate::f(), 123); // 集成测试（和基准测试）像
}                                   // 第三方一样“依赖”于 crate。因此，它们只能看到公共项。
```
</div></div></div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-anatomy-5" name="tab-group-anatomy" >
<label for="tab-anatomy-5"><b>基准测试</b>{{ experimental() }}</label>
<panel><div>


<!-- 在小屏幕上创建一个水平滚动区域以保持布局 -->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

```
// benches/sample.rs (示例基准测试)

#![feature(test)]   // #[bench] 仍然是实验性的

extern crate test;  // 即使在 '18 版本中，由于某些原因，这也是必需的。
                    // 通常在 '18 代码中你不需要这个。

use test::{black_box, Bencher};

#[bench]
fn my_algo(b: &mut Bencher) {
    b.iter(|| black_box(my_crate::f())); // `black_box` 防止 `f` 被优化掉。
}
```
</div></div></div></panel></tab>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-anatomy-6" name="tab-group-anatomy" >
<label for="tab-anatomy-6"><b>构建脚本</b></label>
<panel><div>

<!-- 在小屏幕上创建一个水平滚动区域以保持布局 -->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

```
// build.rs (示例预构建脚本)

fn main() {
    // 你需要依赖环境变量来获取目标；`#[cfg(…)]` 是为主机准备的。
    let target_os = env::var("CARGO_CFG_TARGET_OS");
}
```

<sup>*</sup>[此处是设置的环境变量列表](https://doc.rust-lang.org/cargo/reference/environment-variables.html#environment-variables-cargo-sets-for-build-scripts)。

</div></div></div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-anatomy-25" name="tab-group-anatomy" >
<label for="tab-anatomy-25"><b>过程宏</b>{{ esoteric() }}</label>
<panel><div>


<!-- 在小屏幕上创建一个水平滚动区域以保持布局 -->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

```
// src/lib.rs (过程宏的默认入口点)

extern crate proc_macro;  // 显然需要这样导入。

use proc_macro::TokenStream;

#[proc_macro_attribute]   // Crate 现在可以使用 `#[my_attribute]`
pub fn my_attribute(_attr: TokenStream, item: TokenStream) -> TokenStream {
    item
}
```


```
// Cargo.toml

[package]
name = "my_crate"
version = "0.1.0"

[lib]
proc-macro = true
```


</div></div></div></panel></tab>


</tabs>



{{ tablesep() }}


模块树和导入：

<tabs>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-module-import-1" name="tab-group-module-import" checked>
<label for="tab-module-import-1"><b>模块树</b></label>
<panel><div>


<!-- 在小屏幕上创建一个水平滚动区域以保持布局 -->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

**模块** {{ book(page="ch07-02-defining-modules-to-control-scope-and-privacy.html") }} {{ ex(page="mod.html#modules") }} {{ ref(page="items/modules.html#modules") }} 和**源文件**的工作方式如下：

- **模块树**需要显式定义，**不是**从**文件系统树**隐式构建的。{{ link(url="http://www.sheshbabu.com/posts/rust-module-system/") }}
- **模块树根**等于库、应用程序等的入口点（例如 `lib.rs`）。

实际的**模块定义**工作方式如下：
- **`mod m {}`** 在文件中定义模块，而 **`mod m;`** 将读取 `m.rs` 或 `m/mod.rs`。
- `.rs` 的路径基于**嵌套**，例如 `mod a { mod b { mod c; }}}` 要么是 `a/b/c.rs` 要么是 `a/b/c/mod.rs`。
- 没有通过某个 `mod m;` 从模块树根路径化的文件不会被编译器处理！{{ bad() }}

<!-- - **Visibility** of items (e.g., functions, fields) between modules governed by: "Is there visible path to item?"
    - Visibility like `pub fn f() {}` does not mean "`f` is public", but "`f` at most public if all parents public`. -->


</div></div></div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-module-import-2" name="tab-group-module-import">
<label for="tab-module-import-2"><b>命名空间</b>{{ esoteric() }}</label>
<panel><div>


Rust 有三种**命名空间**：

<table>
    <thead>
        <tr>
            <th>命名空间 <i>类型</i></th>
            <th>命名空间 <i>函数</i></th>
            <th>命名空间 <i>宏</i></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>mod X {}</code></td>
            <td><code>fn X() {}</code></td>
            <td><code>macro_rules! X { … }</code></td>
        </tr>
        <tr>
            <td><code>X</code> (crate)</td>
            <td><code>const X: u8 = 1;</code></td>
            <td><code></code></td>
        </tr>
        <tr>
            <td><code>trait X {}</code></td>
            <td><code>static X: u8 = 1;</code></td>
            <td><code></code></td>
        </tr>
        <tr>
            <td><code>enum X {}</code></td>
            <td><code></code></td>
            <td><code></code></td>
        </tr>
        <tr>
            <td><code>union X {}</code></td>
            <td><code></code></td>
            <td><code></code></td>
        </tr>
        <tr>
            <td><code>struct X {}</code></td>
            <td><code></code></td>
            <td><code></code></td>
        </tr>
        <tr>
            <td colspan="2" style="text-align: center; padding-right: 50px;"> <span style="opacity: 50%">←</span> <code>struct X;</code><sup>1</sup> <span style="opacity: 50%">→</span> </td>
            <td></td>
        </tr>
        <tr>
            <td colspan="2" style="text-align: center; padding-right: 50px;"> <span style="opacity: 50%">←</span> <code>struct X();</code><sup>2</sup> <span style="opacity: 50%">→</span> </td>
            <td></td>
        </tr>
    </tbody>
</table>

<footnotes>

<sup>1</sup> 在<i>类型</i>和<i>函数</i>中都算，定义了类型 `X` *和*常量 `X`。<br>
<sup>2</sup> 在<i>类型</i>和<i>函数</i>中都算，定义了类型 `X` *和*函数 `X`。

</footnotes>

- 在任何给定的作用域中，例如在一个模块内，每个命名空间只能存在一个项，例如，
    - `enum X {}` 和 `fn X() {}` 可以共存
    - `struct X;` 和 `const X` 不能共存
- 使用 `use my_mod::X;`，所有名为 `X` 的项都将被导入。

> 由于命名约定（例如，`fn` 和 `mod` 按惯例是小写的）和*常识*（大多数开发者不会把所有东西都命名为 `X`），在大多数情况下你不需要担心这些*种类*。然而，在设计宏时，它们可能是一个因素。


</div></panel></tab>


</tabs>


{{ tablesep() }}



## Cargo {#cargo}

一些值得了解的命令和工具。


<div class="color-header tooling">

| 命令                                                                             | 描述                                                                                            |
| -------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| `cargo init`                                                                     | 为最新版本创建一个新项目。                                                                      |
| <code>cargo <span class="cargo-prefix">b</span>uild</code>                       | 在调试模式下构建项目（<code>--<span class="cargo-prefix">r</span>elease</code> 用于所有优化）。 |
| <code>cargo <span class="cargo-prefix">c</span>heck</code>                       | 检查项目是否会编译（速度快得多）。                                                              |
| <code>cargo <span class="cargo-prefix">t</span>est</code>                        | 运行项目的测试。                                                                                |
| <code>cargo <span class="cargo-prefix">d</span>oc --no-deps --open</code>        | 为你的代码在本地生成文档。                                                                      |
| <code>cargo <span class="cargo-prefix">r</span>un</code>                         | 运行你的项目，如果产生了二进制文件（main.rs）。                                                 |
| {{ tab() }} `cargo run --bin b`                                                  | 运行二进制文件 `b`。统一与其他依赖项的特性（可能会令人困惑）。                                  |
| {{ tab() }} <code>cargo run --<span class="cargo-prefix">p</span>ackage w</code> | 运行子工作区 `w` 的 main。更合理地处理特性。                                                    |
| <code>cargo … --timings</code>                                                   | 显示哪些 crate 导致你的构建耗时过长。{{ hot() }}                                                |
| `cargo tree`                                                                     | 显示依赖图，项目中使用的所有 crate，递归地。                                                    |
| {{ tab() }} `cargo tree -i foo`                                                  | 反向依赖查找，解释为什么使用了 `foo`。                                                          |
| `cargo info foo`                                                                 | 显示 `foo` 的 crate 元数据（默认为此项目使用的版本）。                                          |
| <code>cargo +{nightly, stable} …</code>                                          | 对命令使用给定的工具链，例如，用于“仅 nightly”的工具。                                          |
| <code>cargo +1.85.0 …</code>                                                     | 也直接接受特定版本。                                                                            |
| `cargo +nightly …`                                                               | 一些仅 nightly 的命令（用下面的命令替换 `…`）                                                   |
| {{ tab() }} `rustc -- -Zunpretty=expanded`                                       | 显示展开的宏。{{ experimental() }}                                                              |
| `rustup doc`                                                                     | 打开离线 Rust 文档（包括书籍），在飞机上很好用！                                                |

</div>

<footnotes>

这里 <code>cargo <span class="cargo-prefix">b</span>uild</code> 意味着你可以输入 `cargo build` 或只输入 `cargo b`；<code>--<span class="cargo-prefix">r</span>elease</code> 意味着它可以被替换为 `-r`。

</footnotes>


{{ tablesep() }}


这些是可选的 `rustup` 组件。
用 `rustup component add [tool]` 安装它们。


<div class="color-header tooling">

| 工具           | 描述                                                                                                                                                                 |
| -------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `cargo clippy` | 额外的 ([lints](https://rust-lang.github.io/rust-clippy/master/))，用于捕捉常见的 API 误用和非惯用代码。{{ link(url = "https://github.com/rust-lang/rust-clippy") }} |
| `cargo fmt`    | 自动代码格式化器（`rustup component add rustfmt`）。{{ link(url = "https://github.com/rust-lang/rustfmt") }}                                                         |

</div>

{{ tablesep() }}

可以在[**这里**](https://crates.io/categories/development-tools::cargo-plugins?sort=downloads)找到大量的额外 cargo 插件。


{{ tablesep() }}


## 交叉编译 {#cross-compilation}

<!-- <div class="steps"> -->

<!-- 在小屏幕上创建一个水平滚动区域以保持布局 -->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

🔘 检查[目标是否受支持](https://doc.rust-lang.org/rustc/platform-support.html)。

🔘 通过 **`rustup target install aarch64-linux-android`**（例如）安装目标。

🔘 安装原生工具链（需要用于*链接*，取决于目标）。

从目标供应商处获取（Google, Apple, &hellip;），可能并非在所有主机上都可用（例如，Windows 上没有 iOS 工具链）。

**一些工具链需要额外的构建步骤**（例如，Android 的 `make-standalone-toolchain.sh`）。

🔘 更新 **`~/.cargo/config.toml`**，如下所示：

```
[target.aarch64-linux-android]
linker = "[PATH_TO_TOOLCHAIN]/aarch64-linux-android/bin/aarch64-linux-android-clang"
```

   或

```
[target.aarch64-linux-android]
linker = "C:/[PATH_TO_TOOLCHAIN]/prebuilt/windows-x86_64/bin/aarch64-linux-android21-clang.cmd"
```

🔘 设置**环境变量**（可选，等到编译器抱怨再设置）：

```
set CC=C:\[PATH_TO_TOOLCHAIN]\prebuilt\windows-x86_64\bin\aarch64-linux-android21-clang.cmd
set CXX=C:\[PATH_TO_TOOLCHAIN]\prebuilt\windows-x86_64\bin\aarch64-linux-android21-clang.cmd
set AR=C:\[PATH_TO_TOOLCHAIN]\prebuilt\windows-x86_64\bin\aarch64-linux-android-ar.exe
…
```

是否设置它们取决于编译器如何抱怨，不一定都需要。

> 一些平台/配置对路径的指定方式（例如 `\` vs `/`）和引号**极其敏感**。


✔️ 使用 **`cargo build --target=aarch64-linux-android`** 编译


<!-- End overflow area -->
</div>
</div>

<!-- End steps  -->
<!-- </div> -->

{{ tablesep() }}




## 工具指令 {#tooling-directives}

嵌入在源代码中，由工具或预处理器使用的特殊标记。

<tabs>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-preprocessing-1" name="tab-group-preprocessing" checked>
<label for="tab-preprocessing-1"><b>宏片段</b></label>
<panel><div class="color-header undefined-color-3">

<fixed-2-column class="color-header special_example">

<!-- 工具：**预处理器（自动）** -->


<!-- ```
macro_rules! my_macro {
    ($x:ty) => { ... }
}
``` -->

在**声明式** {{ book(page="ch19-06-macros.html#declarative-macros-with-macro_rules-for-general-metaprogramming") }} **示例宏** {{book(page="ch19-06-macros.html")}} {{ex(page="macros.html#macro_rules")}} {{ref(page="macros-by-example.html")}} `macro_rules!` 实现中，这些**片段指定符** {{ ref(page="macros-by-example.html#metavariables") }} 可以工作：

| 宏内部                     | 解释                                                                             |
| -------------------------- | -------------------------------------------------------------------------------- |
| `$x:ty`                    | 宏捕获（这里 `$x` 是捕获，`ty` 表示 `x` 必须是类型）。                           |
| {{ tab() }} `$x:block`     | 一个语句或表达式的块 `{}`，例如 `{ let x = 5; }`                                 |
| {{ tab() }} `$x:expr`      | 一个表达式，例如 `x`、`1 + 1`、`String::new()` 或 `vec![]`                       |
| {{ tab() }} `$x:expr_2021` | 一个匹配 Rust '21 行为的表达式 {{ rfc(page="3531-macro-fragment-policy.html") }} |
| {{ tab() }} `$x:ident`     | 一个标识符，例如在 `let x = 0;` 中，标识符是 `x`。                               |
| {{ tab() }} `$x:item`      | 一个项，如函数、结构体、模块等。                                                 |
| {{ tab() }} `$x:lifetime`  | 一个生命周期（例如 `'a`、`'static` 等）。                                        |
| {{ tab() }} `$x:literal`   | 一个字面量（例如 `3`、`"foo"`、`b"bar"` 等）。                                   |
| {{ tab() }} `$x:meta`      | 一个元项；放在 `#[…]` 和 `#![…]` 属性内部的东西。                                |
| {{ tab() }} `$x:pat`       | 一个模式，例如 `Some(x)`、`(17, 'a')` 或 <code>x&vert;x</code>。                 |
| {{ tab() }} `$x:pat_param` | 模式的子集，不含顶层 &vert;，例如 `Some(x)` 或 `x`。                             |
| {{ tab() }} `$x:path`      | 一个路径（例如 `foo`、`::std::mem::replace`、`transmute::<_, int>`）。           |
| {{ tab() }} `$x:stmt`      | 一个语句，例如 `let x = 1 + 1;`、`String::new();` 或 `vec![];`                   |
| {{ tab() }} `$x:tt`        | 一个单独的标记树，更多细节请见[这里](https://stackoverflow.com/a/40303308)。     |
| {{ tab() }} `$x:ty`        | 一个类型，例如 `String`、`usize` 或 `Vec<u8>`。                                  |
| {{ tab() }} `$x:vis`       | 一个可见性修饰符；`pub`、`pub(crate)` 等。                                       |
| `$crate`                   | 特殊的卫生变量，宏定义的 crate。{{ todo() }}                                     |

</fixed-2-column>

</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-preprocessing-2" name="tab-group-preprocessing">
<label for="tab-preprocessing-2"><b>文档</b></label>
<panel><div class="color-header undefined-color-2">

<fixed-2-column  class="color-header special_example">

<!-- ```
/// Accepts an [`S`].
///
/// ```rust
///     f(s);
/// ```
``` -->

在**文档注释** {{ book(page="ch14-02-publishing-to-crates-io.html#making-useful-documentation-comments") }} {{ ex(page="meta/doc.html#documentation") }} {{ ref(page="comments.html#doc-comments")}} 中，这些可以工作：

| 文档注释内                                                    | 解释                                                                                                                     |
| ------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| ` ```…``` `                                                   | 包含一个[**文档测试**](https://doc.rust-lang.org/rustdoc/documentation-tests.html)（在 `cargo test` 上运行的文档代码）。 |
| ` ```X,Y …``` `                                               | 同上，并包含可选配置；其中 `X`、`Y` 是……                                                                                 |
| {{ tab() }} <code style="color: gray;">rust</code>            | 明确测试是用 Rust 编写的；由 Rust 工具链暗示。                                                                           |
| {{ tab() }} <code style="color: gray; opacity: 0.3;">-</code> | 编译测试。运行测试。如果 panic 则失败。**默认行为**。                                                                    |
| {{ tab() }} <code style="color: gray;">should_panic</code>    | 编译测试。运行测试。执行应该 panic。如果不是，则测试失败。                                                               |
| {{ tab() }} <code style="color: gray;">no_run</code>          | 编译测试。如果代码无法编译则测试失败，不运行测试。                                                                       |
| {{ tab() }} <code style="color: gray;">compile_fail</code>    | 编译测试，但如果代码*可以*编译则测试失败。                                                                               |
| {{ tab() }} <code style="color: gray;">ignore</code>          | 不编译。不运行。最好使用上面的选项。                                                                                     |
| {{ tab() }} <code style="color: gray;">edition2018</code>     | 将代码作为 Rust '18 执行；默认为 '15。                                                                                   |
| `#`                                                           | 从文档中隐藏行 (` ```   # use x::hidden; ``` `)。                                                                        |
| <code>[&#96;S&#96;]</code>                                    | 创建一个到结构体、枚举、trait、函数等 `S` 的链接。                                                                       |
| <code>[&#96;S&#96;]&#40;crate::S&#41;</code>                  | 也可以使用路径，以 markdown 链接的形式。                                                                                 |


</fixed-2-column>


</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-preprocessing-7" name="tab-group-preprocessing">
<label for="tab-preprocessing-7"><b><code>#![globals]</code></b></label>
<panel><div class="color-header undefined-color-3">

<!-- ```
// Attributes usually found in toplevel project file.
#![no_std]
#![feature(xxx)]
``` -->
<fixed-3-column  class="color-header special_example">

影响整个 crate 或应用程序的属性：

| Opt-Out's                 | 作用于 | 解释                                                                                                                                                                 |
| ------------------------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `#![no_std]`              | `C`    | 不（自动）导入 **`std`**{{ std(page="std/") }}；改用 **`core`**{{ std(page="core/") }}。{{ ref(page="names/preludes.html#the-no_std-attribute") }}                   |
| `#![no_implicit_prelude]` | `CM`   | 不添加 **`prelude`**{{ std(page="std/prelude/index.html") }}，需要手动导入 `None`、`Vec` 等。{{ ref(page="names/preludes.html#the-no_implicit_prelude-attribute") }} |
| `#![no_main]`             | `C`    | 如果你自己做，则不在应用程序中发出 `main()`。{{ ref(page="crates-and-source-files.html#the-no_main-attribute") }}                                                    |

<!-- | `#![no_builtins]` | `C` | Does ... something ... probably important. {{ todo() }} {{ ref(page="attributes/codegen.html#the-no_builtins-attribute") }}| -->

{{ tablesep() }}

| Opt-In's               | 作用于 | 解释                                                                                                                                   |
| ---------------------- | ------ | -------------------------------------------------------------------------------------------------------------------------------------- |
| `#![feature(a, b, c)]` | `C`    | 依赖可能不会稳定的特性，参见 [**Unstable Book**](https://doc.rust-lang.org/unstable-book/the-unstable-book.html)。{{ experimental() }} |

{{ tablesep() }}

| 构建                            | 作用于 | 解释                                                                                                                                                |
| ------------------------------- | ------ | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| `#![crate_name = "x"]`          | `C`    | 指定当前 crate 名称，例如在不使用 `cargo` 时。{{ todo() }} {{ ref(page="crates-and-source-files.html#the-crate_name-attribute") }} {{ esoteric() }} |
| `#![crate_type = "bin"]`        | `C`    | 指定当前 crate 类型（`bin`、`lib`、`dylib`、`cdylib` 等）。{{ ref(page="linkage.html") }} {{ esoteric() }}                                          |
| `#![recursion_limit = "123"]`   | `C`    | 设置解引用、宏等的*编译时*递归限制。{{ ref(page="attributes/limits.html#the-recursion_limit-attribute") }} {{ esoteric() }}                         |
| `#![type_length_limit = "456"]` | `C`    | 限制类型替换的最大数量。{{ ref(page="attributes/limits.html#the-type_length_limit-attribute") }} {{ esoteric() }}                                   |
| `#![windows_subsystem = "x"]`   | `C`    | 在 Windows 上，制作一个 `console` 或 `windows` 应用程序。{{ ref(page="runtime.html#the-windows_subsystem-attribute") }} {{ esoteric() }}            |


{{ tablesep() }}

| 处理器                   | 作用于 | 解释                                                                                                                                                                  |
| ------------------------ | ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `#[alloc_error_handler]` | `F`    | 将某个 `fn(Layout) -> !` 设为**分配失败处理器**。{{ link(url="https://github.com/rust-lang/rust/issues/51540") }} {{ experimental() }}                                |
| `#[global_allocator]`    | `S`    | 将实现了 `GlobalAlloc` {{ std(page="alloc/alloc/trait.GlobalAlloc.html") }} 的静态项设为**全局分配器**。{{ ref(page="runtime.html#the-global_allocator-attribute") }} |
| `#[panic_handler]`       | `F`    | 将某个 `fn(&PanicInfo) -> !` 设为应用程序的**恐慌处理器**。{{ ref(page="runtime.html#the-panic_handler-attribute") }}                                                 |


</fixed-3-column>


</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-preprocessing-4" name="tab-group-preprocessing">
<label for="tab-preprocessing-4"><b><code>#[code]</code></b></label>
<panel><div class="color-header undefined-color-3">

主要控制生成代码的属性：

<fixed-3-column  class="color-header special_example">

| 开发者 UX                         | 作用于 | 解释                                                                                                                             |
| --------------------------------- | ------ | -------------------------------------------------------------------------------------------------------------------------------- |
| `#[non_exhaustive]`               | `T`    | 使 `struct` 或 `enum` 面向未来；提示它将来可能会增长。{{ ref(page="attributes/type_system.html#the-non_exhaustive-attribute") }} |
| `#[path = "x.rs"]`                | `M`    | 从非标准文件获取模块。{{ ref(page="items/modules.html#the-path-attribute") }}                                                    |
| `#[diagnostic::on_unimplemented]` | `X`    | 当 trait 未实现时提供更好的错误消息。{{ rfc(page="3368-diagnostic-attribute-namespace.html") }}                                  |

{{ tablesep() }}

| 代码生成                           | 作用于 | 解释                                                                                                                                                                                    |
| ---------------------------------- | ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `#[cold]`                          | `F`    | 提示函数可能不会被调用。{{ ref(page="attributes/codegen.html#the-cold-attribute") }}                                                                                                    |
| `#[inline]`                        | `F`    | 友好地建议编译器在调用点内联函数。{{ ref(page="attributes/codegen.html#the-inline-attribute") }}                                                                                        |
| `#[inline(always)]`                | `F`    | 强烈威胁编译器内联调用，否则…… {{ ref(page="attributes/codegen.html#the-inline-attribute") }}                                                                                           |
| `#[inline(never)]`                 | `F`    | 指示编译器如果仍然内联函数会感到悲伤。{{ ref(page="attributes/codegen.html#the-inline-attribute") }}                                                                                    |
| `#[repr(X)]`<sup>1</sup>           | `T`    | 使用另一种表示，而不是默认的 **`rust`** {{ ref(page="type-layout.html#the-default-representation") }} 表示：                                                                            |
| `#[target_feature(enable="x")]`    | `F`    | 为 `unsafe fn` 的代码启用 CPU 特性（例如 `avx2`）。{{ ref(page="attributes/codegen.html#the-target_feature-attribute") }}                                                               |
| `#[track_caller]`                  | `F`    | 允许 `fn` 找到**`caller`**{{ std(page="core/panic/struct.Location.html#method.caller") }} 以获得更好的 panic 消息。{{ ref(page="attributes/codegen.html#the-track_caller-attribute") }} |
| {{ tab() }} `#[repr(C)]`           | `T`    | 使用 C 兼容的（用于 FFI）、可预测的（用于 `transmute`）布局。{{ ref(page="type-layout.html#the-c-representation") }}                                                                    |
| {{ tab() }} `#[repr(C, u8)]`       | `enum` | 给 `enum` 的判别值指定类型。{{ ref(page="type-layout.html#the-c-representation") }}                                                                                                     |
| {{ tab() }} `#[repr(transparent)]` | `T`    | 使单元素类型的布局与包含的字段相同。{{ ref(page="type-layout.html#the-transparent-representation") }}                                                                                   |
| {{ tab() }} `#[repr(packed(1))]`   | `T`    | 降低结构体和包含字段的对齐，轻微易于 UB。{{ ref(page="type-layout.html#the-alignment-modifiers") }}                                                                                     |
| {{ tab() }} `#[repr(align(8))]`    | `T`    | 将结构体的对齐提高到给定值，例如用于 SIMD 类型。{{ ref(page="type-layout.html#the-alignment-modifiers") }}                                                                              |

<!-- {{ tablesep() }}

| 表示                   | 作用于 | 解释                                                                                                                        |
| ---------------------- | ------ | --------------------------------------------------------------------------------------------------------------------------- |
| `-`                    | `T`    | In absence of `#[repr]` the **`rust` representation** is used {{ ref(page="type-layout.html#the-default-representation") }} |
| `#[repr(C)]`           | `T`    | Use a predictable, C-compatible representation. {{ ref(page="type-layout.html#the-c-representation") }}                     |
| `#[repr(C, u8)]`       | `enum` | Give `enum` discriminant the specified type. {{ ref(page="type-layout.html#the-c-representation") }}                        |
| `#[repr(transparent)]` | `T`    | Give single-element type same layout as contained field. {{ ref(page="type-layout.html#the-transparent-representation") }}  |
| `#[repr(packed(1))]`   | `T`    | Lower alignment of struct and contained fields, mildly UB prone. {{ ref(page="type-layout.html#the-alignment-modifiers") }} |
| `#[repr(align(8))]`    | `T`    | Raise alignment of struct to given value, e.g., for SIMD types. {{ ref(page="type-layout.html#the-alignment-modifiers") }}  | --> |

<footnotes>

<sup>1</sup> 一些表示修饰符可以组合使用，例如 `#[repr(C, packed(1))]`。

</footnotes>

{{ tablesep() }}

| 链接                             | 作用于 | 解释                                                                                                    |
| -------------------------------- | ------ | ------------------------------------------------------------------------------------------------------- |
| `#[unsafe(no_mangle)]`           | `*`    | 直接使用项名作为符号名，而不是进行名称修饰。{{ ref(page="abi.html#the-no_mangle-attribute") }}          |
| `#[unsafe(export_name = "foo")]` | `FS`   | 以不同名称导出一个 `fn` 或 `static`。{{ ref(page="abi.html#the-export_name-attribute") }}               |
| `#[unsafe(link_section = ".x")]` | `FS`   | 项应放置的目标文件的节名。{{ ref(page="abi.html#the-link_section-attribute") }}                         |
| `#[link(name="x", kind="y")]`    | `X`    | 查找符号时要链接的原生库。{{ ref(page="items/external-blocks.html#the-link-attribute") }}               |
| `#[link_name = "foo"]`           | `F`    | 解析 `extern fn` 时要搜索的符号名。{{ ref(page="items/external-blocks.html#the-link_name-attribute") }} |
| `#[no_link]`                     | `X`    | 当只需要宏时，不链接 `extern crate`。{{ ref(page="items/extern-crates.html#the-no_link-attribute") }}   |
| `#[used]`                        | `S`    | 即使 `static` 变量看起来未使用，也不要优化掉。{{ ref(page="abi.html#the-used-attribute") }}             |



</fixed-3-column>

</div></panel></tab>




<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-preprocessing-3" name="tab-group-preprocessing">
<label for="tab-preprocessing-3"><b><code>#[quality]</code></b></label>
<panel><div class="color-header undefined-color-3">

Rust 工具用于提高代码质量的属性：

<fixed-3-column  class="color-header special_example">

| 代码模式                    | 作用于 | 解释                                                                                                                            |
| --------------------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------- |
| `#[allow(X)]`               | `*`    | 指示 `rustc` / `clippy` 忽略 `X` 类的可能问题。{{ ref(page="attributes/diagnostics.html#lint-check-attributes") }}              |
| `#[expect(X)]` <sup>1</sup> | `*`    | 如果 lint 未触发，则发出警告。{{ ref(page="attributes/diagnostics.html#lint-check-attributes") }}                               |
| `#[warn(X)]` <sup>1</sup>   | `*`    | … 发出警告，与 `clippy` lints 混合使用效果很好。{{ hot() }} {{ ref(page="attributes/diagnostics.html#lint-check-attributes") }} |
| `#[deny(X)]` <sup>1</sup>   | `*`    | … 编译失败。{{ ref(page="attributes/diagnostics.html#lint-check-attributes") }}                                                 |
| `#[forbid(X)]` <sup>1</sup> | `*`    | … 编译失败并阻止后续的 `allow` 覆盖。{{ ref(page="attributes/diagnostics.html#lint-check-attributes") }}                        |
| `#[deprecated = "msg"]`     | `*`    | 让你的用户知道你犯了一个设计错误。{{ ref(page="diagnostics.html#the-deprecated-attribute") }}                                   |
| `#[must_use = "msg"]`       | `FTX`  | 使编译器检查返回值是否被调用者*处理*。{{ hot() }} {{ ref(page="attributes/diagnostics.html#the-must_use-attribute") }}          |

<footnotes>

<sup>1</sup> {{ opinionated() }} 关于哪种方法是确保高质量 crate 的*最佳*方法存在一些争论。积极维护的多开发者 crate 可能从更激进的 `deny` 或 `forbid` lints 中受益；不定期更新的 crate 可能更多地从保守使用 `warn` 中受益（因为未来的编译器或 `clippy` 更新可能会突然破坏原本工作正常的、有轻微问题的代码）。

</footnotes>

{{ tablesep() }}

</fixed-3-column>

<fixed-3-column  class="color-header special_example">

| 测试                | 作用于 | 解释                                                                                                             |
| ------------------- | ------ | ---------------------------------------------------------------------------------------------------------------- |
| `#[test]`           | `F`    | 将函数标记为测试，用 `cargo test` 运行。{{ hot() }} {{ ref(page="attributes/testing.html#the-test-attribute") }} |
| `#[ignore = "msg"]` | `F`    | 编译但暂时不执行某个 `#[test]`。{{ ref(page="attributes/testing.html#the-ignore-attribute") }}                   |
| `#[should_panic]`   | `F`    | 测试必须 `panic!()` 才能真正成功。{{ ref(page="attributes/testing.html#the-ignore-attribute") }}                 |
| `#[bench]`          | `F`    | 将 `bench/` 中的函数标记为 `cargo bench` 的基准测试。{{ experimental() }} {{ ref(page="") }}                     |

{{ tablesep() }}


| 格式化                             | 作用于 | 解释                                                                            |
| ---------------------------------- | ------ | ------------------------------------------------------------------------------- |
| `#[rustfmt::skip]`                 | `*`    | 防止 `cargo fmt` 清理项。{{ link(url="https://github.com/rust-lang/rustfmt") }} |
| `#![rustfmt::skip::macros(x)]`     | `CM`   | … 防止清理宏 `x`。{{ link(url="https://github.com/rust-lang/rustfmt") }}        |
| `#![rustfmt::skip::attributes(x)]` | `CM`   | … 防止清理属性 `x`。{{ link(url="https://github.com/rust-lang/rustfmt") }}      |

</fixed-3-column>

{{ tablesep() }}

<fixed-3-column class="color-header special_example extra-wide">


| 文档                                 | 作用于 | 解释                                                                                                                                                |
| ------------------------------------ | ------ | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| `#[doc = "Explanation"]`             | `*`    | 与添加 `///` 文档注释相同。{{ link(url="https://doc.rust-lang.org/rustdoc/the-doc-attribute.html") }}                                               |
| `#[doc(alias = "other")]`            | `*`    | 为文档中的搜索提供别名。{{ link(url="https://github.com/rust-lang/rust/issues/50146") }}                                                            |
| `#[doc(hidden)]`                     | `*`    | 防止项在文档中显示。{{ link(url="https://doc.rust-lang.org/rustdoc/write-documentation/the-doc-attribute.html#hidden") }}                           |
| `#![doc(html_favicon_url = "")]`     | `C`    | 设置文档的 `favicon`。{{ link(url="https://doc.rust-lang.org/rustdoc/write-documentation/the-doc-attribute.html#html_favicon_url") }}               |
| `#![doc(html_logo_url  = "")]`       | `C`    | 文档中使用的 logo。{{ link(url="https://doc.rust-lang.org/rustdoc/write-documentation/the-doc-attribute.html#html_logo_url") }}                     |
| `#![doc(html_playground_url  = "")]` | `C`    | 生成 `Run` 按钮并使用给定的服务。{{ link(url="https://doc.rust-lang.org/rustdoc/write-documentation/the-doc-attribute.html#html_playground_url") }} |
| `#![doc(html_root_url  = "")]`       | `C`    | 到外部 crate 链接的基本 URL。{{ link(url="https://doc.rust-lang.org/rustdoc/write-documentation/the-doc-attribute.html#html_root_url") }}           |
| `#![doc(html_no_source)]`            | `C`    | 防止源代码被包含在文档中。{{ link(url="https://doc.rust-lang.org/rustdoc/write-documentation/the-doc-attribute.html#html_no_source") }}             |

<!-- | `#![doc(issue_tracker_base_url  = "")]` | `C` | Mostly for `std::`, where issue numbers link. {{ link(url="https://doc.rust-lang.org/rustdoc/the-doc-attribute.html#issue_tracker_base_url") }}| -->

</fixed-3-column>




</div></panel></tab>




<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-preprocessing-8" name="tab-group-preprocessing">
<label for="tab-preprocessing-8"><b><code>#[macros]</code></b></label>
<panel><div class="color-header undefined-color-3">

<fixed-3-column  class="color-header special_example">

与宏的创建和使用相关的属性：

| 示例宏            | 作用于 | 解释                                                                                                             |
| ----------------- | ------ | ---------------------------------------------------------------------------------------------------------------- |
| `#[macro_export]` | `!`    | 在 crate 级别将 `macro_rules!` 导出为 `pub` {{ ref(page="macros-by-example.html#path-based-scope") }}            |
| `#[macro_use]`    | `MX`   | 使宏在模块之外持久化；或从 `extern crate` 导入。{{ ref(page="macros-by-example.html#the-macro_use-attribute") }} |

{{ tablesep() }}

| 过程宏                      | 作用于 | 解释                                                                                                                         |
| --------------------------- | ------ | ---------------------------------------------------------------------------------------------------------------------------- |
| `#[proc_macro]`             | `F`    | 将 `fn` 标记为**函数式**过程宏，可作为 `m!()` 调用。{{ ref(page="procedural-macros.html#function-like-procedural-macros") }} |
| `#[proc_macro_derive(Foo)]` | `F`    | 将 `fn` 标记为**派生宏**，可以 `#[derive(Foo)]`。{{ ref(page="procedural-macros.html#derive-macros") }}                      |
| `#[proc_macro_attribute]`   | `F`    | 将 `fn` 标记为**属性宏**，用于新的 `#[x]`。{{ ref(page="procedural-macros.html#attribute-macros") }}                         |

{{ tablesep() }}

| 派生           | 作用于 | 解释                                                                               |
| -------------- | ------ | ---------------------------------------------------------------------------------- |
| `#[derive(X)]` | `T`    | 让某个过程宏提供一个相当不错的 `trait X` 的 `impl`。{{ hot() }} {{ ref(page="") }} |

<!-- | `#[derive(Eq)]` |  | xxx{{ ref(page="") }}|
| `#[derive(PartialEq)]` | |  xxx|
| `#[derive(Ord)]` | |  xxx|
| `#[derive(PartialOrd)]` | |  xxx|
| `#[derive(Clone)]` | |  xxx|
| `#[derive(Copy)]` | |  xxx|
| `#[derive(Hash)]` | |  xxx|
| `#[derive(Default)]` | |  xxx|
| `#[derive(Debug)]` | |  xxx| -->


</fixed-3-column>


</div></panel></tab>






<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-preprocessing-5" name="tab-group-preprocessing">
<label for="tab-preprocessing-5"><b><code>#[cfg]</code></b></label>
<panel><div class="color-header undefined-color-3">

控制条件编译的属性：

<fixed-3-column class="color-header special_example extra-wide">

| 配置属性                      | 作用于 | 解释                                                                                                              |
| ----------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------- |
| `#[cfg(X)]`                   | `*`    | 如果配置 `X` 成立，则包含该项。{{ ref(page="conditional-compilation.html#the-cfg-attribute") }}                   |
| `#[cfg(all(X, Y, Z))]`        | `*`    | 如果所有选项都成立，则包含该项。{{ ref(page="conditional-compilation.html#conditional-compilation") }}            |
| `#[cfg(any(X, Y, Z))]`        | `*`    | 如果至少有一个选项成立，则包含该项。{{ ref(page="conditional-compilation.html#conditional-compilation") }}        |
| `#[cfg(not(X))]`              | `*`    | 如果 `X` 不成立，则包含该项。{{ ref(page="conditional-compilation.html#conditional-compilation") }}               |
| `#[cfg_attr(X, foo = "msg")]` | `*`    | 如果配置 `X` 成立，则应用 `#[foo = "msg"]`。{{ ref(page="conditional-compilation.html#the-cfg_attr-attribute") }} |

{{ tablesep() }}

> ⚠️ 注意，选项通常可以设置多次，即同一个键可以出现多次，带有不同的值。可以期望 `#[cfg(target_feature = "avx")]` **和** `#[cfg(target_feature = "avx2")]` 同时为真。

{{ tablesep() }}

| 已知选项                              | 作用于 | 解释                                                                                                                   |
| ------------------------------------- | ------ | ---------------------------------------------------------------------------------------------------------------------- |
| `#[cfg(debug_assertions)]`            | `*`    | `debug_assert!()` 等是否会 panic。{{ ref(page="conditional-compilation.html#debug_assertions") }}                      |
| `#[cfg(feature = "foo")]`             | `*`    | 当你的 crate 用*特性* `foo` 编译时。{{ hot() }} {{ ref(page="conditional-compilation.html#conditional-compilation") }} |
| `#[cfg(target_arch = "x86_64")]`      | `*`    | crate 编译的目标 CPU 架构。{{ ref(page="conditional-compilation.html#target_arch") }}                                  |
| `#[cfg(target_env = "msvc")]`         | `*`    | 在操作系统上如何与 DLL 和函数交互。{{ ref(page="conditional-compilation.html#target_env") }}                           |
| `#[cfg(target_endian = "little")]`    | `*`    | 你的新零成本协议失败的主要原因。{{ ref(page="conditional-compilation.html#target_endian") }}                           |
| `#[cfg(target_family = "unix")]`      | `*`    | 操作系统所属的家族。{{ ref(page="conditional-compilation.html#target_family") }}                                       |
| `#[cfg(target_feature = "avx")]`      | `*`    | 某个特定指令集是否可用。{{ ref(page="conditional-compilation.html#target_feature") }}                                  |
| `#[cfg(target_os = "macos")]`         | `*`    | 你的代码将运行的操作系统。{{ ref(page="conditional-compilation.html#target_os") }}                                     |
| `#[cfg(target_pointer_width = "64")]` | `*`    | 指针、`usize` 和字的位数。{{ ref(page="conditional-compilation.html#target_pointer_width") }}                          |
| `#[cfg(target_vendor = "apple")]`     | `*`    | 目标的制造商。{{ ref(page="conditional-compilation.html#target_vendor") }}                                             |
| `#[cfg(panic = "unwind")]`            | `*`    | panic 时是 `unwind` 还是 `abort`。{{ todo() }}                                                                         |
| `#[cfg(proc_macro)]`                  | `*`    | crate 是否作为过程宏编译。{{ ref(page="conditional-compilation.html#proc_macro") }}                                    |
| `#[cfg(test)]`                        | `*`    | 是否用 `cargo test` 编译。{{ hot() }} {{ ref(page="conditional-compilation.html#test") }}                              |

</fixed-3-column>



</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-preprocessing-6" name="tab-group-preprocessing">
<label for="tab-preprocessing-6"><b><code>build.rs</code></b></label>
<panel><div class="color-header undefined-color-3">

与预构建脚本相关的环境变量和输出。考虑使用 **build-rs**{{ link(url="https://docs.rs/build-rs/0.1.2/build/") }}。

<fixed-2-column class="color-header special_example extra-wide">

| 输入环境变量                                    | 解释 {{ link(url="https://doc.rust-lang.org/cargo/reference/environment-variables.html") }} |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `CARGO_FEATURE_X`                               | 为每个激活的特性 `x` 设置的环境变量。                                                       |
| {{ tab() }} `CARGO_FEATURE_SOMETHING`           | 如果特性 `something` 被启用。                                                               |
| {{ tab() }} `CARGO_FEATURE_SOME_FEATURE`        | 如果*特性* `some-feature` 被启用；破折号 `-` 被转换为 `_`。                                 |
| `CARGO_CFG_X`                                   | 暴露 cfg；通过 `,` 连接多个选项，并将 `-` 转换为 `_`。                                      |
| {{ tab() }} `CARGO_CFG_TARGET_OS=macos`         | 如果 `target_os` 设置为 `macos`。                                                           |
| {{ tab() }} `CARGO_CFG_TARGET_FEATURE=avx,avx2` | 如果 `target_feature` 设置为 `avx` 和 `avx2`。                                              |
| `OUT_DIR`                                       | 输出应放置的位置。                                                                          |
| `TARGET`                                        | 正在编译的目标三元组。                                                                      |
| `HOST`                                          | 主机三元组（运行此构建脚本）。                                                              |
| `PROFILE`                                       | 可以是 `debug` 或 `release`。                                                               |

<footnotes>

在 `build.rs` 中通过 `env::var()?` 可用。列表不详尽。

</footnotes>

</fixed-2-column>

<fixed-2-column class="color-header special_example extra-wide">

{{ tablesep() }}

| 输出字符串                             | 解释 {{ link(url="https://doc.rust-lang.org/cargo/reference/build-scripts.html") }} |
| -------------------------------------- | ----------------------------------------------------------------------------------- |
| `cargo::rerun-if-changed=PATH`         | 如果 `PATH` 改变，（仅）再次运行此 `build.rs`。                                     |
| `cargo::rerun-if-env-changed=VAR`      | 如果环境 `VAR` 改变，（仅）再次运行此 `build.rs`。                                  |
| `cargo::rustc-cfg=KEY[="VALUE"]`       | 发出给定的 `cfg` 选项，用于后续编译。                                               |
| `cargo::rustc-cdylib-link-arg=FLAG `   | 构建 `cdylib` 时，传递链接器标志。                                                  |
| `cargo::rustc-env=VAR=VALUE `          | 发出可在编译期间通过 `env!()` 访问的变量。                                          |
| `cargo::rustc-flags=FLAGS`             | 向编译器添加特殊标志。{{ todo() }}                                                  |
| `cargo::rustc-link-lib=[KIND=]NAME`    | 链接原生库，如同通过 `-l` 选项。                                                    |
| `cargo::rustc-link-search=[KIND=]PATH` | 搜索原生库的路径，如同通过 `-L` 选项。                                              |
| `cargo::warning=MESSAGE`               | 发出编译器警告。                                                                    |

<footnotes>

从 `build.rs` 通过 `println!()` 发出。列表不详尽。

</footnotes>

</fixed-2-column>

</div></panel></tab>


</tabs>


<footnotes>

对于属性上的*作用于*列：<br>
`C` 表示在 crate 级别（通常在顶层文件中以 `#![my_attr]` 形式给出）。<br>
`M` 表示在模块上。<br>
`F` 表示在函数上。<br>
`S` 表示在静态项上。<br>
`T` 表示在类型上。<br>
`X` 表示某些特殊情况。<br>
`!` 表示在宏上。<br>
`*` 表示在几乎任何项上。<br>

</footnotes>


---

# 处理类型


## 类型、Trait、泛型 {#types-traits-generics}

允许用户*自带类型*并避免代码重复。

<tabs>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-types-1" name="tab-group-types" checked>
<label for="tab-types-1"><b>类型与 Trait</b></label>
<panel><div>


<!-- Section -->
<generics-section id="ttg-types">
<header>类型</header>
<description>

<mini-zoo class="zoo">
    <entry>
        <type class="primitive"><code>u8</code></type>
    </entry>
    <entry>
        <type class="composed"><code>String</code></type>
    </entry>
    <entry>
        <type class="composed"><code>Device</code></type>
    </entry>
</mini-zoo>

- 具有给定语义、布局等的一组值。

<mini-table>

| 类型                 | 值                                                                   |
| -------------------- | -------------------------------------------------------------------- |
| `u8`                 | <code>{ 0<sub>u8</sub>, 1<sub>u8</sub>, …, 255<sub>u8</sub> }</code> |
| `char`               | `{ 'a', 'b', … '🦀' }`                                                |
| `struct S(u8, char)` | <code>{ (0<sub>u8</sub>, 'a'), … (255<sub>u8</sub>, '🦀') }</code>    |

<subtitle>示例类型和示例值。</subtitle>

</mini-table>

</description>
</generics-section>


<!-- Section -->
<generics-section id="ttg-equivalence">
<header>类型等价与转换</header>
<description>

<mini-zoo class="zoo">
    <entry>
        <type class="primitive"><code>u8</code></type>
    </entry>
    <entry>
        <type class="primitive"><code>&u8</code></type>
    </entry>
    <entry>
        <type class="primitive"><code>&mut u8</code></type>
    </entry>
    <entry>
        <type class="primitive"><code>[u8; 1]</code></type>
    </entry>
    <entry>
        <type class="composed"><code>String</code></type>
    </entry>
</mini-zoo>



<!-- - 问题：上面的类型中哪一个与其他所有类型都不同？
    - 陷阱问题：所有这些类型都完全不同 -->
- 这可能很明显，但 &nbsp; `u8`、&nbsp;&nbsp; `&u8`、&nbsp;&nbsp; `&mut u8` 彼此完全不同
- 任何 `t: T` 只接受来自精确 `T` 的值，例如，
    - `f(0_u8)` 不能用 `f(&0_u8)` 调用，
    - `f(&mut my_u8)` 不能用 `f(&my_u8)` 调用，
    - `f(0_u8)` 不能用 `f(0_i8)` 调用。

>  是的，在类型方面 `0 != 0`（在数学意义上）！在语言意义上，操作 <code>==(0<sub>u8</sub>, 0<sub>u16</sub>)</code> 根本没有定义，以防止意外发生。

<mini-table>

| 类型      | 值                                                                         |
| --------- | -------------------------------------------------------------------------- |
| `u8`      | <code>{ 0<sub>u8</sub>, 1<sub>u8</sub>, …, 255<sub>u8</sub> }</code>       |
| `u16`     | <code>{ 0<sub>u16</sub>, 1<sub>u16</sub>, …, 65_535<sub>u16</sub> }</code> |
| `&u8`     | <code>{ 0xffaa<sub>&u8</sub>, 0xffbb<sub>&u8</sub>, … }</code>             |
| `&mut u8` | <code>{ 0xffaa<sub>&mut u8</sub>, 0xffbb<sub>&mut u8</sub>, … }</code>     |

<subtitle>不同类型的值如何不同。</subtitle>

</mini-table>



- 然而，Rust 有时可能会帮助**在类型之间进行转换**<sup>1</sup>
    - **casts** 手动转换类型的值，`0_i8 as u8`
    - **coercions** {{ above(target="#language-sugar") }} 在安全的情况下自动转换类型<sup>2</sup>，`let x: &u8 = &mut 0_u8;`




<footnotes>

<sup>1</sup> Casts 和 coercions 将值从一个集合（例如 `u8`）转换为另一个集合（例如 `u16`），可能需要添加 CPU 指令来这样做；这与**子类型化 (subtyping)** 不同，后者意味着类型和子类型是同一集合的一部分（例如，`u8` 是 `u16` 的子类型，`0_u8` 与 `0_u16` 相同），这种转换将纯粹是编译时检查。Rust 不对常规类型使用子类型化（`0_u8` *确实*不同于 `0_u16`），但对生命周期则有所不同。{{ link(url = "https://featherweightmusings.blogspot.com/2014/03/subtyping-and-coercion-in-rust.html") }}

<sup>2</sup> 此处的安全不仅是物理概念（例如，<code>&u8</code> 不能被强制转换为 <code>&u128</code>），还包括“历史表明这种转换会导致编程错误”。

</footnotes>

</description>
</generics-section>



<!-- Section -->
<generics-section id="ttg-impl-s">
<header>实现 &mdash; <code>impl S { }</code></header>
<description>

<mini-zoo class="zoo">
    <entry>
        <type class="primitive"><code>u8</code></type>
        <impl><code>impl { … }</code></impl>
    </entry>
    <entry>
        <type class="composed"><code>String</code></type>
        <impl><code>impl { … }</code></impl>
    </entry>
    <entry>
        <type class="composed"><code>Port</code></type>
        <impl><code>impl { … }</code></impl>
    </entry>
</mini-zoo>

```
impl Port {
    fn f() { … }
}
```

- 类型通常带有**固有实现**，{{ ref(page="items/implementations.html#inherent-implementations") }} 例如 `impl Port {}`，与类型*相关*的行为：
    - **关联函数** `Port::new(80)`
    - **方法** `port.close()`

> 什么被认为是*相关的*，更多是哲学上的而非技术上的，没有什么（除了良好的品味）可以阻止 `u8::play_sound()` 的发生。


</description>
</generics-section>


<!-- Section -->
<generics-section id="ttg-traits">
<header>Trait &mdash; <code>trait T { }</code></header>
<description>

<mini-zoo class="zoo">
    <entry>
        <trait-impl>⌾ <code>Copy</code></trait-impl>
    </entry>
    <entry>
        <trait-impl>⌾ <code>Clone</code></trait-impl>
    </entry>
    <entry>
        <trait-impl>⌾ <code>Sized</code></trait-impl>
    </entry>
    <entry>
        <trait-impl>⌾ <code>ShowHex</code></trait-impl>
    </entry>
</mini-zoo>

- **Trait** …
    - 是“抽象”行为的一种方式，
    - trait 作者声明语义上*这个 trait 意味着 X*，
    - 其他人可以为他们的类型实现（“订阅”）该行为。
- 可以将 trait 视为类型的“成员列表”：


<mini-table>

<mini-table style="width: 200px; display:inline-block;">

<table>
    <thead>
        <tr style=""><th>Copy Trait</th></tr>
        <tr class="subheader"><th><code>Self</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>u8</code></td></tr>
        <tr><td><code>u16</code></td></tr>
        <tr><td><code>…</code></td></tr>
    </tbody>
</table>

</mini-table>

<mini-table style="width: 200px; display:inline-block;">

<table>
    <thead>
        <tr style=""><th>Clone Trait</th></tr>
        <tr class="subheader"><th><code>Self</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>u8</code></td></tr>
        <tr><td><code>String</code></td></tr>
        <tr><td><code>…</code></td></tr>
    </tbody>
</table>

</mini-table>

<mini-table style="width: 200px; display:inline-block;">

<table>
    <thead>
        <tr style=""><th>Sized Trait</th></tr>
        <tr class="subheader"><th><code>Self</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>char</code></td></tr>
        <tr><td><code>Port</code></td></tr>
        <tr><td><code>…</code></td></tr>
    </tbody>
</table>

</mini-table>

<subtitle>Trait 作为成员表，<code>Self</code> 指的是包含的类型。</subtitle>

</mini-table>


- **任何属于该成员列表的成员都将遵守列表的行为。**
- Trait 也可以包含关联方法、函数等。

```
trait ShowHex {
    // 必须根据文档实现。
    fn as_hex() -> String;

    // 由 trait 作者提供。
    fn print_hex() {}
}
```

<mini-zoo class="zoo">
    <entry>
        <trait-impl>⌾ <code>Copy</code></trait-impl>
    </entry>
</mini-zoo>

```
trait Copy { }
```

- 没有方法的 Trait 通常称为**标记 trait (marker traits)**。
- `Copy` 是一个标记 trait 的例子，表示*内存可以按位复制*。

<mini-zoo class="zoo">
    <entry>
        <trait-impl>⌾ <code>Sized</code></trait-impl>
    </entry>
</mini-zoo>


- 有些 trait 完全不受显式控制
- `Sized` 由编译器为具有*已知大小*的类型提供；要么是，要么不是


</description>
</generics-section>


<!-- Section -->
<generics-section>
<header>为类型实现 Trait &mdash; <code>impl T for S { }</code></header>
<description>


```
impl ShowHex for Port { … }
```
- Trait 是在“某个时刻”为类型实现的。
- 实现 `impl A for B` 将类型 `B` 添加到 trait 成员列表中：

<mini-table>

<mini-table style="width: 200px; display:inline-block;">

<table>
    <thead>
        <tr><th>ShowHex Trait</th></tr>
        <tr class="subheader"><th><code>Self</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>Port</code></td></tr>
    </tbody>
</table>

</mini-table>
</mini-table>

- 从视觉上讲，你可以认为类型为其成员资格获得了一个“徽章”：

<mini-zoo class="zoo">
    <entry>
        <type class="primitive"><code>u8</code></type>
        <impl><code>impl { … }</code></impl>
        <trait-impl>⌾ <code>Sized</code></trait-impl>
        <trait-impl>⌾ <code>Clone</code></trait-impl>
        <trait-impl>⌾ <code>Copy</code></trait-impl>
    </entry>
    <entry>
        <type class="composed"><code>Device</code></type>
        <impl><code>impl { … }</code></impl>
        <trait-impl>⌾ <code>Transport</code></trait-impl>
    </entry>
    <entry>
        <type class="composed"><code>Port</code></type>
        <impl><code>impl { … }</code></impl>
        <trait-impl>⌾ <code>Sized</code></trait-impl>
        <trait-impl>⌾ <code>Clone</code></trait-impl>
        <trait-impl>⌾ <code>ShowHex</code></trait-impl>
    </entry>
</mini-zoo>

</description>
</generics-section>




<!-- Section -->
<generics-section>
<header>Trait 与接口</header>
<description>


<mini-zoo class="zoo">
    <person>👩‍🦰</person>
    <entry>
        <trait-impl>⌾ <code>Eat</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="margin-left: 10px;">
    <person>🧔</person>
    <entry>
        <type class="composed"><code>Venison</code></type>
        <trait-impl>⌾ <code>Eat</code></trait-impl>
    </entry>
</mini-zoo>


<mini-zoo class="zoo" style="margin-left: 10px; width: 130px;">
    <person></person>
    <entry>
        <code style="text-align:center; width: 100%;"></code>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="margin-left: 10px;">
    <person>🎅</person>
    <entry>
        <code>venison.eat()</code>
    </entry>
</mini-zoo>

{{ tablesep() }}

**接口**

- 在 **Java** 中，Alice 创建了接口 `Eat`。
- 当 Bob 编写 `Venison` 时，他必须决定 `Venison` 是否实现 `Eat`。
- 换句话说，所有成员资格都必须在类型定义期间详尽声明。
- 在使用 `Venison` 时，Santa 可以利用 `Eat` 提供的行为：

```
// Santa 导入 `Venison` 来创建它，如果他想，可以 `eat()`。
import food.Venison;

new Venison("rudolph").eat();
```


{{ tablesep() }}
{{ tablesep() }}


<mini-zoo class="zoo">
    <person>👩‍🦰</person>
    <entry>
        <trait-impl>⌾ <code>Eat</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="margin-left: 10px;">
    <person>🧔</person>
    <entry>
        <type class="composed"><code>Venison</code></type>
    </entry>
</mini-zoo>


<mini-zoo class="zoo" style="margin-left: 10px;">
    <person>👩‍🦰</person> / <person>🧔</person>
    <entry>
        <type class="composed"><code>Venison</code></type>
        <code style="text-align:center; width: 100%;">+</code>
        <trait-impl>⌾ <code>Eat</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="margin-left: 10px;">
    <person>🎅</person>
    <entry>
        <code>venison.eat()</code>
    </entry>
</mini-zoo>

{{ tablesep() }}

**Trait**

- 在 **Rust** 中，Alice 创建了 trait `Eat`。
- Bob 创建了类型 `Venison` 并决定不实现 `Eat`（他甚至可能不知道 `Eat`）。
- 后来*某人*<sup>*</sup>决定将 `Eat` 添加到 `Venison` 是一个非常好的主意。
- 在使用 `Venison` 时，Santa 必须单独导入 `Eat`：

```
// Santa 需要导入 `Venison` 来创建它，并导入 `Eat` 来使用 trait 方法。
use food::Venison;
use tasks::Eat;

// 呵呵呵
Venison::new("rudolph").eat();
```

<footnotes>

<sup>*</sup> 为了防止两个人以不同的方式实现 `Eat`，Rust 将该选择限制为 Alice 或 Bob；也就是说，`impl Eat for Venison` 只能发生在 `Venison` 的 crate 中或 `Eat` 的 crate 中。有关详细信息，请参见一致性。{{todo()}}

</footnotes>


</description>
</generics-section>


</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-types-2" name="tab-group-types">
<label for="tab-types-2"><b>泛型</b></label>
<panel><div>


<!-- Section -->
<generics-section>
<header>类型构造器 &mdash; <code>Vec&lt;&gt;</code></header>
<description>

<mini-zoo class="zoo">
    <entry>
        <type class="composed"><code>Vec&lt;u8&gt;</code></type>
    </entry>
    <entry>
        <type class="composed"><code>Vec&lt;char&gt;</code></type>
    </entry>
</mini-zoo>

- `Vec<u8>` 是“字节向量”类型；`Vec<char>` 是“字符向量”类型，但 `Vec<>` 是什么？

<mini-table>

| 构造        | 值                                  |
| ----------- | ----------------------------------- |
| `Vec<u8>`   | `{ [], [1], [1, 2, 3], … }`         |
| `Vec<char>` | `{ [], ['a'], ['x', 'y', 'z'], … }` |
| `Vec<>`     | -                                   |

<subtitle>类型与类型构造器。</subtitle>

</mini-table>



<mini-zoo class="zoo">
    <entry>
        <type class="generic dotted"><code>Vec&lt;&gt;</code></type>
    </entry>
</mini-zoo>

- `Vec<>` 不是类型，不占用内存，甚至不能翻译成代码。
- `Vec<>` 是**类型构造器 (type constructor)**，一个“模板”或“创建类型的配方”
    - 允许第三方通过参数构造具体的类型，
    - 只有这样，这个 `Vec<UserType>` 才会成为一个真正的类型本身。

</description>
</generics-section>


<!-- Section -->
<generics-section>
<header>泛型参数 &mdash; <code>&lt;T&gt;</code></header>
<description>

<mini-zoo class="zoo">
    <entry>
        <type class="generic dotted"><code>Vec&lt;T&gt;</code></type>
    </entry>
    <entry>
        <type class="generic dotted"><code>[T; 128]</code></type>
    </entry>
    <entry>
        <type class="generic dotted"><code>&T</code></type>
    </entry>
    <entry>
        <type class="generic dotted"><code>&mut T</code></type>
    </entry>
    <entry>
        <type class="generic dotted"><code>S&lt;T&gt;</code></type>
    </entry>
</mini-zoo>

- `Vec<>` 的参数通常命名为 `T`，因此是 `Vec<T>`。
- `T` 是一个“类型的变量名”，供用户插入具体的东西，如 `Vec<f32>`、`S<u8>` 等。


<mini-table>

| 类型构造器         | 产生族                                      |
| ------------------ | ------------------------------------------- |
| `struct Vec<T> {}` | `Vec<u8>`, `Vec<f32>`, `Vec<Vec<u8>>`, …    |
| `[T; 128]`         | `[u8; 128]`, `[char; 128]`, `[Port; 128]` … |
| `&T`               | `&u8`, `&u16`, `&str`,  …                   |

<subtitle>类型与类型构造器。</subtitle>

</mini-table>


```
// S<> 是带有参数 T 的类型构造器；用户可以为 T 提供任何具体类型。
struct S<T> {
    x: T
}

// 在“具体”代码中，必须为 T 提供一个现有类型。
fn f() {
    let x: S<f32> = S::new(0_f32);
}

```

</description>
</generics-section>


<!-- Section -->
<generics-section >
<header>常量泛型 &mdash; <code>[T; N]</code> 和 <code>S&lt;const N: usize&gt;</code></header>
<description>

<mini-zoo class="zoo">
    <entry>
        <type class="generic dotted"><code>[T; n]</code></type>
    </entry>
    <entry>
        <type class="generic dotted"><code>S&lt;const N&gt;</code></type>
    </entry>
</mini-zoo>

- 一些类型构造器不仅接受特定类型，还接受**特定常量**。
- `[T; n]` 构造一个包含 `n` 次 `T` 类型的数组类型。
- 对于自定义类型，声明为 `MyArray<T, const N: usize>`。

<mini-table>

| 类型构造器                    | 产生族                             |
| ----------------------------- | ---------------------------------- |
| `[u8; N]`                     | `[u8; 0]`, `[u8; 1]`, `[u8; 2]`, … |
| `struct S<const N: usize> {}` | `S<1>`, `S<6>`, `S<123>`,  …       |

<subtitle>基于常量的类型构造器。</subtitle>

</mini-table>


```
let x: [u8; 4]; // "4字节的数组"
let y: [f32; 16]; // "16个浮点数的数组"

// `MyArray` 是一个类型构造器，需要具体的类型 `T` 和
// 具体的 usize `N` 来构造特定的类型。
struct MyArray<T, const N: usize> {
    data: [T; N],
}
```

</description>
</generics-section>


<!-- Section -->
<!-- <generics-section >
<header>Generics in Types</header>
<description>

</description>
</generics-section> -->




<!-- Section -->
<generics-section >
<header>约束（简单） &mdash; <code>where T: X</code></header>
<description>

<mini-zoo class="zoo">
    <person>🧔</person>
    <entry>
        <type class="generic dotted"><code>Num&lt;T&gt;</code></type>
    </entry>
    <narrow-entry>
        <code style="text-align:center; width: 100%;">→</code>
    </narrow-entry>
    <person>🎅</person>
    <entry>
        <type class="composed"><code>Num&lt;u8&gt;</code></type>
    </entry>
    <entry>
        <type class="composed"><code>Num&lt;f32&gt;</code></type>
    </entry>
    <entry>
        <type class="composed"><code>Num&lt;Cmplx&gt;</code></type>
    </entry>
    <narrow-entry>
        <code style="text-align:center; width: 50px;">&nbsp;</code>
    </narrow-entry>
    <entry class="">
        <type class="primitive"><code>u8</code></type>
        <trait-impl>⌾ <code>Absolute</code></trait-impl>
        <trait-impl>⌾ <code>Dim</code></trait-impl>
        <trait-impl>⌾ <code>Mul</code></trait-impl>
    </entry>
    <entry class="grayed">
        <type class="composed"><code>Port</code></type>
        <trait-impl>⌾ <code>Clone</code></trait-impl>
        <trait-impl>⌾ <code>ShowHex</code></trait-impl>
    </entry>
</mini-zoo>

- 如果 `T` 可以是任何类型，我们如何对这样的 `Num<T>` *进行推理*（编写代码）？
- 参数**约束**：
    - 限制允许的类型（**trait 约束**）或值（**常量约束** {{ todo() }}），
    - 我们现在可以利用这些限制！
- Trait 约束就像“成员资格检查”：

<mini-table>

<div style="display: inline-block;">

```
// 类型只能为某个 `T` 构造，如果该
// T 是 `Absolute` 成员列表的一部分。
struct Num<T> where T: Absolute {
    …
}

```

</div>


<mini-table style="width: 200px; display:inline-block;">

<table>
    <thead>
        <tr style=""><th>Absolute Trait</th></tr>
        <tr class="subheader"><th><code>Self</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>u8</code></td></tr>
        <tr><td><code>u16</code></td></tr>
        <tr><td><code>…</code></td></tr>
    </tbody>
</table>

</mini-table>
</mini-table>


<!--
// 常量 `N` 必须是 `usize`
struct Arrayf32<const N: usize> {
    data: [f32; N],
} -->

<footnotes>

我们在这里为结构体添加约束。实际上，最好在各自的 impl 块中添加约束，详见本节后面。

</footnotes>

<!-- > Note to self, is `const N: usize` a "const bound"? It seemingly acts as one, limiting the choice of values for N (albeit to specific types only). -->

</description>
</generics-section>


<!-- Section -->
<generics-section>
<header>约束（复合） &mdash; <code>where T: X + Y</code></header>
<description>

<mini-zoo class="zoo">
    <entry class="grayed">
        <type class="primitive"><code>u8</code></type>
        <trait-impl>⌾ <code>Absolute</code></trait-impl>
        <trait-impl>⌾ <code>Dim</code></trait-impl>
        <trait-impl>⌾ <code>Mul</code></trait-impl>
    </entry>
    <entry class="grayed">
        <type class="primitive"><code>f32</code></type>
        <trait-impl>⌾ <code>Absolute</code></trait-impl>
        <trait-impl>⌾ <code>Mul</code></trait-impl>
    </entry>
    <entry class="grayed">
        <type class="primitive"><code>char</code></type>
    </entry>
    <entry>
        <type class="composed"><code>Cmplx</code></type>
        <trait-impl>⌾ <code>Absolute</code></trait-impl>
        <trait-impl>⌾ <code>Dim</code></trait-impl>
        <trait-impl>⌾ <code>Mul</code></trait-impl>
        <trait-impl>⌾ <code>DirName</code></trait-impl>
        <trait-impl>⌾ <code>TwoD</code></trait-impl>
    </entry>
    <entry class="grayed">
        <type class="composed"><code>Car</code></type>
        <trait-impl>⌾ <code>DirName</code></trait-impl>
    </entry>
</mini-zoo>



```
struct S<T>
where
    T: Absolute + Dim + Mul + DirName + TwoD
{ … }
```

- 长的 trait 约束可能看起来很吓人。
- 实际上，每个 `+ X` 的添加只是缩小了合格类型的范围。

</description>
</generics-section>



<!-- Section -->
<generics-section>
<header>实现族 &mdash; <code>impl&lt;&gt;</code></header>
<description>

{{ tablesep() }}

当我们写：
```
impl<T> S<T> where T: Absolute + Dim + Mul {
    fn f(&self, x: T) { … };
}
```
它可以被读作：
- 这是任何类型 `T` 的实现配方（`impl <T>` 部分），
- 其中<sup>*</sup>该类型必须是 `Absolute + Dim + Mul` trait 的成员，
- 你可以为类型族 `S<>` 添加一个实现块，
- 包含方法……

你可以将这样的 `impl<T> … {}` 代码视为**抽象地实现了一个行为族**。{{ ref(page="items/implementations.html#generic-implementations") }} 最值得注意的是，它们允许第三方透明地物化实现，类似于类型构造器物化类型的方式：

```
// 如果编译器遇到这个，它会
// - 检查 `0` 和 `x` 是否满足 `T` 的成员资格要求
// - 创建两个新版本的 `f`，一个用于 `char`，另一个用于 `u32`。
// - 基于提供的“族实现”
s.f(0_u32);
s.f('x');
```


</description>
</generics-section>


<!-- Section -->
<generics-section>
<header>毯式实现 &mdash; <code>impl&lt;T&gt X for T { … }</code></header>
<description>

{{ tablesep() }}

也可以编写“族实现”，以便它们将 trait 应用于多种类型：

```
// 如果类型已经实现了 ToHex，则也为任何类型实现 Serialize
impl<T> Serialize for T where T: ToHex { … }
```

这些被称为**毯式实现 (blanket implementations)**。

<mini-table>

<mini-table style="width: 200px; display:inline-block;">

<table>
    <thead>
        <tr style=""><th>ToHex</th></tr>
        <tr class="subheader"><th><code>Self</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>Port</code></td></tr>
        <tr><td><code>Device</code></td></tr>
        <tr><td><code>…</code></td></tr>
    </tbody>
</table>

</mini-table>

<div style="display: inline-block; width: 100px;">

→  左表中的任何内容，都可能根据以下配方（`impl`）添加到右表中 →

</div>

<mini-table style="width: 200px; display:inline-block;">

<table>
    <thead>
        <tr style=""><th>Serialize Trait</th></tr>
        <tr class="subheader"><th><code>Self</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>u8</code></td></tr>
        <tr><td><code>Port</code></td></tr>
        <tr><td><code>…</code></td></tr>
    </tbody>
</table>

</mini-table>

</mini-table>


如果外部类型实现了另一个接口，它们可以是为外部类型提供模块化功能的好方法。

</description>
</generics-section>


</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-types-3" name="tab-group-types">
<label for="tab-types-3"><b>高级概念</b>{{ esoteric() }}</label>
<panel><div>


<!-- Section -->
<!-- <generics-section >
<header>Pseudo-Specialization</header>
<description>

</description>
</generics-section> -->




<!-- Section -->
<generics-section>
<header>Trait 参数 &mdash; <code>Trait&lt;In&gt; { type Out; } </code></header>
<description>

{{ tablesep() }}

注意有些 trait 可以“附加”多次，而另一些只能附加一次吗？

<mini-zoo class="zoo">
    <entry style="left:300px; top: 25px;">
        <type class="composed"><code>Port</code></type>
        <trait-impl class="">⌾ <code>From&lt;u8&gt;</code></trait-impl>
        <trait-impl class="">⌾ <code>From&lt;u16&gt;</code></trait-impl>
    </entry>
    <entry style="left:400px; top: 25px;">
        <type class="composed"><code>Port</code></type>
        <trait-impl class="">⌾ <code>Deref</code></trait-impl>
        <associated-type class="grayed"><code>type u8;</code></associated-type>
    </entry>
</mini-zoo>

<!--
<mini-zoo class="zoo">
    <entry>
        <trait-impl class="">⌾ <code>A&lt;T&gt;</code></trait-impl>
    </entry>
    <narrow-entry>
        <code style="text-align:center; width: 100%;">→</code>
    </narrow-entry>
    <entry>
        <trait-impl class="">⌾ <code>A&lt;u8&gt;</code></trait-impl>
    </entry>
    <entry>
        <trait-impl class="">⌾ <code>A&lt;f32&gt;</code></trait-impl>
    </entry>
    <entry>
        <trait-impl class="">⌾ <code>A&lt;str&gt;</code></trait-impl>
    </entry>
</mini-zoo>

<br>

<mini-zoo class="zoo">
    <entry>
        <trait-impl class="">⌾ <code>B</code></trait-impl>
        <associated-type class=""><code>type T;</code></associated-type>
    </entry>
    <narrow-entry>
        <code style="text-align:center; width: 100%;">→</code>
    </narrow-entry>
    <entry>
        <trait-impl class="">⌾ <code>B</code></trait-impl>
        <associated-type class=""><code>T = u8;</code></associated-type>
    </entry>
</mini-zoo> -->

<br>

{{ tablesep() }}

为什么会这样？

- Trait 本身可以对两种**参数**进行泛型化：
    - `trait From<I> {}`
    - `trait Deref { type O; }`
- 还记得我们说过 trait 是类型的“成员列表”并称该列表为 `Self` 吗？
- 事实证明，参数 `I`（表示**输入**）和 `O`（表示**输出**）只是该 trait 列表的更多*列*：

```
impl From<u8> for u16 {}
impl From<u16> for u32 {}
impl Deref for Port { type O = u8; }
impl Deref for String { type O = str; }
```


<mini-table>

<mini-table style="width: 200px; display:inline-block;">

<table>
    <thead>
        <tr style=""><th colspan="2">From</th></tr>
        <tr class="subheader"><th><code>Self</code></th><th><code>I</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>u16</code></td><td><code>u8</code></td></tr>
        <tr><td><code>u32</code></td><td><code>u16</code></td></tr>
        <tr><td colspan="2"><code>…</code></td></tr>
    </tbody>
</table>

</mini-table>


<mini-table style="width: 200px; display:inline-block;">

<table>
    <thead>
        <tr style=""><th colspan="2">Deref</th></tr>
        <tr class="subheader"><th><code>Self</code></th><th><code>O</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>Port</code></td><td><code>u8</code></td></tr>
        <tr><td><code>String</code></td><td><code>str</code></td></tr>
        <tr><td colspan="2"><code>…</code></td></tr>
    </tbody>
</table>

</mini-table>

<subtitle>输入和输出参数。</subtitle>

</mini-table>


这里的关键是，
- **任何输出 `O` 参数必须由输入参数 `I` 唯一确定**，
- （与关系 `X Y` 表示函数的方式相同），
- `Self` 算作一个输入。

一个更复杂的例子：

```
trait Complex<I1, I2> {
    type O1;
    type O2;
}
```

- 这创建了一个名为 `Complex` 的类型关系，
- 有 3 个输入（`Self` 总是其中之一）和 2 个输出，并且它持有 `(Self, I1, I2) => (O1, O2)`

<mini-table>

<table>
    <thead>
        <tr style=""><th colspan="5">Complex</th></tr>
        <tr class="subheader"><th><code>Self [I]</code></th><th><code>I1</code></th><th><code>I2</code></th><th><code>O1</code></th><th><code>O2</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>Player</code></td><td><code>u8</code></td><td><code>char</code></td><td><code>f32</code></td><td><code>f32</code></td></tr>
        <tr><td><code>EvilMonster</code></td><td><code>u16</code></td><td><code>str</code></td><td><code>u8</code></td><td><code>u8</code></td></tr>
        <tr><td><code>EvilMonster</code></td><td><code>u16</code></td><td><code>String</code></td><td><code>u8</code></td><td><code>u8</code></td></tr>
        <tr><td><code>NiceMonster</code></td><td><code>u16</code></td><td><code>String</code></td><td><code>u8</code></td><td><code>u8</code></td></tr>
        <tr><td><code>NiceMonster</code><sup>{{ bad() }}</sup></td><td><code>u16</code></td><td><code>String</code></td><td><code>u8</code></td><td><code>u16</code></td></tr>
    </tbody>
</table>

<subtitle>各种 trait 实现。最后一个是无效的，因为 `(NiceMonster, u16, String)` 已经<br> 唯一确定了输出。</subtitle>

</mini-table>

</description>
</generics-section>



<!-- Section -->
<generics-section>
<header>Trait 编写注意事项（抽象）</header>
<description>

<mini-zoo class="zoo">
    <person>👩‍🦰</person>
    <entry>
        <trait-impl class="dotted">⌾ <code>A&lt;I&gt;</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="margin-left: 10px;">
    <person>🧔</person>
    <entry>
        <type class="composed"><code>Car</code></type>
    </entry>
</mini-zoo>


<mini-zoo class="zoo" style="margin-left: 10px;">
    <person>👩‍🦰</person> / <person>🧔</person>
    <entry>
        <type class="composed"><code>Car</code></type>
        <trait-impl class="dotted">⌾ <code>A&lt;I&gt;</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="margin-left: 10px;">
    <person>🎅</person>
    <entry>
        <code>car.a(0_u8)</code>
        <code>car.a(0_f32)</code>
    </entry>
</mini-zoo>

<br>

<mini-zoo class="zoo">
    <person>👩‍🦰</person>
    <entry>
        <trait-impl class="">⌾ <code>B</code></trait-impl>
        <associated-type class=""><code>type O;</code></associated-type>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="margin-left: 10px;">
    <person>🧔</person>
    <entry>
        <type class="composed"><code>Car</code></type>
    </entry>
</mini-zoo>


<mini-zoo class="zoo" style="margin-left: 10px;">
    <person>👩‍🦰</person> / <person>🧔</person>
    <entry>
        <type class="composed"><code>Car</code></type>
        <trait-impl class="">⌾ <code>B</code></trait-impl>
        <associated-type class=""><code>T = u8;</code></associated-type>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="margin-left: 10px;">
    <person>🎅</person>
    <entry>
        <code>car.b(0_u8)</code>
        <code style="text-decoration: line-through;">car.b(0_f32)</code>
    </entry>
</mini-zoo>

- 参数的选择（输入与输出）也决定了谁可以添加成员：
    - `I` 参数允许将“实现族”转发给用户（Santa），
    - `O` 参数必须由 trait 实现者（Alice 或 Bob）确定。

```
trait A<I> { }
trait B { type O; }

// 实现者将 (X, u32) 添加到 A。
impl A<u32> for X { }

// 实现者将族实现 (X, …) 添加到 A，用户可以物化。
impl<T> A<T> for Y { }

// 实现者必须决定将哪个具体的条目 (X, O) 添加到 B。
impl B for X { type O = u32; }
```



<mini-table>

<mini-table style="width: 200px; display:inline-block;">

<table>
    <thead>
        <tr style=""><th colspan="2">A</th></tr>
        <tr class="subheader"><th><code>Self</code></th><th><code>I</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>X</code></td><td><code>u32</code></td></tr>
        <tr><td><code>Y</code></td><td><code>…</code></td></tr>
    </tbody>
</table>

<subtitle>Santa 可以通过提供自己的类型 `T` 来添加更多成员。</subtitle>

</mini-table>


<mini-table style="width: 200px; display:inline-block;">

<table>
    <thead>
        <tr style=""><th colspan="2">B</th></tr>
        <tr class="subheader"><th><code>Self</code></th><th><code>O</code></th></tr>
    </thead>
    <tbody>
        <tr><td><code>Player</code></td><td><code>String</code></td></tr>
        <tr><td><code>X</code></td><td><code>u32</code></td></tr>
    </tbody>
</table>

<subtitle>对于给定的输入集（此处为 `Self`），实现者必须预先选择 `O`。</subtitle>

</mini-table>

</mini-table>


</description>
</generics-section>


<!-- Section -->
<generics-section id="trait-authoring-examples">
<header>Trait 编写注意事项（示例）</header>
<description>

<mini-zoo class="zoo">
    <entry>
        <trait-impl class="">⌾ <code>Query</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <narrow-entry>
        <code style="text-align:center; width: 100%;">vs.</code>
    </narrow-entry>
</mini-zoo>

<mini-zoo class="zoo">
    <entry>
        <trait-impl class="dotted">⌾ <code>Query&lt;I&gt;</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <narrow-entry>
        <code style="text-align:center; width: 100%;">vs.</code>
    </narrow-entry>
</mini-zoo>

<mini-zoo class="zoo">
    <entry>
        <trait-impl class="">⌾ <code>Query</code></trait-impl>
        <associated-type class=""><code>type O;</code></associated-type>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <narrow-entry>
        <code style="text-align:center; width: 100%;">vs.</code>
    </narrow-entry>
</mini-zoo>

<mini-zoo class="zoo">
    <entry>
        <trait-impl class="dotted">⌾ <code>Query&lt;I&gt;</code></trait-impl>
        <associated-type class=""><code>type O;</code></associated-type>
    </entry>
</mini-zoo>



{{ tablesep() }}

参数的选择与 trait 需要满足的目的有关。

<hr>


**无额外参数**

```
trait Query {
    fn search(&self, needle: &str);
}

impl Query for PostgreSQL { … }
impl Query for Sled { … }

postgres.search("SELECT …");
```

<mini-zoo class="zoo">
    <person>👩‍🦰</person>
    <entry>
        <trait-impl class="">⌾ <code>Query</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <narrow-entry>
        <code style="text-align:center; width: 100%;">→</code>
    </narrow-entry>
</mini-zoo>

<mini-zoo class="zoo">
    <person>🧔</person>
    <entry>
        <type class="composed"><code>PostgreSQL</code></type>
        <trait-impl class="">⌾ <code>Query</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <entry>
        <type class="composed"><code>Sled</code></type>
        <trait-impl class="">⌾ <code>Query</code></trait-impl>
    </entry>
</mini-zoo>

{{ tablesep() }}

Trait 作者假设：
- 实现者和用户都不需要自定义 API。

{{ tablesep() }}

<hr>

**输入参数**

```
trait Query<I> {
    fn search(&self, needle: I);
}

impl Query<&str> for PostgreSQL { … }
impl Query<String> for PostgreSQL { … }
impl<T> Query<T> for Sled where T: ToU8Slice { … }

postgres.search("SELECT …");
postgres.search(input.to_string());
sled.search(file);
```

<mini-zoo class="zoo">
    <person>👩‍🦰</person>
    <entry>
        <trait-impl class="dotted">⌾ <code>Query&lt;I&gt;</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <narrow-entry>
        <code style="text-align:center; width: 100%;">→</code>
    </narrow-entry>
</mini-zoo>

<mini-zoo class="zoo">
    <person>🧔</person>
    <entry>
        <type class="composed"><code>PostgreSQL</code></type>
        <trait-impl class="">⌾ <code>Query&lt;&str&gt;</code></trait-impl>
        <trait-impl class="">⌾ <code>Query&lt;String&gt;</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <entry>
        <type class="composed"><code>Sled</code></type>
        <trait-impl class="dotted">⌾ <code>Query&lt;T&gt;</code></trait-impl>
        <note><span style="margin-left: 10px; display: inline-block; transform: rotate(90deg); font-size: 100%">↲</span> where <code>T</code> is <code>ToU8Slice</code>.</note>
    </entry>
</mini-zoo>


{{ tablesep() }}

Trait 作者假设：
- 实现者会为同一个 `Self` 类型以多种方式自定义 API，
- 用户可能希望能够决定哪些 `I` 类型应该可以具有该行为。

{{ tablesep() }}


<hr>


**输出参数**

```
trait Query {
    type O;
    fn search(&self, needle: Self::O);
}

impl Query for PostgreSQL { type O = String; …}
impl Query for Sled { type O = Vec<u8>; … }

postgres.search("SELECT …".to_string());
sled.search(vec![0, 1, 2, 4]);
```

<mini-zoo class="zoo">
    <person>👩‍🦰</person>
    <entry>
        <trait-impl class="">⌾ <code>Query</code></trait-impl>
        <associated-type class=""><code>type O;</code></associated-type>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <narrow-entry>
        <code style="text-align:center; width: 100%;">→</code>
    </narrow-entry>
</mini-zoo>

<mini-zoo class="zoo">
    <person>🧔</person>
    <entry>
        <type class="composed"><code>PostgreSQL</code></type>
        <trait-impl class="">⌾ <code>Query</code></trait-impl>
        <associated-type class=""><code>O = String;</code></associated-type>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <entry>
        <type class="composed"><code>Sled</code></type>
        <trait-impl class="">⌾ <code>Query</code></trait-impl>
        <associated-type class=""><code>O = Vec&lt;u8&gt;;</code></associated-type>
    </entry>
</mini-zoo>


{{ tablesep() }}

Trait 作者假设：
- 实现者会为 `Self` 类型自定义 API（但只有一种方式），
- 用户不需要，或者不应该有能力影响特定 `Self` 的自定义。

> 如你所见，术语**输入**或**输出**并**不**（必然）与 `I` 或 `O` 是否是实际函数的输入或输出有关！

{{ tablesep() }}

<hr>

**多个输入和输出参数**

```
trait Query<I> {
    type O;
    fn search(&self, needle: I) -> Self::O;
}

impl Query<&str> for PostgreSQL { type O = String; … }
impl Query<CString> for PostgreSQL { type O = CString; … }
impl<T> Query<T> for Sled where T: ToU8Slice { type O = Vec<u8>; … }

postgres.search("SELECT …").to_uppercase();
sled.search(&[1, 2, 3, 4]).pop();
```

<mini-zoo class="zoo">
    <person>👩‍🦰</person>
    <entry>
        <trait-impl class="dotted">⌾ <code>Query&lt;I&gt;</code></trait-impl>
        <associated-type class=""><code>type O;</code></associated-type>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <narrow-entry>
        <code style="text-align:center; width: 100%;">→</code>
    </narrow-entry>
</mini-zoo>

<mini-zoo class="zoo">
    <person>🧔</person>
    <entry>
        <type class="composed"><code>PostgreSQL</code></type>
        <trait-impl class="">⌾ <code>Query&lt;&str&gt;</code></trait-impl>
        <associated-type class=""><code>O = String;</code></associated-type>
        <trait-impl class="">⌾ <code>Query&lt;CString&gt;</code></trait-impl>
        <associated-type class=""><code>O = CString;</code></associated-type>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <entry>
        <type class="composed"><code>Sled</code></type>
        <trait-impl class="dotted">⌾ <code>Query&lt;T&gt;</code></trait-impl>
        <associated-type class=""><code>O = Vec&lt;u8&gt;;</code></associated-type>
        <note><span style="margin-left: 10px; display: inline-block; transform: rotate(90deg); font-size: 100%">↲</span> where <code>T</code> is <code>ToU8Slice</code>.</note>
    </entry>
</mini-zoo>


{{ tablesep() }}

与上述示例类似，特别是 trait 作者假设：
- 用户可能希望能够决定哪些 `I` 类型应该具有该能力，
- 对于给定的输入，实现者应该确定产生的输出类型。


</description>
</generics-section>



<!-- Section -->
<generics-section>
<header>动态/零大小类型</header>
<description>

<mini-zoo class="zoo" style="">
    <entry>
        <type class="composed"><code>MostTypes</code></type>
        <trait-impl>⌾ <code>Sized</code></trait-impl>
        <note>普通类型。</note>
    </entry>
</mini-zoo>

<mini-zoo class="zoo">
    <narrow-entry style="width: 60px;">
        <code style="text-align:center; width: 100%;">vs.</code>
    </narrow-entry>
</mini-zoo>

<mini-zoo class="zoo" style="">
    <entry>
        <type class="zero"><code>Z</code></type>
        <trait-impl>⌾ <code>Sized</code></trait-impl>
        <note>零大小。</note>
    </entry>
</mini-zoo>


<mini-zoo class="zoo">
    <narrow-entry style="width: 60px;">
        <code style="text-align:center; width: 100%;">vs.</code>
    </narrow-entry>
</mini-zoo>

<mini-zoo class="zoo" style="">
    <entry>
        <type class="primitive"><code>str</code></type>
        <trait-impl class="grayed">⌾ <code style="text-decoration: line-through">Sized</code></trait-impl>
        <note>动态大小。</note>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="">
    <entry>
        <type class="primitive"><code>[u8]</code></type>
        <trait-impl class="grayed">⌾ <code style="text-decoration: line-through">Sized</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="">
    <entry>
        <type class="primitive"><code>dyn Trait</code></type>
        <trait-impl class="grayed">⌾ <code style="text-decoration: line-through">Sized</code></trait-impl>
    </entry>
</mini-zoo>

<mini-zoo class="zoo" style="">
    <entry>
        <type class="primitive"><code>…</code></type>
        <trait-impl class="grayed">⌾ <code style="text-decoration: line-through">Sized</code></trait-impl>
    </entry>
</mini-zoo>


- 如果在编译时知道类型 `T` 占用的字节数，则 `T` 是 **`Sized`** {{ std(page="std/marker/trait.Sized.html") }}，`u8` 和 `&[u8]` 是，`[u8]` 不是。
- `Sized` 意味着 `impl Sized for T {}` 成立。这是自动发生的，不能由用户实现。
- 不是 `Sized` 的类型称为**动态大小类型** {{ book(page="ch19-04-advanced-types.html#dynamically-sized-types-and-the-sized-trait") }} {{ nom(page="exotic-sizes.html#dynamically-sized-types-dsts") }}  {{ ref(page="dynamically-sized-types.html#dynamically-sized-types") }} (DSTs)，有时也称为**unsized**。
- 没有数据的类型称为**零大小类型** {{ nom(page="exotic-sizes.html#zero-sized-types-zsts") }} (ZSTs)，不占用空间。

<div class="color-header sized cheats">

| 示例                            | 解释                                                                                                   |
| ------------------------------- | ------------------------------------------------------------------------------------------------------ |
| `struct A { x: u8 }`            | 类型 `A` 是 sized 的，即 `impl Sized for A` 成立，这是一个“常规”类型。                                 |
| `struct B { x: [u8] }`          | 由于 `[u8]` 是 DST，`B` 进而成为 DST，即不 `impl Sized`。                                              |
| `struct C<T> { x: T }`          | 类型参数**有**隐式的 `T: Sized` 约束，例如 `C<A>` 有效，`C<B>` 无效。                                  |
| `struct D<T: ?Sized> { x: T }`  | 使用 **`?Sized`** {{ ref(page="trait-bounds.html#sized") }} 允许选择退出该约束，即 `D<B>` 也是有效的。 |
| `struct E;`                     | 类型 `E` 是零大小的（也是 sized 的），不会消耗内存。                                                   |
| `trait F { fn f(&self); }`      | Trait **没有**隐式的 `Sized` 约束，即 `impl F for B {}` 是有效的。                                     |
| {{ tab() }} `trait F: Sized {}` | 然而，Trait 可以通过父 trait {{ above(target="#functions-behavior") }} 选择加入 `Sized`。              |
| `trait G { fn g(self); }`       | 对于 `Self` 类的参数，DST `impl` 可能仍然失败，因为参数不能放在栈上。                                  |

</div>


</description>
</generics-section>


<!-- Section -->
<generics-section>
<header><code>?Sized</code></header>
<description>


<mini-zoo class="zoo">
    <entry>
        <type class="generic dotted"><code>S&lt;T&gt;</code></type>
    </entry>
    <narrow-entry>
        <code style="text-align:center; width: 100%;">→</code>
    </narrow-entry>
    <entry>
        <type class="composed"><code>S&lt;u8&gt;</code></type>
    </entry>
    <entry>
        <type class="composed"><code>S&lt;char&gt;</code></type>
    </entry>
    <entry>
        <type class="composed grayed"><code>S&lt;str&gt;</code></type>
    </entry>
</mini-zoo>

```
struct S<T> { … }
```

- `T` 可以是任何具体类型。
- 然而，存在一个不可见的默认约束 `T: Sized`，所以 `S<str>` 开箱即用是不可行的。
- 相反，我们必须添加 `T : ?Sized` 来选择退出该约束：

<mini-zoo class="zoo">
    <entry>
        <type class="generic dotted"><code>S&lt;T&gt;</code></type>
    </entry>
    <narrow-entry>
        <code style="text-align:center; width: 100%;">→</code>
    </narrow-entry>
    <entry>
        <type class="composed"><code>S&lt;u8&gt;</code></type>
    </entry>
    <entry>
        <type class="composed"><code>S&lt;char&gt;</code></type>
    </entry>
    <entry>
        <type class="composed"><code>S&lt;str&gt;</code></type>
    </entry>
</mini-zoo>

```
struct S<T> where T: ?Sized { … }
```



</description>
</generics-section>


<!-- Section -->
<generics-section>
<header>泛型与生命周期 &mdash; <code>&lt;'a&gt;</code></header>
<description>

<mini-zoo class="zoo">
    <entry>
        <type class="generic dotted"><code>S&lt;'a&gt;</code></type>
    </entry>
    <entry>
        <type class="generic dotted"><code>&'a f32</code></type>
    </entry>
    <entry>
        <type class="generic dotted"><code>&'a mut u8</code></type>
    </entry>
</mini-zoo>

- 生命周期<sup>*</sup>充当类型参数：
    - 用户必须提供一个具体的 `'a` 来实例化类型（编译器会在方法内部提供帮助），
    - `S<'p>` 和 `S<'q>` 是不同的类型，就像 `Vec<f32>` 和 `Vec<u8>` 一样
    - 这意味着你不能简单地将 `S<'a>` 类型的值赋给期望 `S<'b>` 的变量（例外：生命周期的子类型关系，即 `'a` 超过 `'b`）。


<mini-zoo class="zoo">
    <entry>
        <type class="generic dotted"><code>S&lt;'a&gt;</code></type>
    </entry>
    <narrow-entry>
        <code style="text-align:center; width: 100%;">→</code>
    </narrow-entry>
    <entry>
        <type class="composed"><code>S&lt;'auto&gt;</code></type>
    </entry>
    <entry>
        <type class="composed"><code>S&lt;'static&gt;</code></type>
    </entry>
</mini-zoo>


- `'static` 是生命周期*种类*中唯一全局可用的类型。

```
// `'a 在这里是自由参数（用户可以传递任何特定的生命周期）
struct S<'a> {
    x: &'a u32
}

// 在非泛型代码中，'static 是我们唯一可以显式放入的命名生命周期。
let a: S<'static>;

// 或者，在非泛型代码中，我们（通常必须）省略 'a'，让 Rust 自动
// 确定 'a' 的正确值。
let b: S;
```

<footnotes>

<sup>*</sup> 存在细微差别，例如，你可以创建一个类型 `u32` 的显式实例 `0`，但除了 `'static` 之外，你不能真正创建一个生命周期，例如“第 80-100 行”，编译器会为你做这件事。{{ link(url="https://medium.com/nearprotocol/understanding-rust-lifetimes-e813bcd405fa" )}}

</footnotes>

</description>
</generics-section>


<!-- Section -->
<!-- <generics-section>
<header>Types of types: kinds</header>
<description>

Rust does not support higher-kinded types or even mention kinds, but knowing a
bit of theory can shed some light on how generics work. Note that the following
uses Rust-like syntax for explanations, but is not actually valid Rust.

- Values have types, e.g. `true` has type `bool`, written `true: bool`.
- Types have _kinds_, e.g. `bool` has kind `*`, also written `bool: *`. (`*` is
  pronounced _star_ or, sometimes a bit confusingly, _type_.)
- (Kinds have _sorts_, which is beyond scope here. Type theories ran out of
  English synonyms for _type_ afterwards, but luckily value/type/kind is enough
  for most type systems anyway.)

Rust conceptually uses three kinds: `*`, `kind1 -> kind2` (type constructors),
and `lifetime`.

- All values have a type of kind `*`.
- The opposite is not true: there are types of kind `*` that have no values,
  e.g. `!` (the empty type).
- Type constructors such as `Vec` take a type of kind `*`, e.g. `bool`, to a
  new type of kind `*`, in this case `Vec<bool>`. We can say `Vec: * -> *`.
- `lifetime` is the kind of lifetimes, e.g. `'static: lifetime`. Since
  `lifetime` is not `*`, types of kind `lifetime` cannot have values. They can
  however be used as parameters to create types. For example in

  ```rust
  struct S<'a> {
      x: &'a u32
  }
  ```

  the kind of `S` is `lifetime -> *`.
- Note that `Vec<'static>` is a kind error, because `Vec: * -> *`, not
  `lifetime -> *`.

</description>
</generics-section> -->


<!-- Section -->
<!-- <generics-section >
<header>Another <code>?X</code></header>
<description>

- `Sized` is trait, automatically implemented **and** automatically used as default bound
- Could there (ever) be another trait `T` so that:
    - `S<T>` means `S<T> where T: Sized + X` by default and
    - you'd have to opt out with `S<T> where T: ?X` ?
- Issue:
    - Any `S<T>` written today does not know `X`, so can't opt into supporting it
    - If `X` were introduced and not implemented for any existing type, `S<T>` would stop working on that type

</description>
</generics-section> -->


<!-- Section -->
<!-- <generics-section >
<header>GAT {{ experimental() }}</header>
<description>


</description>
</generics-section> -->



<!-- Section -->
<!-- <generics-section >
<header>(Co-/Contra-) Variance </header>
<description>


</description>
</generics-section>
 -->

<!-- Section -->
<!-- <generics-section id="zoo_todo">
<header>Todo</header>
<description>


</description>
</generics-section>
 -->


</div></panel></tab>

</tabs>

<footnotes>

点击展开示例。

</footnotes>




## 外部类型与 Trait {#foreign-types-and-traits}

你的 crate 和上游 crate 中类型和 trait 的视觉概览。

<!-- 在小屏幕上创建一个水平滚动区域以保持布局 -->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 750px;">


<zoo class="zoo">

<!-- REGION -->
<region style="height: 310px;">
<!-- Primitives -->
<group style="left:6%; width: 200px;">
    <entry style="left:100px; top: 10%;">
        <type class="primitive"><code>u8</code></type>
    </entry>
    <entry style="left:20px; top: 32%;">
        <type class="primitive"><code>u16</code></type>
    </entry>
    <entry style="left:30px; top: 20%;">
        <type class="primitive"><code>f32</code></type>
    </entry>
    <entry style="left:0px; top: 7%;">
        <type class="primitive"><code>bool</code></type>
    </entry>
    <entry style="left:120px; top: 32%;">
        <type class="primitive"><code>char</code></type>
    </entry>
    <label style="left:8px; top: 43%;">原始类型</label>
</group>
<!-- Composed -->
<group style="left:50%; width: 350px;">
    <entry style="left:110px; top: 60px;">
        <type class="composed"><code>File</code></type>
    </entry>
    <entry style="left:180px; top: 34%;">
        <type class="composed"><code>String</code></type>
    </entry>
    <entry style="left:230px; top: 13%;">
        <type class="composed"><code>Builder</code></type>
    </entry>
    <label style="left:150px; top: 43%;">复合类型</label>
</group>
<!-- Type constructors -->
<group style="left: 30px; top:53%; width: 200px;">
    <!-- Group -->
    <entry style="left:50px; top: 8%;">
        <type class="composed"><code>Vec&lt;T&gt;</code></type>
    </entry>
    <entry style="left:45px; top: 9%;">
        <type class="composed"><code>Vec&lt;T&gt;</code></type>
    </entry>
    <entry style="left:40px; top: 10%;">
        <type class="generic dotted"><code>Vec&lt;T&gt;</code></type>
    </entry>
    <!-- Group -->
    <entry style="left:170px; top: 2%;">
        <type class="primitive"><code>&'a T</code></type>
    </entry>
    <entry style="left:165px; top: 3%;">
        <type class="primitive"><code>&'a T</code></type>
    </entry>
    <entry style="left:160px; top: 4%;">
        <type class="generic dotted"><code>&'a T</code></type>
    </entry>
    <!-- Group -->
    <entry style="left:140px; top: 18%;">
        <type class="primitive"><code>&mut 'a T</code></type>
    </entry>
    <entry style="left:135px; top: 19%;">
        <type class="primitive"><code>&mut 'a T</code></type>
    </entry>
    <entry style="left:130px; top: 20%;">
        <type class="generic dotted"><code>&mut 'a T</code></type>
    </entry>
    <!-- Group -->
    <entry style="left:40px; top: 28%;">
        <type class="primitive"><code>[T; n]</code></type>
    </entry>
    <entry style="left:35px; top: 29%;">
        <type class="primitive"><code>[T; n]</code></type>
    </entry>
    <entry style="left:30px; top: 30%;">
        <type class="generic dotted"><code>[T; n]</code></type>
    </entry>
    <label style="left:80px; top: 40%;">类型构造器</label>
</group>
<!-- Functrions -->
<group style="left: 50%; top:53%; width: 200px;">
    <!-- Group -->
    <entry style="left:10px; top: 8%;">
        <function class=""><code>Vec&lt;T&gt;</code></function>
    </entry>
    <entry style="left:5px; top: 9%;">
        <function class=""><code>Vec&lt;T&gt;</code></function>
    </entry>
    <entry style="left:0px; top: 10%;">
        <function class="dotted"><code>f&lt;T&gt;() {}</code></function>
    </entry>
    <!-- Group -->
    <entry style="left:20px; top: 24%;">
        <function><code>drop() {}</code></function>
    </entry>
    <label style="left:10px; top: 40%;">函数</label>
</group>
<!-- Unsized -->
<!-- <group style="left: 50%; top:53%;">
    <entry style="left:30%; top: 10%;">
        <type class="unsized"><code>str</code></type>
    </entry>
    <entry style="left:35%; top: 20%;">
        <type class="unsized"><code>[u8]</code></type>
    </entry>
    <entry style="left:28%; top: 30%;">
        <type class="unsized"><code>dyn Trait</code></type>
    </entry>
    <label style="left:30%; top: 40%;">Unsized Types</label>
</group> -->
<!-- Macros -->
<group class="grayed" style="left: 80%; top:53%; width: 140px;">
    <entry style="left:5px; top: 15%;">
        <macro><code>PI</code></macro>
    </entry>
    <entry style="left:0px; top: 28%;">
        <macro><code>dbg!</code></macro>
    </entry>
    <label style="left:20px; top: 40%;">其他</label>
</group>
<!-- Traits -->
<group style="left:36%; width: 30px;">
    <entry style="left:20px; top: 20px;">
        <trait-impl>⌾ <code>Copy</code></trait-impl>
    </entry>
    <entry style="left:60px; top: 90px;">
        <trait-impl class="">⌾ <code>Deref</code></trait-impl>
        <associated-type class=""><code>type Tgt;</code></associated-type>
    </entry>
    <entry style="left:90px; top: 50px;">
        <trait-impl class="">⌾ <code>From&lt;T&gt;</code></trait-impl>
    </entry>
    <entry style="left:85px; top: 55px;">
        <trait-impl class="">⌾ <code>From&lt;T&gt;</code></trait-impl>
    </entry>
    <entry style="left:80px; top: 60px;">
        <trait-impl class="dotted">⌾ <code>From&lt;T&gt;</code></trait-impl>
    </entry>
    <label style="left:60px; top: 43%;">Trait</label>
</group>
</region>
<region-label>在上游 crate 中定义的项。</region-label>

<!-- REGION -->
<region class="your-crate" style="height: 190px;">
<!-- traits -->
<group style="left:5px; width: 200px;">
    <entry style="left:10px; top: 25px;">
        <trait-impl class="">⌾ <code>Serialize</code></trait-impl>
    </entry>
    <entry style="left:30px; top: 65px;">
        <trait-impl class="">⌾ <code>Transport</code></trait-impl>
    </entry>
    <entry style="left:15px; top: 105px;">
        <trait-impl class="">⌾ <code>ShowHex</code></trait-impl>
    </entry>
    <!-- <label style="left:60px; top: 165px">Traits</label> -->
</group>
<!-- types -->
<group style="left:150px; width: 200px;">
    <entry style="left:0px; top: 25px;">
        <type class="composed"><code>Device</code></type>
        <trait-impl class="grayed">⌾ <code>From&lt;u8&gt;</code></trait-impl>
        <!-- <trait-impl class="grayed">⌾ <code>Deref</code></trait-impl>
        <associated-type class="grayed"><code>type Thing;</code></associated-type> -->
        <note>为本地类型实现外部 trait。</note>
    </entry>
    <entry style="left:100px; top: 25px;">
        <type class="grayed composed"><code>String</code></type>
        <trait-impl class="">⌾ <code>Serialize</code></trait-impl>
        <note>为外部类型实现本地 trait。</note>
    </entry>
    <entry style="left:200px; top: 25px;">
        <type class="composed grayed"><code>String</code></type>
        <trait-impl class="grayed">⌾ <code>From&lt;u8&gt;</code></trait-impl>
        <note>{{ bad() }} 非法，为外部类型实现外部 trait。</note>
    </entry>
    <entry style="left:200px; top: 110px;">
        <type class="composed grayed"><code>String</code></type>
        <trait-impl class="grayed">⌾ <code>From&lt;Port&gt;</code></trait-impl>
        <note>例外：如果使用的类型是本地的则合法。</note>
    </entry>
    <entry style="left:300px; top: 25px;">
        <type class="composed"><code>Port</code></type>
        <trait-impl class="">⌾ <code>From&lt;u8&gt;</code></trait-impl>
        <trait-impl class="">⌾ <code>From&lt;u16&gt;</code></trait-impl>
        <note>具有不同<b>输入</b>参数的 trait 的多个 impl。</note>
    </entry>
    <entry style="left:400px; top: 25px;">
        <type class="composed"><code>Container</code></type>
        <trait-impl class="">⌾ <code>Deref</code></trait-impl>
        <associated-type class="grayed"><code>Tgt = u8;</code></associated-type>
        <trait-impl class="">⌾ <code>Deref</code></trait-impl>
        <associated-type class="grayed"><code>Tgt = f32;</code></associated-type>
        <note>{{ bad() }} 具有不同<b>输出</b>参数的 trait 的非法 impl。</note>
    </entry>
    <entry style="left:510px; top: 15px;">
        <type class="composed"><code>T</code></type>
    </entry>
    <entry style="left:505px; top: 20px;">
        <type class="composed"><code>T</code></type>
    </entry>
    <entry style="left:500px; top: 25px;">
        <type class="generic dotted"><code>T</code></type>
        <trait-impl class="">⌾ <code>ShowHex</code></trait-impl>
        <note>为任何类型毯式实现 trait。</note>
    </entry>
</group>
</region>
<region-label>你的 crate。</region-label>

<!-- REGION -->
<!-- <region style="height: 90px;">
<group style="left:324px; width: 200px;">
    <entry style="left:20px; top: 30px;">
        <code>ccc.f();</code>
    </entry>
</group>
</region>
<region-label>Downstream crates.</region-label> -->

</zoo>

<footnotes>

trait 和类型的示例，以及你可以为哪些类型实现哪些 trait。

</footnotes>



<!-- End scrollable overflow-->
</div>
</div>




## 类型转换 {#type-conversions}

当你有了 `A`，如何得到 `B`？

<div class="color-header variance">

<tabs>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-variance-1" name="tab-variance" checked>
<label for="tab-variance-1"><b>简介</b></label>
<panel><div>

```
fn f(x: A) -> B {
    // 你如何从 A 得到 B？
}
```

| 方法                     | 解释                                                         |
| ------------------------ | ------------------------------------------------------------ |
| **恒等**                 | 简单情况，`B` **就是** `A`。                                 |
| **计算**                 | 通过**编写代码**转换数据来创建和操作 `B` 的实例。            |
| **转换 (Casts)**         | 在建议谨慎的情况下**按需**在类型之间转换。                   |
| **强制转换 (Coercions)** | 在*“弱化规则集”*内**自动**转换。<sup>1</sup>                 |
| **子类型化 (Subtyping)** | 在*“相同布局不同生命周期规则集”*内**自动**转换。<sup>1</sup> |

{{ tablesep() }}

<footnotes>

<sup>1</sup> 虽然两者都将 `A` 转换为 `B`，但**强制转换**通常链接到一个*不相关*的 `B`（一个“可以合理地期望有不同方法”的类型），
而**子类型化**链接到一个仅在生命周期上不同的 `B`。

</footnotes>

</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-variance-2" name="tab-variance">
<label for="tab-variance-2"><b>计算 (Traits)</b></label>
<panel><div>

```
fn f(x: A) -> B {
    x.into()
}
```

从 `A` 得到 `B` 的*常规*方法。一些 trait 提供了规范的、用户可计算的类型关系：

| Trait                      | 示例            | Trait 意味着…                                          |
| -------------------------- | --------------- | ------------------------------------------------------ |
| `impl From<A> for B {}`    | `a.into()`      | *显而易见*、总是有效的关系。                           |
| `impl TryFrom<A> for B {}` | `a.try_into()?` | *显而易见*、有时有效的关系。                           |
| `impl Deref for A {}`      | `*a`            | `A` 是携带 `B` 的智能指针；也启用强制转换。            |
| `impl AsRef<B> for A {}`   | `a.as_ref()`    | `A` 可以被*视为* `B`。                                 |
| `impl AsMut<B> for A {}`   | `a.as_mut()`    | `A` 可以被可变地视为 `B`。                             |
| `impl Borrow<B> for A {}`  | `a.borrow()`    | `A` 有一个借用的*等价物* `B`（在 `Eq` 等下行为相同）。 |
| `impl ToOwned for A { … }` | `a.to_owned()`  | `A` 有一个自有的等价物 `B`。                           |


<!--
<footnotes>

<sup>1</sup> Pretty much any function, like `is_signed(x)`, puts values of two types in a _specific_ relationship, especially if their _meaning_ is highly _overloaded_ (e.g., `true` in the `is_signed` relation is proxy for a different concept than `true` in an `is_odd` one). In contrast, the traits above (and type conversions in general) are mainly about unambiguous conversions across any possible meaning.

</footnotes>
 -->

</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-variance-3" name="tab-variance">
<label for="tab-variance-3"><b>转换 (Casts)</b></label>
<panel><div>

```
fn f(x: A) -> B {
    x as B
}
```

如果转换*相对明显*但**可能引起问题**，则**使用关键字 `as`** 转换类型。{{ nom(page="casts.html") }}


| A               | B          | 示例                        | 解释                                                           |
| --------------- | ---------- | --------------------------- | -------------------------------------------------------------- |
| `Pointer`       | `Pointer`  | `device_ptr as *const u8`   | 如果 `*A`, `*B` 是 `Sized`。                                   |
| `Pointer`       | `Integer`  | `device_ptr as usize`       |                                                                |
| `Integer`       | `Pointer`  | `my_usize as *const Device` |                                                                |
| `Number`        | `Number`   | `my_u8 as u16`              | 通常有令人惊讶的行为。{{ above(target="#numeric-types-ref") }} |
| `enum` (无字段) | `Integer`  | `E::A as u8`                |                                                                |
| `bool`          | `Integer`  | `true as u8`                |                                                                |
| `char`          | `Integer`  | `'A' as u8`                 |                                                                |
| `&[T; N]`       | `*const T` | `my_ref as *const u8`       |                                                                |
| `fn(…)`         | `Pointer`  | `f as *const u8`            | 如果 `Pointer` 是 `Sized`。                                    |
| `fn(…)`         | `Integer`  | `f as usize`                |                                                                |

{{ tablesep() }}

<footnote>

这里 `Pointer`、`Integer`、`Number` 只是为了简洁而使用，实际上意味着：
- `Pointer` 任何 `*const T` 或 `*mut T`；
- `Integer` 任何可数的 `u8` … `i128`；
- `Number` 任何 `Integer`、`f32`、`f64`。

</footnote>

> **个人观点** {{ opinionated() }} &mdash; 转换，尤其是 `Number - Number`，很容易出错。
> 如果你关心正确性，请考虑使用更明确的方法。

</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-variance-4" name="tab-variance">
<label for="tab-variance-4"><b>强制转换 (Coercions)</b></label>
<panel><div>

```
fn f(x: A) -> B {
    x
}
```

自动**弱化**类型 `A` 为 `B`；类型可以*实质上*<sup>1</sup>不同。{{ nom(page="coercions.html") }}


| A                                | B              | 解释                                                                                           |
| -------------------------------- | -------------- | ---------------------------------------------------------------------------------------------- |
| `&mut T`                         | `&T`           | **指针弱化**。                                                                                 |
| `&mut T`                         | `*mut T`       | -                                                                                              |
| `&T`                             | `*const T`     | -                                                                                              |
| `*mut T`                         | `*const T`     | -                                                                                              |
| `&T`                             | `&U`           | **解引用**，如果 `impl Deref<Target=U> for T`。                                                |
| `T`                              | `U`            | **去大小化 (Unsizing)**，如果 `impl CoerceUnsized<U> for T`。<sup>2</sup> {{ experimental() }} |
| `T`                              | `V`            | **传递性**，如果 `T` 强制转换为 `U` 且 `U` 强制转换为 `V`。                                    |
| <code>&vert;x&vert; x + x</code> | `fn(u8) -> u8` | **非捕获闭包**，转换为等效的 `fn` 指针。                                                       |

{{ tablesep() }}

<footnote>

<sup>1</sup> *实质上*意味着可以常规地期望强制转换结果 `B` 是一个*完全不同的类型*（即，具有完全不同的方法）而不是原始类型 `A`。

<sup>2</sup> 在上面的示例中不太适用，因为无大小类型不能放在栈上；可以想象 `f(x: &A) -> &B`。去大小化默认适用于：
- `[T; n]` 到 `[T]`
- `T` 到 `dyn Trait` 如果 `impl Trait for T {}`。
- `Foo<…, T, …>` 到 `Foo<…, U, …>` 在某些晦涩的{{ link(url="https://doc.rust-lang.org/nomicon/coercions.html") }}情况下。

</footnote>


</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-variance-5" name="tab-variance">
<label for="tab-variance-5"><b>子类型化</b>{{ esoteric() }}</label>
<panel><div>

```
fn f(x: A) -> B {
    x
}
```

对于**仅在生命周期上不同**的类型，自动将 `A` 转换为 `B` {{ nom(page="subtyping.html") }} - 子类型化**示例**：


| A<sup>(子类型)</sup>  | B<sup>(超类型)</sup> | 解释                                                                |
| --------------------- | -------------------- | ------------------------------------------------------------------- |
| `&'static u8`         | `&'a u8`             | 有效，*永久*指针也是*瞬时*指针。                                    |
| `&'a u8`              | `&'static u8`        | {{ bad() }} 无效，瞬时不应是永久。                                  |
| `&'a &'b u8`          | `&'a &'b u8`         | 有效，相同的东西。**但现在事情变得有趣了。请继续阅读。**            |
| `&'a &'static u8`     | `&'a &'b u8`         | 有效，`&'static u8` 也是 `&'b u8`；在 `&` 内部是**协变**的。        |
| `&'a mut &'static u8` | `&'a mut &'b u8`     | {{ bad() }} 无效且令人惊讶；在 `&mut` 内部是**不变**的。            |
| `Box<&'static u8>`    | `Box<&'a u8>`        | 有效，带有永久的 `Box` 也是带有瞬时的 `Box`；协变的。               |
| `Box<&'a u8>`         | `Box<&'static u8>`   | {{ bad() }} 无效，带有瞬时的 `Box` 可能不是带有永久的。             |
| `Box<&'a mut u8>`     | `Box<&'a u8>`        | {{ bad() }} <sup>⚡</sup> 无效，见下表，`&mut u8` 从来*不是* `&u8`。 |
| `Cell<&'static u8>`   | `Cell<&'a u8>`       | {{ bad() }} 无效，`Cell` **从不**是其他东西；不变的。               |
| `fn(&'static u8)`     | `fn(&'a u8)`         | {{ bad() }} 如果 `fn` 需要永久，它可能会在瞬时上窒息；**逆变**的。  |
| `fn(&'a u8)`          | `fn(&'static u8)`    | 但吃瞬时的东西**可以是**(!)吃永久的东西。                           |
| `for<'r> fn(&'r u8)`  | `fn(&'a u8)`         | 高阶类型 `for<'r> fn(&'r u8)` 也是 `fn(&'a u8)`。                   |


{{ tablesep() }}

相比之下，这些**不是**{{ bad() }}子类型化的例子：

| A            | B        | 解释                                                                             |
| ------------ | -------- | -------------------------------------------------------------------------------- |
| `u16`        | `u8`     | {{ bad() }} **显然无效**；`u16` 永远不应自动成为 `u8`。                          |
| `u8`         | `u16`    | {{ bad() }} **设计上无效**；具有不同数据的类型即使*可以*，也永远不会是子类型。   |
| `&'a mut u8` | `&'a u8` | {{ bad() }} 特洛伊木马，不是子类型化；而是强制转换（仍然有效，但不是子类型化）。 |

{{ tablesep() }}

</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-variance-8" name="tab-variance">
<label for="tab-variance-8"><b>变性 (Variance)</b>{{ esoteric() }}</label>
<panel><div>

```
fn f(x: A) -> B {
    x
}
```

对于**仅在生命周期上不同**的类型，自动将 `A` 转换为 `B` {{ nom(page="subtyping.html") }} - 子类型化**变性规则**：

- 较长的生命周期 `'a` 超过较短的 `'b`，是 `'b` 的子类型。
- 这意味着 `'static` 是所有其他生命周期 `'a` 的子类型。
- 具有参数的类型（例如 `&'a T`）是否是彼此的子类型，使用以下变性表：

| 构造<sup>1</sup> | `'a` | `T`      | `U`  |
| ---------------- | ---- | -------- | ---- |
| `&'a T`          | 协变 | 协变     |      |
| `&'a mut T`      | 协变 | 不变     |      |
| `Box<T>`         |      | 协变     |      |
| `Cell<T>`        |      | 不变     |      |
| `fn(T) -> U`     |      | **逆**变 | 协变 |
| `*const T`       |      | 协变     |      |
| `*mut T`         |      | 不变     |      |

<footnotes>

**协变 (Covariant)** 意味着如果 `A` 是 `B` 的子类型，那么 `T[A]` 是 `T[B]` 的子类型。<br>
**逆变 (Contravariant)** 意味着如果 `A` 是 `B` 的子类型，那么 **`T[B]`** 是 `T[A]` 的子类型。<br>
**不变 (Invariant)** 意味着即使 `A` 是 `B` 的子类型，`T[A]` 和 `T[B]` 都不会是对方的子类型。<br>
<!-- <br> -->

<sup>1</sup> 像 `struct S<T> {}` 这样的复合类型通过其使用的字段获得变性，如果混合了多种变性，通常会变得不变。<br>

</footnotes>

> 💡 **换句话说**，“常规”类型永远不是彼此的子类型（例如，`u8` 不是 `u16` 的子类型），
> `Box<u32>` 也永远不会是任何东西的子类型或超类型。
> 然而，通常情况下，`Box<A>` *可以*是 `Box<B>` 的子类型（通过协变），如果 `A` 是
> `B` 的子类型，这只会在 `A` 和 `B` 是“仅在生命周期上不同的同一种类型”时发生，例如，`A` 是 `&'static u32`，`B` 是 `&'a u32`。

</div></panel></tab>

</tabs>

</div>


{{ tablesep() }}




---

# 编码指南


## 惯用的 Rust {#idiomatic-rust}

如果你习惯了 Java 或 C，请考虑这些。

<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px; ">
<div class="color-header number">


| 惯用法                    | 代码                                                                                                                                                          |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **用表达式思考**          | `y = if x { a } else { b };`                                                                                                                                  |
|                           | `y = loop { break 5 };`                                                                                                                                       |
|                           | `fn f() -> u32 { 0 }`                                                                                                                                         |
| **用迭代器思考**          | `(1..10).map(f).collect()`                                                                                                                                    |
|                           | <code>names.iter().filter(&vert;x&vert; x.starts_with("A"))</code>                                                                                            |
| **用 `?` 测试缺失**       | `y = try_something()?;`                                                                                                                                       |
|                           | `get_option()?.run()?`                                                                                                                                        |
| **使用强类型**            | `enum E { Invalid, Valid { … } }` 而不是 `ERROR_INVALID = -1`                                                                                                 |
|                           | `enum E { Visible, Hidden }` 而不是 `visible: bool`                                                                                                           |
|                           | `struct Charge(f32)` 而不是 `f32`                                                                                                                             |
| **非法状态：不可能**      | `my_lock.write().unwrap().guaranteed_at_compile_time_to_be_locked = 10;` <sup>1</sup>                                                                         |
|                           | <code>thread::scope(&vert;s&vert; { /* 线程的存活时间不能超过 scope() */ });</code>                                                                           |
| **避免*全局*状态**        | 在多个版本中被依赖会秘密地复制静态变量。{{ bad() }} {{ link(url="https://doc.rust-lang.org/cargo/reference/resolver.html#version-incompatibility-hazards") }} |
| **提供构建器 (Builders)** | `Car::new("Model T").hp(20).build();`                                                                                                                         |
| **使其为 Const**          | 在可能的情况下将函数标记为 `const`；在可行的情况下在 `const {}` 内运行代码。                                                                                  |
| **不要 Panic**            | Panic *不是*异常，它们表明进程应立即中止！                                                                                                                    |
|                           | 仅在编程错误时 panic；否则使用 `Option<T>`{{ std(page="std/option/enum.Option.html") }} 或 `Result<T,E>`{{ std(page="std/result/enum.Result.html") }}。       |
|                           | 如果是用户明确请求的，例如调用 `obtain()` 而不是 `try_obtain()`，panic 也可以。                                                                               |
|                           | 在 `const { NonZero::new(1).unwrap() }` 中，panic 会变成编译错误，也可以。                                                                                    |
| **适度使用泛型**          | 一个简单的 `<T: Bound>`（例如 `AsRef<Path>`）可以让你的 API 更易于使用。                                                                                      |
|                           | 复杂的约束使其难以理解。如有疑问，不要在*泛型*上发挥创意。                                                                                                    |
| **拆分实现**              | 像 `Point<T>` 这样的泛型可以为每个 `T` 有单独的 `impl` 以实现某种特化。                                                                                       |
|                           | `impl<T> Point<T> { /* 在这里添加通用方法 */ }`                                                                                                               |
|                           | `impl Point<f32> { /* 在这里添加只与 Point<f32> 相关的方法 */ }`                                                                                              |
| **Unsafe**                | 避免 `unsafe {}`，{{ below(target="#unsafe-unsound-undefined") }} 通常有更安全、更快的解决方案。                                                              |
| **实现 Trait**            | `#[derive(Debug, Copy, …)]` 以及在需要时自定义 `impl`。                                                                                                       |
| **工具链**                | 定期运行 [**clippy**](https://github.com/rust-lang/rust-clippy) 以显著提高你的代码质量。{{ hot() }}                                                           |
|                           | 用 [**rustfmt**](https://github.com/rust-lang/rustfmt) 格式化你的代码以保持一致性。{{ hot() }}                                                                |
|                           | 添加**单元测试**{{ book(page="ch11-01-writing-tests.html") }} (`#[test]`) 以确保你的代码能工作。                                                              |
|                           | 添加**文档测试**{{ book(page="ch14-02-publishing-to-crates-io.html") }} (` ``` my_api::f() ``` `) 以确保文档与代码匹配。                                      |
| **文档**                  | 用文档注释注解你的 API，这些注释会显示在 [**docs.rs**](https://docs.rs) 上。                                                                                  |
|                           | 不要忘记包含一个**摘要句**和**示例**标题。                                                                                                                    |
|                           | 如果适用：**Panics**, **Errors**, **Safety**, **Abort** 和 **Undefined Behavior**。                                                                           |


</div>
</div>
</div>

<footnotes>

<sup>1</sup> 在大多数情况下，你应该优先使用 `?` 而不是 `.unwrap()`。然而，在锁的情况下，返回的 [**`PoisonError`**](https://doc.rust-lang.org/stable/std/sync/struct.PoisonError.html) 表示另一个线程发生了 panic，所以 unwrap 它（从而传播 panic）通常是更好的主意。


</footnotes>

{{ tablesep() }}

> 🔥 我们**强烈**建议你也遵循
> [**API 指南**](https://rust-lang.github.io/api-guidelines/)（[**清单**](https://rust-lang.github.io/api-guidelines/checklist.html)）
> 用于任何共享项目！🔥


{{ tablesep() }}


## 性能提示 {#performance-tips}

在将微基准测试移植到 Rust 或进行性能分析后，“我的代码很慢”有时会出现。

<div class="color-header blue">

| 评级                                                               | 名称                                                                                                                                                 | 描述                                                                                                                     |
| ------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| {{ tbl_boost() }}{{ tbl_simple() }}                                | **Release 模式** {{ book(page="ch01-03-hello-cargo.html") }} {{ hot() }}                                                                             | 总是使用 `cargo build --release` 来获得巨大的速度提升。                                                                  |
| {{ noemoji1() }}{{ tbl_simple() }}{{ noemoji1() }}{{ tbl_risk() }} | **目标原生 CPU** {{ link(url="https://doc.rust-lang.org/rustc/codegen-options/index.html#target-cpu") }}                                             | 在 `config.toml` 中添加 `rustflags = ["-Ctarget-cpu=native"]`。{{ above(target = "#project-anatomy") }}                  |
| {{ noemoji1() }}{{ tbl_simple() }}{{ tbl_tradeoff() }}             | **代码生成单元** {{ link(url="https://doc.rust-lang.org/rustc/codegen-options/index.html#codegen-units") }}                                          | 代码生成单元 `1` 可能会产生更快的代码，但编译更慢。                                                                      |
| {{ noemoji1() }}{{ tbl_simple() }}                                 | **预留容量** {{ std(page="std/?search=with_capacity") }}                                                                                             | 预分配集合可以减少分配压力。                                                                                             |
| {{ noemoji1() }}{{ tbl_simple() }}                                 | **回收集合** {{ std(page="std/index.html?search=clear") }}                                                                                           | 调用 `x.clear()` 并重用 `x` 可以防止分配。                                                                               |
| {{ noemoji1() }}{{ tbl_simple() }}                                 | **追加到字符串** {{ std(page="std/macro.write.html") }}                                                                                              | 使用 `write!(&mut s, "{}")` 可以防止额外的分配。                                                                         |
| {{ noemoji1() }}{{ tbl_simple() }}{{ tbl_tradeoff() }}             | **全局分配器** {{ std(page="std/alloc/index.html#the-global_allocator-attribute") }}                                                                 | 在某些平台上，外部分配器（例如 **mimalloc** {{ link(url="https://crates.io/crates/mimalloc") }}）更快。                  |
|                                                                    | **Bump 分配** {{ link(url="https://docs.rs/bumpalo/latest/bumpalo/") }}                                                                              | 廉价地获取*临时的*动态内存，尤其是在热循环中。                                                                           |
|                                                                    | **批量 API**                                                                                                                                         | 设计 API 以一次处理多个相似的元素，例如切片。                                                                            |
| {{ noemoji2() }}{{ tbl_tradeoff() }}                               | **SoA** / **AoSoA** {{ link(url="https://web.archive.org/web/20240815193855/https://www.rustsim.org/blog/2020/03/23/simd-aosoa-in-nalgebra/") }}     | 除此之外，考虑*数组的结构体*（SoA）等。                                                                                  |
| {{ tbl_boost() }}{{ noemoji1() }}{{ tbl_tradeoff() }}              | **SIMD** {{ std(page="std/simd/index.html") }} {{ experimental() }}                                                                                  | 在（数学密集型）批量 API 内部使用 SIMD 可以提供 2x - 8x 的提升。                                                         |
|                                                                    | **减小数据大小**                                                                                                                                     | 小类型（例如 `u8` vs `u32`，niche {{ todo() }}）和数据具有更好的缓存利用率。                                             |
|                                                                    | **保持数据就近** {{ link(url="https://en.wikipedia.org/wiki/Data-oriented_design" ) }}                                                               | 将经常使用的数据存储在*附近*可以提高内存访问时间。                                                                       |
|                                                                    | **按大小传递** {{ link(url="https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#reason-45" ) }}                             | 小的（2-3 个字）结构体最好按值传递，大的按引用传递。                                                                     |
| {{ noemoji2() }}{{ tbl_tradeoff() }}                               | **Async-Await** {{ link( url = "https://rust-lang.github.io/async-book/01_getting_started/01_chapter.html") }}                                       | 如果*并行等待*发生得很多（例如，服务器 I/O），`async` 是个好主意。                                                       |
|                                                                    | **线程** {{ std(page="std/thread/index.html") }}                                                                                                     | 线程允许你一次在多个项上执行*并行工作*。                                                                                 |
| {{ tbl_boost() }}                                                  | ... **在应用程序中**                                                                                                                                 | 通常对应用程序有好处，因为更短的等待时间意味着更好的用户体验。                                                           |
| {{ noemoji2() }}{{ tbl_tradeoff() }}                               | ... **在库内部**                                                                                                                                     | 在库*内部*不透明地使用*线程*通常不是个好主意，可能过于固执己见。                                                         |
| {{ tbl_boost() }}{{ noemoji1() }}                                  | ... **对库调用者**                                                                                                                                   | 然而，允许*你的用户*并行处理*你*是个极好的主意。                                                                         |
| {{ noemoji2() }}{{ tbl_tradeoff() }}                               | **避免锁**                                                                                                                                           | 多线程代码中的锁会扼杀并行性。                                                                                           |
| {{ noemoji2() }}{{ tbl_tradeoff() }}                               | **避免原子操作**                                                                                                                                     | 不必要的原子操作（例如 `Arc` vs `Rc`）会影响其他内存访问。                                                               |
| {{ noemoji2() }}{{ tbl_tradeoff() }}                               | **避免伪共享** {{ link(url="https://en.wikipedia.org/wiki/False_sharing") }}                                                                         | 确保不同 CPU 读/写的数据至少相距 64 字节。{{ link(url="https://igoro.com/archive/gallery-of-processor-cache-effects/")}} |
| {{ tbl_boost() }}{{ tbl_simple() }}                                | **缓冲 I/O** {{ std(page="std/io/index.html#bufreader-and-bufwriter") }} {{ hot() }}                                                                 | 没有缓冲的原始 `File` I/O 效率极低。                                                                                     |
| {{ noemoji1() }}{{ tbl_simple() }}{{ noemoji1() }}{{ tbl_risk() }} | **更快的哈希器** {{ link(url="https://lib.rs/crates/seahash") }}                                                                                     | 默认的 `HashMap` {{ std(page="std/collections/struct.HashMap.html") }} 哈希器具有 DoS 攻击弹性但速度慢。                 |
| {{ noemoji1() }}{{ tbl_simple() }}{{ noemoji1() }}{{ tbl_risk() }} | **更快的 RNG**                                                                                                                                       | 如果你使用加密 RNG，考虑换成非加密的。                                                                                   |
| {{ noemoji2() }}{{ tbl_tradeoff() }}                               | **避免 Trait 对象** {{ link(url="https://stackoverflow.com/questions/28621980/what-are-the-actual-runtime-performance-costs-of-dynamic-dispatch") }} | T.O. 减小代码大小，但增加内存间接性。                                                                                    |
| {{ noemoji2() }}{{ tbl_tradeoff() }}                               | **延迟 Drop** {{ link(url="https://abrams.cc/rust-dropping-things-in-another-thread") }}                                                             | 在转储线程中 drop *重*对象可以释放当前线程。                                                                             |
| {{ noemoji1() }}{{ tbl_simple() }}{{ noemoji1() }}{{ tbl_risk() }} | **未经检查的 API**  {{ std(page="std/?search=unchecked") }}                                                                                          | 如果你 100% 自信，`unsafe { unchecked_ }` 会跳过检查。                                                                   |

</div>


<footnotes>

标记为 {{ tbl_boost() }} 的条目通常带来巨大的（> 2x）性能提升，{{ tbl_simple() }} 即使事后也很容易实现，{{ tbl_tradeoff() }} 可能有昂贵的副作用（例如，内存，复杂性），{{ tbl_risk() }} 有特殊风险（例如，安全，正确性）。

</footnotes>

{{ tablesep() }}

> **性能分析提示** {{ opinionated() }}
>
> 性能分析器是识别代码中热点的不可或缺的工具。为了获得最佳体验，请将以下内容添加到你的 <code class="ignore-auto language-bash">Cargo.toml</code>：
> ```cargo
> [profile.release]
> debug = true
> ```
> 然后执行 `cargo build --release` 并用 [**Superluminal**](https://superluminal.eu/rust/) (Windows) 或 [**Instruments**](https://en.wikipedia.org/wiki/Instruments_%28software%29) (macOS) 运行结果。
> 话虽如此，有许多性能机会是性能分析器找不到的，但需要*设计进去*。

{{ tablesep() }}



## Async-Await 101 {#async-await-101}

如果你熟悉 C# 或 TypeScript 中的 async / await，这里有一些需要记住的事情：


<tabs class="color-header orange">

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-async-1" name="tab-async" checked>
<label for="tab-async-1"><b>基础</b></label>
<panel><div>



| 构造                               | 解释                                                                                                          |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| `async`                            | 任何声明为 `async` 的东西总是返回一个 `impl Future<Output=_>`。{{ std(page="std/future/trait.Future.html") }} |
| {{ tab() }} `async fn f() {}`      | 函数 `f` 返回一个 `impl Future<Output=()>`。                                                                  |
| {{ tab() }} `async fn f() -> S {}` | 函数 `f` 返回一个 `impl Future<Output=S>`。                                                                   |
| {{ tab() }} `async { x }`          | 将 `{ x }` 转换为一个 `impl Future<Output=X>`。                                                               |
| `let sm = f();   `                 | 调用 `async` 的 `f()` **不会**执行 `f`，而是产生一个状态机 `sm`。{{ note(note="1") }} {{ note(note="2") }}    |
| {{ tab() }} `sm = async { g() };`  | 同样，**不会**执行 `{ g() }` 块；而是产生一个状态机。                                                         |
| `runtime.block_on(sm);`            | 在 `async {}` 外部，调度 `sm` 实际运行。会执行 `g()`。{{ note(note="3") }} {{ note(note="4") }}               |
| `sm.await`                         | 在 `async {}` 内部，运行 `sm` 直到完成。如果 `sm` 未就绪，则让给运行时。                                      |



<footnotes>

<sup>1</sup> 技术上讲，`async` 将随后的代码转换为一个匿名的、编译器生成的状态机类型；`f()` 实例化该机器。<br>
<sup>2</sup> 状态机总是 `impl Future`，可能还 `impl Send` 等，取决于在 `async` 内部使用的类型。<br>
<sup>3</sup> 状态机由工作线程直接通过运行时调用 `Future::poll()` 驱动，或间接通过父 `.await` 驱动。<br>
<sup>4</sup> Rust 不带运行时，需要外部 crate，例如 [tokio](https://crates.io/crates/tokio)。另外，[futures crate](https://github.com/rust-lang-nursery/futures-rs) 中有更多辅助工具。

</footnotes>



</div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-async-2" name="tab-async">
<label for="tab-async-2"><b>执行流</b></label>
<panel><div>


在每个 `x.await` 处，状态机将控制权传递给下属状态机 `x`。在某个时刻，通过 `.await` 调用的低级状态机可能尚未就绪。在这种情况下，工作线程会一直返回到运行时，以便它可以驱动另一个 Future。一段时间后，运行时：
- **可能**会恢复执行。通常会，除非 `sm` / `Future` 被 drop。
- **可能**会用前一个工作线程**或另一个**工作线程恢复（取决于运行时）。

在 `async` 块内部编写的代码的简化图：


<!-- 在小屏幕上创建一个水平滚动区域以保持布局 -->
<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

```
       consecutive_code();           consecutive_code();           consecutive_code();
开始 --------------------> x.await --------------------> y.await --------------------> 就绪
// ^                          ^     ^                               Future<Output=X> 就绪 -^
// 通过运行时或外部 .await 调用   |     |
//                                 |     这可能会在另一个线程上恢复（下一个最好的可用线程），
//                                 |     或者如果 Future 在等待时被 drop，则根本不会恢复。
//                                 |
//                                 执行 `x`。如果就绪：继续执行；否则，将此线程
//                                 返回给运行时。
```

</div>
</div>

</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-async-3" name="tab-async">
<label for="tab-async-3"><b>注意事项</b> {{ bad() }} </label>
<panel><div>


在 `async` 结构中编写代码时的一些注意事项：

<div class="color-header orange">


| 构造 {{ note(note="1") }}   | 解释                                                                                                                                                                           |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `sleep_or_block();`         | 绝对糟糕 {{ bad() }}，永远不要暂停当前线程，会堵塞执行器。                                                                                                                     |
| `set_TL(a); x.await; TL();` | 绝对糟糕 {{ bad() }}，`await` 可能会从其他线程返回，[线程局部存储](https://doc.rust-lang.org/std/macro.thread_local.html)无效。                                                |
| `s.no(); x.await; s.go();`  | 可能糟糕 {{ bad() }}，如果 `Future` 在等待时被 drop，`await` 将[不会返回](http://www.randomhacks.net/2019/03/09/in-nightly-rust-await-may-never-return/)。{{ note(note="2") }} |
| `Rc::new(); x.await; rc();` | 非 `Send` 类型会阻止 `impl Future` 成为 `Send`；兼容性较差。                                                                                                                   |

</div>

<footnotes>

<sup>1</sup> 这里我们假设 `s` 是任何可能暂时处于无效状态的非局部变量；
`TL` 是任何线程局部存储，并且包含该代码的 `async {}` 的编写
没有假设执行器的具体细节。<br/>
<sup>2</sup> 由于在 `Future` 被 drop 时，[Drop](https://doc.rust-lang.org/std/ops/trait.Drop.html) 在任何情况下都会运行，如果必须在 `.await` 点跨越时将其置于不良状态，请考虑使用 drop guard 来清理/修复应用程序状态。

</footnotes>

</div></panel></tab>

<!-- end tabs -->
</tabs>


{{ tablesep() }}



## API 中的闭包 {#closures-in-apis}

存在一个子 trait 关系 `Fn` : `FnMut` : `FnOnce`。这意味着实现 `Fn` {{ std(page="std/ops/trait.Fn.html") }} 的闭包也实现了 `FnMut` 和 `FnOnce`。同样，实现 `FnMut` {{ std(page="std/ops/trait.FnMut.html") }} 的闭包也实现了 `FnOnce`。{{ std(page="std/ops/trait.FnOnce.html") }}

从调用点的角度来看，这意味着：

<div class="color-header green">

| 签名                      | 函数 `g` 可以调用 &hellip; | 函数 `g` 接受 &hellip;  |
| ------------------------- | -------------------------- | ----------------------- |
| `g<F: FnOnce()>(f: F)`    | &hellip; `f()` 最多一次。  | `Fn`, `FnMut`, `FnOnce` |
| `g<F: FnMut()>(mut f: F)` | &hellip; `f()` 多次。      | `Fn`, `FnMut`           |
| `g<F: Fn()>(f: F)`        | &hellip; `f()` 多次。      | `Fn`                    |

</div>

<footnotes>

注意，作为函数**要求**一个 `Fn` 闭包
对调用者来说是最严格的；但作为调用者**拥有**一个 `Fn`
闭包与任何函数都是最兼容的。

</footnotes>



{{ tablesep() }}

从定义闭包的人的角度来看：

<div class="color-header green">

| 闭包                                     | 实现<sup>*</sup>        | 注释                                  |
| ---------------------------------------- | ----------------------- | ------------------------------------- |
| <code> &vert;&vert; { moved_s; } </code> | `FnOnce`                | 调用者必须放弃 `moved_s` 的所有权。   |
| <code> &vert;&vert; { &mut s; } </code>  | `FnOnce`, `FnMut`       | 允许 `g()` 改变调用者的局部状态 `s`。 |
| <code> &vert;&vert; { &s; } </code>      | `FnOnce`, `FnMut`, `Fn` | 不能改变状态；但可以共享和重用 `s`。  |

</div>

<div class="footnotes">

<sup>*</sup> Rust [更喜欢通过引用捕获](https://doc.rust-lang.org/stable/reference/expressions/closure-expr.html)，
（从调用者的角度来看，这会产生最“兼容”的 `Fn` 闭包），但可以通过
`move || {}` 语法强制其通过复制或移动来捕获环境。

</div>

{{ tablesep() }}

这带来了以下优点和缺点：

<div class="color-header green">

| 要求        | 优点                                                  | 缺点                                                                   |
| ----------- | ----------------------------------------------------- | ---------------------------------------------------------------------- |
| `F: FnOnce` | <span class="good">作为调用者很容易满足。</span>      | <span class="bad">只能使用一次，`g()` 最多只能调用 `f()` 一次。</span> |
| `F: FnMut`  | <span class="good">允许 `g()` 改变调用者状态。</span> | <span class="bad">调用者在 `g()` 期间不能重用捕获。</span>             |
| `F: Fn`     | <span class="good">可以同时存在多个。</span>          | <span class="bad">对调用者来说最难产生。</span>                        |

</div>


{{ tablesep() }}



<!-- ## Macro Hygiene -->
<!-- {{ tablesep() }} -->





## Unsafe、Unsound、Undefined {#unsafe-unsound-undefined}

Unsafe 导致 Unsound。Unsound 导致 Undefined。Undefined 导致原力的黑暗面。



<tabs>

<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-unsafe-0" name="tab-unsafe" checked>
<label for="tab-unsafe-0"><b>安全代码</b></label>
<panel><div>


**安全代码 (Safe Code)**

- _Safe_ 在 Rust 中有狭义的含义，大致是“*内在*地防止未定义行为 (UB)”。
- 内在意味着语言不允许你用*它自己*来导致 UB。
- 让飞机坠毁或删除你的数据库不是 UB，因此从 Rust 的角度来看是“安全的”。
- 写入 `/proc/[pid]/mem` 来自我修改你的代码也是“安全的”，由此产生的 UB 不是*内在*引起的。

<!-- 换句话说，_safe_ 只意味着语言将产生二进制代码，当合理调用时，其执行方式与源代码中编写的方式一致。 -->

<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

```rust
let y = x + x;  // 安全的 Rust 只保证这段代码的执行与
print(y);       // '规范'（说来话长……）一致。它不保证 y 是 2x
                // （X::add 可能实现得很糟糕）也不保证 y 被打印（Y::fmt 可能 panic）。
```
</div></div>


</div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-unsafe-1" name="tab-unsafe">
<label for="tab-unsafe-1"><b>不安全代码</b></label>
<panel><div>


**不安全代码 (Unsafe Code)**

- 标记为 `unsafe` 的代码具有特殊权限，例如，可以解引用裸指针，或调用其他 `unsafe` 函数。
- 随之而来的是作者*必须*向编译器遵守的特殊**承诺**，编译器*会*相信你。
- `unsafe` 代码本身并不坏，但很危险，对于 FFI 或奇异的数据结构是必需的。

<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

```rust
// `x` 必须总是指向无竞争、有效、对齐、初始化的 u8 内存。
unsafe fn unsafe_f(x: *mut u8) {
    my_native_lib(x);
}
```
</div></div></div></panel></tab>


<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-unsafe-2" name="tab-unsafe" >
<label for="tab-unsafe-2"><b>未定义行为</b></label>
<panel><div>


**未定义行为 (Undefined Behavior, UB)**
- 如前所述，`unsafe` 代码意味着对编译器有[特殊承诺](https://doc.rust-lang.org/stable/reference/behavior-considered-undefined.html)（否则就不需要 `unsafe`）。
- 未能遵守任何承诺都会使编译器产生错误的代码，执行这些代码会导致 UB。
- 触发未定义行为后，*任何事情*都可能发生。阴险的是，其影响可能是 1) 微妙的，2) 在远离违规地点的地方显现，或 3) 仅在特定条件下可见。
- 一个看似*能工作*的程序（包括任何数量的单元测试）并不能证明 UB 代码不会随时失效。
- 带有 UB 的代码客观上是危险的、无效的，并且永远不应该存在。

<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">


```rust
if maybe_true() {
    let r: &u8 = unsafe { &*ptr::null() };   // 一旦这行运行，整个应用程序都是未定义的。即使
} else {                                     // 这行看似没做什么，应用程序现在也可能运行
    println!("the spanish inquisition");     // 两个路径，破坏数据库，或做任何其他事情。
}
```
</div></div></div></panel></tab>



<!-- NEW TAB -->
<tab>
<input type="radio" id="tab-unsafe-3" name="tab-unsafe" >
<label for="tab-unsafe-3"><b>不健全代码</b></label>
<panel><div>


**不健全代码 (Unsound Code)**
- 任何*安全*的 Rust 代码，如果可能（即使只是理论上）对任何用户输入产生 UB，那么它总是**不健全的 (unsound)**。
- 同样，`unsafe` 代码如果通过违反上述承诺而自行调用 UB，也是不健全的。
- 不健全的代码是稳定性和安全性的风险，并违反了许多 Rust 用户的基本假设。

<div style="overflow:auto;">
<div style="min-width: 100%; width: 650px;">

```rust
fn unsound_ref<T>(x: &T) -> &u128 {      // 对用户来说，签名看起来是安全的。碰巧
    unsafe { mem::transmute(x) }         // 如果用 &u128 调用就没问题，但对于几乎
}                                        // 其他所有东西都是 UB。
```

</div></div></div></panel></tab>

</tabs>

{{ tablesep() }}

>
> **负责任地使用 Unsafe** {{ opinionated() }}
>
> - 除非绝对必要，否则不要使用 `unsafe`。
> - 遵循 [Nomicon](https://doc.rust-lang.org/nightly/nomicon/)、[Unsafe 指南](https://rust-lang.github.io/unsafe-code-guidelines/)，**始终**遵守**所有**安全规则，并**绝不**调用 [UB](https://doc.rust-lang.org/stable/reference/behavior-considered-undefined.html)。
> - 最小化 `unsafe` 的使用，并将其封装在易于审查的小而健全的模块中。
> - 永远不要创建不健全的抽象；如果你不能正确地封装 `unsafe`，就不要做。
> - 每个 `unsafe` 单元都应附有纯文本的理由，概述其安全性。


{{ tablesep() }}



## 对抗性代码 {{ esoteric() }} {#adversarial-code}

*对抗性*代码是*安全*的第三方代码，它能编译但*不遵循* API 的期望，并可能干扰你自己的（安全）保证。


<div class="color-header redred">


| 你编写                      | 用户代码可能会…                              |
| --------------------------- | -------------------------------------------- |
| `fn g<F: Fn()>(f: F) { … }` | 意外地 panic。                               |
| `struct S<X: T> { … }`      | 糟糕地实现 `T`，例如，滥用 `Deref` 等。      |
| `macro_rules! m { … }`      | 做以上所有事情；调用点可能有*奇怪的*作用域。 |

{{ tablesep() }}

| 风险模式                                             | 描述                                                                  |
| ---------------------------------------------------- | --------------------------------------------------------------------- |
| `#[repr(packed)]`                                    | 紧凑对齐可能会使引用 `&s.x` 无效。                                    |
| `impl std::… for S {}`                               | 任何 trait `impl`，尤其是 `std::ops`，都可能被破坏。特别是…           |
| {{ tab() }} `impl Deref for S {}`                    | 可能随机地 `Deref`，例如 `s.x != s.x`，或 panic。                     |
| {{ tab() }} `impl PartialEq for S {}`                | 可能违反相等性规则；panic。                                           |
| {{ tab() }} `impl Eq for S {}`                       | 可能导致 `s != s`；panic；在 `HashMap` 等中不得使用 `s`。             |
| {{ tab() }} `impl Hash for S {}`                     | 可能违反哈希规则；panic；在 `HashMap` 等中不得使用 `s`。              |
| {{ tab() }} `impl Ord for S {}`                      | 可能违反排序规则；panic；在 `BTreeMap` 等中不得使用 `s`。             |
| {{ tab() }} `impl Index for S {}`                    | 可能随机索引，例如 `s[x] != s[x]`；panic。                            |
| {{ tab() }} `impl Drop for S {}`                     | 可能在作用域 `{} `结束时，或在赋值 `s = new_s` 期间运行代码或 panic。 |
| `panic!()`                                           | 用户代码可能在*任何*时候 panic，导致中止或展开。                      |
| <code>catch_unwind(&vert;&vert; s.f(panicky))</code> | 另外，调用者可能会强制观察 `s` 的破坏状态。                           |
| `let … = f();`                                       | 变量名会影响 `Drop` 执行的顺序。<sup>1</sup> {{ bad() }}              |

<footnotes>

<sup>1</sup> 值得注意的是，当你将变量从 <code>_x</code> 重命名为 <code>&lowbar;</code> 时，你也会改变 Drop 的行为，因为你改变了语义。名为 <code>_x</code> 的变量将在其作用域结束时执行 <code>Drop::drop()</code>，而名为 <code>&lowbar;</code> 的变量可以在“表面”赋值时立即执行（“表面”是因为名为 <code>&lowbar;</code> 的绑定意味着**通配符**{{ ref(page="patterns.html#wildcard-pattern")}}*丢弃这个*，这会尽快发生，通常是立即）！

</footnotes>

{{ tablesep() }}

</div>


> **影响**
>
> - 如果安全性依赖于类型在大多数（`std::`）trait 方面的合作，那么泛型代码**不可能是安全的**。
> - 如果需要类型合作，你必须使用 `unsafe` trait（可能自己实现）。
> - 你必须考虑在意想不到的地方（例如，重新赋值、作用域结束）随机执行代码。
> - 在最坏情况的 panic 之后，你可能仍然是可观察的。
>
> 作为推论，*安全*但致命的代码（例如 `airplane_speed<T>()`）可能也应该遵循这些指南。


{{ tablesep() }}


## API 稳定性 {#api-stability}

更新 API 时，这些更改可能会破坏客户端代码。{{ rfc(page="1105-api-evolution.html") }} 主要更改（🔴）**肯定会破坏**，而次要更改（🟡）**可能会破坏**：

<div class="color-header api-stability">


{{ tablesep() }}

| Crates                                               |
| ---------------------------------------------------- |
| 🔴 使一个之前在*稳定版*上编译的 crate 需要*nightly*。 |
| 🔴 移除 Cargo 特性。                                  |
| 🟡 更改现有的 Cargo 特性。                            |

{{ tablesep() }}


| 模块                                                              |
| ----------------------------------------------------------------- |
| 🔴 重命名/移动/移除任何公共项。                                    |
| 🟡 添加新的公共项，因为这可能会破坏做 `use your_crate::*` 的代码。 |

{{ tablesep() }}

| 结构体                                                                               |
| ------------------------------------------------------------------------------------ |
| 🔴 当所有当前字段都为公共时，添加私有字段。                                           |
| 🔴 当没有私有字段存在时，添加公共字段。                                               |
| 🟡 当至少有一个私有字段已经存在时（更改前后），添加或移除私有字段。                   |
| 🟡 从一个所有字段都为私有的元组结构体（至少有一个字段）变为一个普通结构体，反之亦然。 |

{{ tablesep() }}

| 枚举                                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------------------------- |
| 🔴 添加新的变体；可以通过早期使用 `#[non_exhaustive]` {{ ref(page="attributes/type_system.html#the-non_exhaustive-attribute") }} 来缓解 |
| 🔴 向一个变体添加新的字段。                                                                                                             |


{{ tablesep() }}

| Trait                                                              |
| ------------------------------------------------------------------ |
| 🔴 添加一个非默认项，会破坏所有现有的 `impl T for S {}`。           |
| 🔴 对项签名的任何非平凡更改，会影响消费者或实现者。                 |
| 🔴 实现任何“基础”trait，因为*不*实现一个基础 trait 已经是一个承诺。 |
| 🟡 添加一个默认项；可能会与其他现有 trait 引起分发歧义。            |
| 🟡 添加一个默认类型参数。                                           |
| 🟡 实现任何非基础 trait；也可能引起分发歧义。                       |

{{ tablesep() }}

| 固有实现                                                                      |
| ----------------------------------------------------------------------------- |
| 🟡 添加任何固有项；可能会导致客户端优先选择它而不是 trait 函数并产生编译错误。 |

{{ tablesep() }}

| 类型定义中的签名                            |
| ------------------------------------------- |
| 🔴 收紧约束（例如，`<T>` 到 `<T: Clone>`）。 |
| 🟡 放松约束。                                |
| 🟡 添加默认类型参数。                        |
| 🟡 泛化为泛型。                              |

| 函数中的签名             |
| ------------------------ |
| 🔴 添加/移除参数。        |
| 🟡 引入一个新的类型参数。 |
| 🟡 泛化为泛型。           |


{{ tablesep() }}

| 行为更改                                                         |
| ---------------------------------------------------------------- |
| 🔴 / 🟡 *更改语义可能不会导致编译器错误，但可能会使客户端做错事。* |


</div>


{{ tablesep() }}


<!-- ## Authoring Quality Crates

> **Note** <sup>💬</sup> &mdash; This chapter is mildly **subjective**. That said, it tries to be observational with respect to successful Rust crates (i.e., crates with most downloads should check most of these boxes).


<div class="color-header quality_crate">

#### Code Patterns

| What                                           | Why    |
| ---------------------------------------------- | ------ |
| ☐ Write idiomatic code, follow API guides.     |        |
| ☐ Regularly use `clippy`, `fmt`                |        |
| ☐ Err on the side of `#[deny]`, not `#[allow]` | asdasd |


#### Infrastructure

| What                                             | Why  |
| ------------------------------------------------ | ---- |
| ☐ Minimize dependencies.                         | asds |
| ☐ Add optional deps. to essential `trait` crates | asds |
| ☐ Have unit & integration tests                  | asds |
| ☐ Have benchmarks                                | asds |


#### Site

| What                                              | Why  |
| ------------------------------------------------- | ---- |
| ☐ Feature **prominent** API example, screenshot … | asds |
| ☐ Have permissive license for libs.               | asds |

</div>

<footnotes>


</footnotes> -->


<!-- 打印时不要渲染此部分，它不会有帮助 -->
<noprint>

---

# 杂项


## 链接与服务 {#links-services}

<div class="color-header lavender">

<!-- Official Rust online "books" about Rust itself or major components (e.g., WebAssembly, Embedded, …).
     This is not a random link section. Resources below should be have official community
     involvement, be maintained, have +1k Github stars, and be 'substantial'. Given our own
     audience we generally favor compact resources targetting experienced programmers. -->

专业书籍，另请参见 [Rust 书籍小集](https://lborb.github.io/book/title-page.html)。

| 主题&nbsp;️📚                                                                                      | 描述                                             |
| ------------------------------------------------------------------------------------------------ | ------------------------------------------------ |
| [API 指南](https://rust-lang.github.io/api-guidelines/)                                          | 如何编写惯用且可重用的 Rust。                    |
| [异步编程](https://rust-lang.github.io/async-book/)  {{ experimental() }}                        | 解释 `async` 代码、`Futures` 等。                |
| [Cargo](https://doc.rust-lang.org/cargo/)                                                        | 如何使用 `cargo` 和编写 `Cargo.toml`。           |
| [命令行工具](https://rust-lang-nursery.github.io/cli-wg/)                                        | 关于创建命令行工具的信息。                       |
| [食谱](https://rust-lang-nursery.github.io/rust-cookbook/)                                       | 演示良好实践的简单示例集合。                     |
| [设计模式](https://rust-unofficial.github.io/patterns//)                                         | 惯用法、模式、反模式。                           |
| [版本指南](https://doc.rust-lang.org/nightly/edition-guide/)                                     | 使用 Rust 2015、Rust 2018 及更高版本。           |
| [嵌入式](https://docs.rust-embedded.org/book/intro/index.html)                                   | 使用嵌入式和 `#![no_std]` 设备。                 |
| [函数式编程术语](https://github.com/JasonShin/functional-programming-jargon.rs) {{ esoteric() }} | 用 Rust 解释的函数式编程术语集合。               |
| [Rustc 开发指南](https://rustc-dev-guide.rust-lang.org/index.html) {{ esoteric() }}              | 解释编译器内部如何工作。                         |
| [Rust 宏小书](https://veykril.github.io/tlborm/introduction.html)                                | 社区关于 Rust 宏的集体知识。                     |
| [性能](https://nnethercote.github.io/perf-book/)                                                 | 提高速度和内存使用的技术。                       |
| [RFCs](https://rust-lang.github.io/rfcs/) {{ esoteric() }}                                       | 查找已接受的 RFC 以及它们如何改变语言。          |
| [Rustdoc](https://doc.rust-lang.org/stable/rustdoc/)                                             | 关于如何自定义 `cargo doc` 和 `rustdoc` 的提示。 |
| [不安全代码指南](https://rust-lang.github.io/unsafe-code-guidelines/) {{ experimental() }}       | 关于编写 `unsafe` 代码的简明信息。               |
| [不稳定版](https://doc.rust-lang.org/unstable-book/index.html)  {{ esoteric() }}                 | 关于不稳定项的信息，例如 `#![feature(…)]`。      |

</div>


{{ tablesep() }}



全面的常见组件查找表。

<div class="color-header lavender">

<!-- Table-like sites, often auto-generated. -->
| 表格&nbsp;📋                                                                                         | 描述                                                                                             |
| --------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| [Rust Forge](https://forge.rust-lang.org/)                                                          | 列出发布火车和为编译器工作的人员的链接。                                                         |
| {{ tab() }} [支持的平台](https://doc.rust-lang.org/rustc/platform-support.html)                     | 所有支持的平台及其等级。                                                                         |
| {{ tab() }} [组件历史](https://rust-lang.github.io/rustup-components-history/) {{ experimental() }} | 检查一个平台的各种 Rust 工具的**nightly**状态。                                                  |
| [Clippy Lints](https://rust-lang.github.io/rust-clippy/master/)                                     | 你可能感兴趣的所有 [**clippy**](https://github.com/rust-lang/rust-clippy) lints。                |
| [Rustfmt 配置](https://rust-lang.github.io/rustfmt/)                                                | 你可以在 `.rustfmt.toml` 中使用的所有 [**rustfmt**](https://github.com/rust-lang/rustfmt) 选项。 |
</div>

{{ tablesep() }}


提供信息或工具的在线服务。

<div class="color-header lavender">

<!-- Other online web services related to Rust. As a heuristic, things here should
    be essential (or at least address a major concern as "best of class") and be
    a self-contained, user-facing web site. -->

| 服务&nbsp;⚙️                                                                                | 描述                                       |
| ------------------------------------------------------------------------------------------ | ------------------------------------------ |
| [Rust Playground](https://play.rust-lang.org/)                                             | 尝试和分享 Rust 代码片段。                 |
| [crates.io](https://crates.io/)                                                            | 所有 Rust 的第三方库。                     |
| [lib.rs](https://lib.rs/)                                                                  | 优质 Rust 库和应用程序的非官方概述。       |
| [blessed.rs](https://blessed.rs/) <a class="tooltip" title="Opinionated."><sup>💬</sup></a> | Rust 生态系统的非官方指南，更加固执己见。  |
| [std.rs](https://std.rs/)                                                                  | `std` 文档的快捷方式。                     |
| [stdrs.dev](https://stdrs.dev/)  {{ esoteric() }}                                          | `std` 文档的快捷方式，包括编译器内部模块。 |
| [docs.rs](https://docs.rs/)                                                                | 第三方库的文档，从源代码自动生成。         |
| [releases.rs](https://releases.rs/)                                                        | 之前和即将发布的版本的发布说明。           |

</div>

{{ tablesep() }}


## 打印与 PDF {#printing-pdf}

> 想要这份 Rust 速查表的 PDF 吗？在这里下载<a href="https://cheats.rs/dl/rust_cheat_sheet_a4.pdf"><b>最新的 PDF（A4）</b></a>和<a href="https://cheats.rs/dl/rust_cheat_sheet_letter.pdf"><b>Letter</b></a>格式。或者，通过<i>文件 > 打印</i>然后“另存为 PDF”自行生成（在 Chrome 中效果很好，在 Firefox 中有些问题）。

</noprint>

<footer>

 由 <a href="https://github.com/jhq223" target="_blank">jhq223</a> 翻译和托管，
        基于 <a href="https://cheats.rs" target="_blank">cheats.rs</a> (Ralf Biedert)。
<noprint>

[法律与隐私](legal) - [常见问题](faq) - [关于翻译](about-translation)

</noprint>

</footer>