# Rust 2022 生态版图年度报告

作者：张汉东

---

去年我写了 [2021 年 Rust 生态版图调研报告 | 星辰大海（上）](https://zhuanlan.zhihu.com/p/456451233) 和 [（下）](https://zhuanlan.zhihu.com/p/458046979) ，大家能看到 Rust 在各个行业领域中开始暂露头角。2022 年，在政治动荡、经济下行和疫情肆虐的世界大环境下，Rust 却迎来了高质量的发展。2022 年，我愿称之为 Rust 发展元年。

## 系列目录

-   Rust 2022 漫谈
-   Rust 2022 全球商业应用盘点
-   Rust 2022 安全参考
-   Rust 2022 开源生态盘点

---

#  Rust 2022 漫谈

##  踏上新的征程：Rust 2024  

Rust 2021 Edition 发布以后，官方就开始制定 Rust 2024 Edition 的路线图了。Rust Edition 是每三年发布的一个大版本（版次）。在 2022 年 4 月，官方博客[宣布 Rust 2024 Roadmap](https://lang-team.rust-lang.org/roadmaps/roadmap-2024.html) 。让我们了解一下 Rust 的下一步愿景是什么。

#### Rust 2024：广泛应用

Rust 的目标是成为一门赋予每个人构建可靠且高效软件能力的语言。Rust 不仅需要设计和实现一种具有优秀库和优秀工具的优秀语言，还需要维护一个优秀的支持社区。

Rust 2024 Edition 的目标是广泛使用，即，让越来越多的人开始使用 Rust 。为了达到这个目标，2024 Edition 需要关注以下三个重点：

- 拉平 Rust 语言的学习曲线。让 Rust 更容易为新用户和现有用户所用，并让解决难题变得更容易。这样可以吸引更多新的 Rust 用户。
- 增强 Rust 用户间的彼此合作。
- 让 Rust  Project (语言自身项目）的贡献者更加方便

##### 拉平学习曲线

建立大型 Rust 用户团队的公司报告说，Rust 工程师的典型的上岗时间约为 3-6 个月。当然，一旦人们学习了 Rust，他们通常会喜欢上它。即便如此，许多人表示在使用它时感觉“认知开销”很高，而“学习曲线”仍然是不使用 Rust 的最常见原因。事实是，即使在您了解了 Rust 借用检查器的工作原理之后，仍然有许多“小细节”需要正确处理才能让您的 Rust 程序编译。

对于 Rust 2024 目标是让开发者能够直接关注问题域的“固有复杂性”，并尽可能避免来自 Rust 的“意外复杂性”。

实现这一愿景的计划是专注于四个高级目标（按从广义到精确的顺序）：

-   **更精确的分析，更少的繁琐：**通过改进借用检查器、类型推断等，使编译器能够更好地识别代码何时正确。识别并消除“样板”模式，例如必须在各处复制和粘贴同一组 where 子句。
-   **更轻松地表达自己：必要时扩展语言，以便开发者可以更直接地表达他希望代码执行的操作。在某些情况下，这采用语法糖的形式（例如 [let-else](https://github.com/rust-lang/rust/issues/87335)），但在其他情况下，它可能意味着扩展类型系统以能够描述新模式（例如[泛型关联类型](https://rust-lang.github.io/generic-associated-types-initiative/)）。
-   **改进异步支持**：将我们的`async/await`支持扩展到当前的“MVP”之外，以包括 trait 中的`async fn`、`async drop`和支持[异步愿景文档](https://rust-lang.github.io/wg-async/vision/roadmap.html)路线图所需的其他功能。
-   **提升`dyn Trait`可用性**：**拓宽可以使用`dyn`的 trait 集，并使使用`dyn`更接近于使用泛型。

##### 增强 Rust 用户间的彼此合作

Rust 结合了所有权和借用、底层系统控制以及过程宏等强大的可扩展性机制，使其成为编写库的绝佳语言。而且，多亏了 Cargo，在程序中使用一个库只需要几行代码。尽管如此，仍有许多事情是库作者不能做或不容易做到的。例如，他们无法控制用户看到的错误消息或部署需要特殊选择加入的“Unstable”功能。 Rust 2024 希望通过帮助管理功能生命周期或扩展库的功能来构建使库作者能够更好地为用户服务的功能。

Rust 2024 希望追求能够在生态系统中进行更多探索的变化，实现这一愿景的计划是专注于四类工作：

-   **功能生命周期**：帮助库作者在功能从实验阶段过渡到最终完成阶段时为其提供支持。帮助库作者管理他们的开发生命周期和演变。
-   **更丰富的抽象**：扩展语言让库作者表达更丰富的抽象。比如支持 GAT ，让开发者编写更通用的库。
-   **定制开发人员体验**：许可库作者可以定制开发人员体验，例如，定制未实现 trait 或引入自定义 lints 时用户收到的错误消息。
-   **互操作性**：库生态系统可以轻松协调，使库协同工作，而无需将它们捆绑在一起。库作者可以根据需要编写可在多种环境中移植或特定于一种环境的代码。


##### 让 Rust  Project 的贡献者更加方便

Rust 语言自身也是一个 Rust 项目，虽然 Rust 语言项目非常活跃，但是当潜在贡献者想要对 Rust 项目贡献时，可能无法弄清楚感兴趣或想要贡献的某些特定事物的状态。因此 Rust 官方团队需要一个系统，以便这些贡献者可以很容易地知道 Rust 项目的状态而更容易地找到贡献点。

Rust 2024 实现这一愿景的计划是将重点放在四类工作上。

- 一目了然地看到状况。潜在贡献者能够很容易地识别出语言团队正在积极开展哪些工作，以及这些设计已经取得了多大进展。希望每一个跟踪问题都能清楚地识别出需要哪些 "下一步 "来推动该特定功能的完成，并确保这些步骤被清楚地记录下来，供可能的贡献者参考。
- 清晰的所有者和清晰的沟通。Rust是通过共识运作的，但这并不意味着每个人都必须知道所有的细节。因此需要一个系统，对需要完成的工作有明确的所有者，最好是不在 Lang 团队中的所有者。简单的分工会导致日后的冲突，所以我们也需要频繁的沟通和更新，以确保每个人都能了解事情的整体发展方向，并尽早地提出问题。
- 高效、开放的流程与工具支持。官方团队一直在寻找方法来改善他们的运作方式。他们注意到的一点是，由机器人或其他工具支持的流程往往能更好地工作。


### 2022 语言改进看点

2022 年 Rust 语言一共发布 11 个稳定版本（1.58～1.66），从语言特性、编译器到库 API 均有改进。下面分别从这三方面罗列了一些看点。

#### 语言特性

-  [字符串格式化支持捕获变量的形式`{ident}`](https://github.com/rust-lang/rust/pull/90473/) 
-   [`*const T` 现在支持常量上下文中解引用](https://github.com/rust-lang/rust/pull/89551/) 
-  [泛型结构体中使用 `Unsize`的规则更加宽松 ](https://github.com/rust-lang/rust/pull/90417/) ，参考 [relaxed_struct_unsize 跟踪 issue](https://github.com/rust-lang/rust/issues/81793) 
- [稳定新的 asm！和 global_asm！适用于 x86、x86_64、ARM、Aarch64 和 RISC-V](https://github.com/rust-lang/rust/pull/91728/) 
- [稳定解构赋值](https://github.com/rust-lang/rust/pull/90521/)，比如支持这种形式`(a, (b.x.y, c)) = (0, (1, 2));`
- [稳定常量泛型参数支持默认参数值，并移除类型和 const 参数的顺序限制](https://github.com/rust-lang/rust/pull/90207/)
- [稳定`#[cfg(panic = "...")]`为`"unwind"`或`"abort"`](https://github.com/rust-lang/rust/pull/93658)
- `const fn` 签名现在已经支持   [泛型 trait 限定](https://github.com/rust-lang/rust/pull/93827/)、 [返回位置的 `impl Trait`](https://github.com/rust-lang/rust/pull/93827/) 和 [函数指针的创建传递转换](https://github.com/rust-lang/rust/pull/93827/)，以及 [`extern "C"`或`extern "Rust"`](https://github.com/rust-lang/rust/pull/95346/)
-  [NLL 稳定，当前编译器仅使用基于 MIR 的借用检查](https://github.com/rust-lang/rust/pull/95565/)
- [稳定`let else`](https://github.com/rust-lang/rust/pull/93628/)
-   [稳定泛型关联类型 (GAT)](https://github.com/rust-lang/rust/pull/96709/)，重要特性，允许开发者可以更方便地开发更加通用的库和框架。
-  [未初始化的整数、浮点数和原始指针现在被视为立即 UB](https://github.com/rust-lang/rust/pull/98919/)。使用 `MaybeUninit`是处理未初始化内存的正确方法。
- [不允许对 `Pin<T>` （哪怕 T 在本地）实现 `Drop`](https://github.com/rust-lang/rust/pull/99576/)
- [重复的生命周期参数将不被自动省略](https://github.com/rust-lang/rust/pull/103450)

#### 编译器

- [升级到 LLVM 14](https://github.com/rust-lang/rust/pull/93577)
- [出现 lint 错误后不要中止编译](https://github.com/rust-lang/rust/pull/87337/)
- [错误消息在更多地方指向 trait bound obligations 的来源](https://github.com/rust-lang/rust/pull/89580/)
- [将 -Z strip 稳定为 -C strip](https://github.com/rust-lang/rust/pull/90058/)
- 添加了更多的 Tier 3 编译目标
- 编译器内部完成了[统一跨所有平台的 可重入锁 ReentrantMutex 实现](https://github.com/rust-lang/rust/pull/96042/)
- [为优化编译启用 MIR 内联](https://github.com/rust-lang/rust/pull/91743) 这为真实世界的 crate 提供了 3-10% 的编译时间改进。查看[性能结果](https://perf.rust-lang.org/compare.html?start=aedf78e56b2279cc869962feac5153b6ba7001ed&end=0075bb4fad68e64b6d1be06bf2db366c30bc75e1&stat=instructions:u)。


#### 库 与 API 

- [`copy`和`copy_nonoverlapping`重新启用调试检查](https://github.com/rust-lang/rust/pull/90041/)
- [`Duration::new`](https://doc.rust-lang.org/stable/std/time/struct.Duration.html#method.new) 和相关的一系列函数可以用于常量上下文
- 稳定[`ops::ControlFlow::is_break`](https://doc.rust-lang.org/stable/std/ops/enum.ControlFlow.html#method.is_break) 和[`ops::ControlFlow::is_continue`](https://doc.rust-lang.org/stable/std/ops/enum.ControlFlow.html#method.is_continue)
- 稳定 [`std::thread::available_parallelism`](https://doc.rust-lang.org/stable/std/thread/fn.available_parallelism.html) ，该函数可以返回程序应使用的默认并行度的估计值，即它可以同时执行的计算数量的限制。也会考虑CPU 配额。例如，在一个有 8 个虚拟 CPU 但配额只允许 50% 使用率的容器中，`available_parallelism`将返回 4。
- 常量上下文中新支持了很多 API ，比如   [`<*const T>::offset`和`<*mut T>::offset`](https://doc.rust-lang.org/stable/std/primitive.pointer.html#method.offset) 
- [用基于 futex 的 RwLock 取代了 Linux 上基于 pthread 的 RwLock](https://github.com/rust-lang/rust/pull/95035/)，另外 [Mutex 和 Condvar 也正在被改进 ](https://github.com/rust-lang/rust/issues/93740)
- [标准库中修复了许多不正确的使用`mem::uninitialized`的情况](https://github.com/rust-lang/rust/pull/99182/)
- 增加 [`thread::scope`](https://doc.rust-lang.org/stable/std/thread/fn.scope.html) 的支持


#### 其他
-  [rustdoc 支持递归显示所有 Deref 实现](https://github.com/rust-lang/rust/pull/90183/) 
-  Cargo 支持[支持缩写`--release`为`-r`](https://github.com/rust-lang/cargo/pull/10133/) 
- [  Cargo 将在二进制文件之前完成库的文档化](https://github.com/rust-lang/cargo/pull/10172/)
- 在 `std::os::unix::io`中添加[`/proc/self/mem`.](https://github.com/rust-lang/rust/pull/97837/) 有关的文档
- [Cargo 现在可以从workspace继承设置，以便可以将设置集中在一个地方](https://github.com/rust-lang/cargo/pull/10859)
- [Rustup组件`rust-analyzer`现已在稳定channel上可用。](https://github.com/rust-lang/rust/pull/98640/)
- [`BTreeMap`修复了一个健全性错误](https://github.com/rust-lang/rust/pull/99413/)，允许在容器之前删除它借用的数据。


**点评**：**今年最重要的语言特性就是泛型关联类型（GAT ）的稳定**。GAT 的稳定带给了 Rust 更高级的抽象方式，允许库和框架开发者开发出更加通用的工具。


## Rust 社区热点观察

### Rust for Linux 进入 Linux 内核

> 参考： [Rust for Linux 文档](https://www.kernel.org/doc/html/next/rust/index.html) 

今年最热的热点就是 Rust for Linux 进入 Linux 6.1 内核。

在今年10 月，初始的 Rust 基础设施[已被合并到 Linux 6.1](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=8aebac82933ff1a7c8eede18cab11e1115e2062b) 。意味着未来 Rust 编程语言将用于内核驱动程序和其他子系统的代码。但初始的 12.5k 行新代码只提供了底层的基础设施和一些非常基础的集成，据称未来的 PR 将添加更多的子系统抽象、多个 Rust 编写的驱动程序等等。目前，构建具有 Rust 支持的 Linux 内核仍然是可选的。

在 11 月，领导 Rust for Linux 工作的 Miguel Ojeda [发布了](https://www.oschina.net/action/GoToLink?url=http%3A%2F%2Flore.kernel.org%2Flkml%2F20221110164152.26136-1-ojeda%40kernel.org%2F)一组优化补丁（ 28 个），为内核提供了更多的 Rust 核心支持代码。这些新的补丁很可能会在 Linux 6.2 合并窗口中看到。


### 整个 Android 12 和 13 系统中，Rust 代码中发现的内存安全漏洞为零

近日， Google 发文称 [Android 中使用了内存安全语言 Rust ](https://security.googleblog.com/2022/12/memory-safe-languages-in-android-13.html) 之后，发现内存安全漏洞的数量在过去几年/版本中大幅下降，从 2019 年到 2022 年，内存安全漏洞的年度数量从 223 个下降到 85 个。**2022 年是内存安全漏洞不再占 Android 大部分漏洞的第一年**。

在 Android 13 中，大约 21% 的新原生代码（C/C++/Rust）是 Rust。AOSP 中大约有 150 万行 Rust 代码，涵盖新功能和组件，例如 Keystore2、新的超宽带 (UWB) 堆栈、DNS-over-HTTP3、Android 的虚拟化框架 (AVF) 以及各种其他组件及其开源依赖项。

**迄今为止，在 Android 的 Rust 代码中发现的内存安全漏洞为零。**

我们不希望这个数字永远保持为零，但考虑到两个 Android 版本中新 Rust 代码的数量，以及使用它的安全敏感组件，这是一个重要的结果。它表明 Rust 正在实现其防止 Android 最常见漏洞来源的预期目的。在许多 Android 的 C/C++ 组件（例如媒体、蓝牙、NFC 等）中，历史漏洞密度大于 1/kLOC（每千行代码有 1 个漏洞）。基于这个历史漏洞密度，使用 Rust 很可能已经阻止了数百个漏洞进入生产环境。

在 Android 的 Rust 中使用 unsafe 似乎按预期工作。它很少被使用，当它被使用时，它是一种封装行为，更容易推理和审查安全性。比如，UWB 代码中 unsafe 有两种用法：一种是实现对存储在 Java 对象中的 Rust 对象的引用，另一种是用于拆解该对象。Unsafe 在这种情况下非常有用，因为对这段代码的额外关注使我们能够发现可能的竞争条件并加以防范。

Rust 在 Android 平台上的使用正在增长，但这还没有结束。为了实现提高 Android 范围内的安全性、稳定性和质量的目标，Android 团队决定需要在本机代码的任何地方使用 Rust。目前正在用 Rust 实现用户空间 HAL。在受信任的应用程序中添加了对 Rust 的支持，已将 Android 虚拟化框架中的 VM 固件迁移到 Rust。随着 Android 从 C/C++ 迁移到 Java/Kotlin/Rust，预计内存安全漏洞的数量将继续下降。


### Rust 语言引入了吉祥物彩蛋

当你使用 Rust 吉祥物 🦀 定义变量时，

```rust
fn main(){
	let 🦀 = 1;
}
```

Rust 编译器会抛出专属的错误:

```rust_errors
error: Ferris cannot be used as an identifier
 --> src/main.rs:2:9
  |
2 |     let 🦀 = 1;
  |         ^^ help: try using their name instead: `ferris`
```

🦀 本来是非官方吉祥物，这个彩蛋也许是来自官方的一种文化认可。

### rust-analyzer 被纳入 rust-lang 官方仓库中

[rust-analyzer](https://github.com/rust-lang/rust-analyzer) 现在已经成为了 Rust 官方的一员。VSCode 、NeoVIM 和 Emacs 等编辑器对 ra 有很好的支持。如果你使用基于 IntelliJ 平台的 IDE，如 CLion、IDEA 或 PyCharm，则不需要 rust-analyzer，而应该使用JetBrains 的[IntelliJ Rust](https://intellij-rust.github.io/)插件。

2019 年 rust-analyzer 社区刚起步构建 IDE 的基础，到 2020 年，[RFC2912](https://github.com/rust-lang/rfcs/pull/2912)中 就提倡：“将 rust-analyzer 作为官方的 LSP（语言服务器协议）实现”。RFC 在社区的压倒性支持下被接受：它仍然是有史以来投票最多的 Rust RFC。让 ra 成为官方的一员将持续推动该 RFC 的落地。接下来，将 rust-analyzer 宣传为 Rust IDE 支持的极有可能的未来，收集反馈，并根据其积极结果，淘汰当前推荐的语言服务器 RLS。

### 来自开源作者的呐喊：“请记住，我的项目是零收入”

开源项目[Kind](https://github.com/kindelia/kind)和[HVM](https://github.com/kindelia/hvm)的作者 Victor Taelin ，收到一位社区中有影响力的人的如是批评：“这个项目背后的人往往会建立令人印象深刻的东西，但后来他突然放弃了这些东西，然后去做点别的……”。 这份批评让 Victor 非常难过，因为这位来自社区有影响力的人也给予了 Victor 很多灵感。

Victor 公开声明：“**我们只是没有资金**！看，这不是大公司的工作，甚至不是大团队的工作。80% 的代码仍然是我做的。有一些朋友帮忙，但他们大多是兼职，自愿，还在学习这东西，所以帮助有限。**然而，什么都没有被放弃。我们只是受到我们微小规模的限制。我没有报酬，这不是一家营利性公司，我只是一个创造酷炫、免费技术以推动人类进步的人。我热爱我的工作！不过，如果您确实希望看到我的想法更快地发展，请考虑对它们进行投资”。

Victor 说：**不管怎样，HVM 和 Kind 都在积极、热情的开发中，并将继续向前发展，即使有点慢！**

来自社区的另一位回复非常暖心：“老实说，即使你放弃了你的项目，我仍然会感谢你的工作。你的输出是创新的，我可以看到它们影响未来的 PL 发展。就我个人而言，我认为你对我自己产生了积极的影响，并且确实帮助激发了我对类型理论的兴趣。综上所述，请不要让一些误导性的批评使您沮丧。只要继续做你最擅长的事情，你就会知道这些年来你已经赢得了很多感激的支持者。”

### Rust 1.65 稳定版发布

Rust 1.65 稳定版发布带来了 Rust 最重要的特性：泛型关联类型。该特性的重要性可以这么说：如果没有它， Rust 将停滞不前。GAT 非常通用，可以实现许多当前无法编写的模式。有关更多信息，请查看[稳定公告](https://blog.rust-lang.org/2022/10/28/gats-stabilization.html)。

### 虚幻引擎集成 Rust

社区中有人将 [Rust 集成到了 虚幻引擎](https://maikklein.github.io/unreal-rust-1/)（Unreal Engine ）5 中，发布了 [unreal-rust](https://github.com/MaikKlein/unreal-rust)。`unreal-rust` 使用基于 Bevy 的实体组件系统 (ECS)，然后 Rust 通过 C FFI 与 Unreal 通信，在 Unreal 之上编写`AActor`并以 Rust 友好的方式公开其 API。

虽然是个人项目，但非常有创意。

###  Asahi Lina 谈她用 Rust 编写内核驱动程序的经历

Asahi Lina [用 Rust 编写了新的 Apple AGX GPU 驱动程序（M1 和 M2）](https://lore.kernel.org/rust-for-linux/70657af9-90bb-ee9e-4877-df4b14c134a5@asahilina.net/t/)。这些 GPU 运行固件并且具有相当复杂的需要宿主机管理的共享内存数据结构，所以 Lina 一直倾向于 Rust。在使用 Rust 之后，Asahi Lina 如是说：「关于内核中的 Rust 是否有用存在很多奇怪的争论......根据我的经验，它比我想象的更有用！  我从第一个渲染到一个稳定的桌面，可以运行游戏、浏览器等。在我的驱动程序上工作了大约两天！所有并发错误都随着 Rust 消失了！内存在需要释放时被释放！一旦你学会了让 Rust 与你一起工作，我觉得它会引导你编写正确的代码，甚至超出语言的安全承诺。这真的很神奇！✨」


### NSA 发布关于如何防范软件内存安全问题的指南

美国国家安全局 (NSA) 发布了[一份指南](https://www.nsa.gov/Press-Room/News-Highlights/Article/Article/3215760/nsa-releases-guidance-on-how-to-protect-against-software-memory-safety-issues/)，以帮助软件开发人员和操作员预防和缓解软件内存安全问题，这些问题占可利用漏洞的很大一部分。建议使用内存安全的Rust 语言。

NSA 方面表示，内存安全问题在可利用的漏洞中占比很大。并引用了微软的数据指出，该公司从 2006 年到 2018 年 70% 的漏洞是由于内存安全问题造成的；谷歌的 Chrome 在几年内也发现了类似比例的内存安全漏洞。

该组织认为，恶意的网络行为者会利用不良的内存管理问题来访问敏感信息、颁布未经授权的代码执行、以及造成其他负面影响，而这些通常会危及设备并成为大规模网络入侵的第一步。

###  Rust 连续 7 年荣获 Stackoverflow 最受欢迎语言

每年面向百万开发者的[Stackoverflow](https://survey.stackoverflow.co/2022/?utm_source=so-owned&utm_medium=announcement-banner&utm_campaign=dev-survey-2022&utm_content=results#section-most-loved-dreaded-and-wanted-programming-scripting-and-markup-languages) 调研结果显示，Rust 再次拿下最受欢迎语言，今年是连续第七年收获此殊荣。并且，在今年 11月的 [TIOBE](https://www.tiobe.com/tiobe-index/) 编程语言排行榜中，Rust 也首次进入了前二十，暂排第 17 位。

### Rust 基金会成员增加到了 39 家

在 2021 年2 月9 日 Rust 基金会成立之初，只有Mozilla、Amazon、华为、谷歌、微软五家创始白金成员，截止到今天（2022.12月）已经有 39 家不同领域的头部公司成为了[Rust 基金会成员](https://foundation.rust-lang.org/members/)，共同推动 Rust 在各自领域的落地。


## 本节小结

2022 年，是新的起点。在 2021 Edition 发布之后，官方又起草和制定了 2024 Edition 路线图，并且在该路线图的指导下开启了新的征程。Rust 2024 的目标是让 Rust 广泛应用。

2022年，Rust 语言特性上取得了重大进展，稳定发布了泛型关联类型。这一特性的发布将解锁 Rust 语言高阶统一抽象，促进生态库和框架的长足发展，以及 Rust 异步特性向零成本抽象的目标更近了一步。

2022 年，最受人们关注的是 Rust for Linux 进入Linux 内核这件事。虽然当前进入内核的只是初步基础补丁，但这关键的一步已经为未来 Rust 在 Linux 内核领域发展奠定了很好的基础。

2022 年，也是收获硕果的一年。Google Android 团队宣布，**2022 年是内存安全漏洞不再占 Android 大部分漏洞的第一年**。Android 13 已经有大约 21% 的新原生代码（C/C++/Rust）是 Rust。AOSP 中大约有 150 万行 Rust 代码，涵盖新功能和组件。并且，**迄今为止，在 Android 的 Rust 代码中发现的内存安全漏洞为零。** 

2022 年，我们也看到社区中一些个人开发者，虽然遭遇不公平的流言蜚语，依然对 Rust 热爱依旧，在零收入的状况下默默地使用 Rust 实现自己的开源项目。

2022 年，可以说是 Rust 语言的发展元年。随着越来越多的公司采用 Rust ，Rust 变得越来越受欢迎。展望未来，我们衷心希望 Rust 2024 Edition 发布目标，让 Rust 广泛应用，可以圆满实现。

---

# Rust 2022 全球商业化应用盘点

- 前言
- Rust 基金会成员应用盘点
- Rust 初创产品
- Rust 领域应用
- 本节总结

2022 年是 Rust 语言距离稳定版正式发布以来已经走过的第七年。从 Rust 发布以来，就一直受到广大开发者的欢迎。在 Stackoverflow 来自 180 个国家 7万3千多名开发者的投票调查中，Rust 连续七年荣获最受欢迎的编程语言，87% 的开发人员希望使用 Rust 。

2022 年也距离 [Rust 基金会](https://foundation.rust-lang.org)成立的第二年。在 2021 年2 月9 日 Rust 基金会成立之初，只有Mozilla、Amazon、华为、谷歌、微软五家创始白金成员，截止到今天（2022.12月）已经有 39 家不同领域的头部公司成为了[Rust 基金会成员](https://foundation.rust-lang.org/members/)，共同推动 Rust 在各自领域的落地。

2022 年在 Rust 基金会成员公司之外，也有不少公司开始使用 Rust。其中包含初创企业，使用 Rust 从头构建产品；也有成立多年的老牌公司，使用 Rust 来改进生产。Rust 开发者数量也逐渐增多。据开发者调查分析公司 SlashData 发布了一份题为“[第 22 届开发者国家状况](https://www.slashdata.co/free-resources/state-of-the-developer-nation-22nd-edition)”的报告指出，从 2020 年 Q1 季度到 2022 年 Q1 季度，Rust 语言的开发者用户量从 60 万猛增到了 220 万。[TIOBE](https://www.tiobe.com/tiobe-index/) 编程语言排行榜2022 年 11 月榜单中，Rust 语言进入了前 20 。

可以说，2022 年是 Rust 语言开始广泛应用的元年。本文就让我们来盘点一下 Rust 在全球商业化领域的应用状态。


## Rust 基金会成员应用盘点

> Rust 基金会成员投资 Rust ，尤其是白金成员们，是在投资 Rust 的可持续性，他们认为应该使用这种语言来构建可持续且安全节能的解决方案。

###  白金成员如何应用 Rust 

在 AWS，Rust 已迅速成为大规模构建基础设施的关键。[Firecracker](https://firecracker-microvm.github.io/)是一种开源虚拟化技术，为[AWS Lambda](https://aws.amazon.com/lambda/)和其他无服务器产品提供支持，它于 2018 年公开发布。AWS 使用 Rust 来交付[Amazon Simple Storage Service](https://aws.amazon.com/s3/) (Amazon S3)、[Amazon Elastic Compute Cloud](https://aws.amazon.com/ec2) (Amazon EC2)、[Amazon CloudFront](https://aws.amazon.com/cloudfront/)等服务。2020 年，推出了[Bottlerocket](https://aws.amazon.com/bottlerocket/)，这是一个用 Rust 编写的基于 Linux 的容器操作系统。 Amazon EC2 团队使用 Rust 作为新[AWS Nitro 系统](https://aws.amazon.com/ec2/nitro/)组件的首选语言，包括敏感应用程序，例如[Nitro Enclaves](https://aws.amazon.com/blogs/aws/aws-nitro-enclaves-isolated-ec2-environments-to-process-confidential-data/)（用于处理机密数据的隔离 EC2 环境）。

此外，过去一年，[Amazon Prime Video 使用了 WASM 和 egui](https://www.amazon.science/blog/how-prime-video-updates-its-app-for-more-than-8-000-device-types) 为超过 8k 多种设备类型更新其应用向数百万客户提供内容（例如游戏机、电视、机顶盒和流媒体等）。他们认为对 Rust 和 WebAssembly 的投资得到了回报，经过一年的开发，共编写了 37,000 行 Rust 代码，显著地提高了性能、稳定性和 CPU 消耗并降低了内存利用率。

Google 将 Rust 应用于[Chromium](https://chromium.googlesource.com/chromium/src/+/refs/heads/main/docs/security/rust-toolchain.md)、 [Android](https://source.android.com/docs/setup/build/rust/building-rust-modules/overview) 和 [Fuchsia OS ](https://fuchsia.dev/fuchsia-src/development/languages/rust)中，其中 Chromium 对 Rust 支持是实验性的。开发者可以使用 Rust 为 Android 和 Fuchsia OS 开发组件，并且 Rust 在 Android 和 Fuchsia OS 内部代码使用超过了一定的比例，尤其是 Fuchsia OS 中 Rust 代码占比已经超过 50%。因为其内部 Cpp 代码比较多，所以 Google 联合 Meta (原 Facebook) 一起开发了 [cxx](https://cxx.rs/) 用于和 Cpp 安全交互。在今年 10 月份，Google 又推出基于开源 RISC-V 芯片的嵌入式系统的新型安全操作系统 KataOS。[Sparrow ](https://github.com/AmbiML/sparrow-manifest)是 KataOS 的参考实现，它运行在[seL4 之上](https://github.com/seL4)，几乎完全用 Rust 编写。该操作系统不适用于台式机或智能手机，而是用于物联网，可能用于智能家居。目标是为嵌入式硬件或边缘设备构建可验证的[安全操作系统](https://www.analyticsinsight.net/significance-of-cloud-security-how-businesses-can-enjoy-its-benefits-2/)，例如用于捕获图像的网络连接相机，这些图像在设备上或云中处理以进行机器学习。在最新发布的 [Android 13 版本](https://security.googleblog.com/2022/12/memory-safe-languages-in-android-13.html)中，Google 也宣布在 Android 13 中，大约 21% 的新原生代码（C/C++/Rust）是 Rust。AOSP 中大约有 150 万行 Rust 代码，涵盖新功能和组件。并且，**迄今为止，在 Android 的 Rust 代码中发现的内存安全漏洞为零。** 为了实现提高 Android 范围内的安全性、稳定性和质量的目标，Android 团队表示需要能够在代码库中需要本地代码的任何地方使用 Rust。

华为的目标是引领通信系统软件向安全可信演进，其中 Rust 语言正在发挥很大的作用。华为希望通过部分 C/C++ 代码的迁移，在保证高性能的同时，拥有更高的安全性。在此过程中， 为开发者提供一套自动化工具支持：基于开源的 C2Rust 转译工具， 首先从 C 代码生成 Rust 代码, 然后通过源到源变换工具自动重构。在华为内部还基于 Actor 的并发编程模式开发了 Rust 库，方便程序员充分利用 Rust的语言特性, 例如`async/await`等开发异步程序。华为也为 Rust 社区贡献了许多重要的功能特性。例如，为 Rust 编译器提交了一系列代码，使得 Rust 编译目标可以支持`ARM AArch64 32`位大端变体[ILP32](https://developer.arm.com/documentation/dai0490/latest/)芯片组, 用于华为的通信产品中。 这些改进使得华为和友商可以在这些常用网络硬件架构上执行Rust 原生程序。这些代码已经通过华为的 Rust 专家`Amanieu d'Antras` 提交给了 [LLVM 编译器](https://reviews.llvm.org/rG21bfd068b32ece1c6fbc912208e7cd1782a8c3fc), [libc 库](https://github.com/rust-lang/libc/pull/2039), 以及 [Rust 编译器](https://github.com/rust-lang/rust/pull/81455)等开源社区。华为国内工程师 [李原 也为 Rust 做了很多贡献](https://github.com/rust-lang/rust/pulls?q=is%3Apr+author%3ASparrowLii)，其中包括修复了多个当前并行编译导致的程序错误，(比如串行并行模式在迭代器panic场景的行为一致性、并行编译死锁处理的ICE问题）、分析并优化了多个编译过程中频繁锁同步导致并行编译效率降低的问题(比如生成attributes编号、生成生命周期依赖分析表等等)、优化了编译器中多处诊断信息的生成，(比如查询中layout深度限制、错误using语句的提示信息、let语句中默认类型的提示信息等)，并且在2022年李原主导发起[重启 Rust 编译器并行编译工作组](https://hackmd.io/@TKyxIWXBRqyDPLDPcP0qfg/parallel_rustc_mcp)，准备为加速 Rust 编译器并行编译做出贡献。

Meta（原Facebook ）从 2016 年开始使用 Rust，也就是该语言的 1.0 版发布一年后。Rust 是它用于 Diem（以前的 Libra）稳定币区块链、Mononoke 源代码控制服务器和Meta 的“用于区块链的新的安全编程语言” [Move的主要语言。](https://developers.diem.com/main/docs/move-overview) 选择 Rust 而不是 C++ 对 Meta 来说是一个重大决定，因为它的大部分后端代码都是用 C++ 编写的，这使其成为显而易见的选择。 据 Meta 称，在 Mononoke 被认为取得成功后，Rust 的采用势头强劲，吸引了具有 Python 和 JavaScript 背景的工程师。 现在，Rust 与 Hack、C++ 和 Python 一起成为主要受支持的服务器端语言。 Meta现在建议将 Rust 用于编写命令行界面 (CLI) 工具和“性能敏感的后端服务”。 Meta 内部也针对 Rust 建立了专门的新手训练营，用于培养 Rust 工程师。Meta 对 Rust 生态的重要贡献之一是 [`cxx`](https://cxx.rs/) ，用于 Rust 和 Cpp 之间的安全交互。在 2022年 7 月，Meta 首次宣布 Rust 成为 [Meta 支持服务器端使用的编程语言](https://engineering.fb.com/2022/07/27/developer-tools/programming-languages-endorsed-for-server-side-use-at-meta/)。

Microsoft 拥有世界上最大的 C/C++ 代码库之一。从 Windows 和 Office 到 Azure 云，其所有核心产品都在其上运行。从2019年开始，微软开始寻找内存安全的语言，与此同时，引入了 Rust 进行尝试。随后在 GitHub 上开源了 [Rust for Windows 库](https://github.com/microsoft/windows-rs/releases)  ，供 Rust 开发者们无缝地使用 Windows API。此外，Azure 孵化的团队 DeisLabs 开始尝试用 Rust  构建 Krustlet 来允许开发人员在 Kubernetes 中运行多个 WebAssembly 模块的服务。2022 年[微软 Azure](https://www.analyticsinsight.net/microsofts-azure-cloud-is-going-to-space-with-this-expansion/)首席技术官Mark Russinovich表示，C 和[C++](https://www.analyticsinsight.net/why-every-programmer-should-learn-c-c-during-their-careers/)不应该用于新项目。“是时候停止使用 C/C++ 启动任何新项目，并将 Rust 用于那些需要非 GC 语言的场景。为了安全性和可靠性，业界应该宣布这些语言已被弃用”。他在 Twitter 上表示，表达的是个人观点，而不是微软的新政策。

> 2022 年 DeisLabs 初创团队离职后出来创业创建了 [Fermyon 公司](https://www.fermyon.com/) ，专注于 WebAssembly 云产品。

JFrog 于 2022 年 9 月宣布加入了 Rust 基金会成为白金会员。JFrog 提供了一个[DevOps 平台](https://jfrog.com/) ，并且支持多种主流编程语言。JFrog 加入 Rust 基金会的目的就是为了与 Rust 社区和 Rust 基金会合作，帮助保护软件供应链。JFrog 将识别并消除 Rust 平台和生态系统面临的安全威胁，并修正 Rust 平台问题以防止进一步的风险。随着物联网（IoT）、云计算和大数据的出现，网络安全威胁也越来越大。在过去两年中，Rust 编程语言的使用量增加了两倍，达到 220 万开发人员。JFrog 与非营利组织的合作反映了其从最近采用的覆盖组织软件供应链的安全解决方案中获益的战略。


###  金牌成员如何应用 Rust 

[Shopify](https://shopify.engineering/shopify-rust-systems-programming) 是加拿大跨国电商公司，在 2022 年 12 月份宣布加入 Rust 基金会，成为基金会第一个金牌会员。 Shopify 在服务端一直使用 Ruby 语言，从2021年开始，Shopify 团队开始使用 Rust 实现[YJIT，这是一种新的 CRuby 即时 (JIT) 编译器](https://shopify.engineering/yjit-just-in-time-compiler-cruby) ，到今年合并到了 Ruby 3.1 版本中。在最近的一次[性能测试](https://speed.yjit.org/)中，YJIT 的性能比 Ruby 解释器 CRuby 快了 38%。

除此之外， Shopify 也决定采用 Rust 作为公司的系统编程语言，比如编写高性能网络服务器。在 Shopify 看来，**Rust 的一致性、性能、社区生态、生产力、安全和互操作性**是他们采用 Rust 用于系统编程的原因。


### 银牌会员及普通赞助商如何应用 Rust

Rust 基金会的银牌成员逐渐增多，目前已经达到了 28 家公司。这些公司分布在各个领域。此外，还包括三家非会员普通赞助商。在文后的「Rust 其他领域应用」小节将统计他们的应用信息。


## Rust 初创产品

2022 年也可以算作是 Rust 创业元年。因为今年陆续有好几家采用 Rust 的创业公司拿到了巨额融资。

### Fermyon

首当其冲的是[ Fermyon 技术公司](https://www.fermyon.com/)。在今年十月份，[Fermyon 宣布](https://www.forbes.com/sites/justinwarren/2022/10/24/webassembly-pioneer-fermyon-raises-20-million-series-a-releases-fermyon-cloud/?sh=6dbc1d6031bb)拿到了 2000 万美元的 A 轮融资。并且发布了 Fermyon Cloud 平台。

Fermyon Cloud 旨在使[基于 WebAssembly 的应用程序和微服务的](https://pivotnine.com/2022/07/08/fermyon-revolution-microservices-wasm/ "https://pivotnine.com/2022/07/08/fermyon-revolution-microservices-wasm/")部署变得快速和容易。使用 Fermyon 的 [Spin](https://github.com/fermyon/spin) 构建工具（基于 Rust 实现），为 WebAssembly 编译和打包应用程序，然后可以立即将其部署到 Fermyon Cloud。Fermymon 的工具链处理将应用程序代码投入生产所需的所有基础设施配置和部署步骤，使应用程序开发人员无需了解有关底层基础设施的任何信息。

WebAssembly 起源于浏览器，针对高安全性和低资源消耗进行了优化。通过将 WebAssembly 引入服务器环境，应用程序可以享受相同的优化，同时使用通用代码库部署到各种环境：云、边缘、物联网或任何组合。Fermyon 以这些概念为基础，将 WebAssembly 引入数据中心和云端。Fermyon 希望实现类似于 Java 的“一次编写，随处运行”的承诺，同时又具有 Heroku 的易用性。它使开发人员无需过多考虑基础架构，从而有助于消除应用程序开发中的摩擦。

“使用 Fermyon Spin，开发人员可以快速创建 WebAssembly 微服务应用程序，现在使用 Fermyon Cloud，开发人员可以在不到两分钟的时间内从零开始实现并部署应用程序。这是 WebAssembly 在云中实现的承诺：快速开发、快速部署、快速执行。”，Fermyon 的联合创始人兼首席执行官 Matt Butcher 在一份声明中如是说。


### 新终端 Warp


虽然现在的常用的终端模拟器也有很多好用的，比如 Rust 实现的高性能跨平台现代化终端模拟器 [alacritty](https://link.zhihu.com/?target=https%3A//github.com/alacritty/alacritty) 。但它们的内核其实还是一个传统的终端模拟器。现代开发者，要使用终端做很多事，从构建代码、执行和部署，与版本控制系统交互到与云端交互等。作为开发者日常离不开的工具，在当下日益增长的开发需求的时代，现在的终端模拟器却没有帮助开发者提升更多工作效率。

而 Warp 的出现，让我看到了终端模拟器进化的下一代形态。[Warp](https://www.warp.dev/) 在 2022 年 4 月 5 号推出其公开测试版并[宣布获得 2300 万美元的资金](https://techcrunch.com/2022/04/05/warp-raises-23m-to-build-a-better-terminal/)，它正试图通过构建一个旨在提高开发人员生产力的新命令行终端来改变这一现状。Warp 值得关注的功能特性是对团队协作的支持，可以共享团队的终端模拟器会话，可以方便地解决团队之间沟通的问题。其他功能还有很多，包括集成了云端，可以让团队方便地共享剪切板等。更多功能可以去[这里](https://link.zhihu.com/?target=https%3A//docs.warp.dev/)查看。

我还没有来得及自己的去挖掘 Warp 的具体功能，但是单从这些功能特性上来看，正如 Figma CEO Dylan 所说，Warp 这个产品和 Figma （在服务端和 wasm 模块 也使用 Rust）很像，都是 **All in One，并且连接了云端，为团队协作提供了很多方便的功能**。并且在商业模式上，都属于产品驱动增长（PLG, Product-led Growth）型公司。事实上，正是 Figma CEO 领投了 Warp ，跟投的还有 Elad Gil （AirBnB、Pinterest、Stripe 和 Square 的早期投资者）、Jeff Weiner（领英执行董事长兼前CEO）和 Marc Benioff（Salesforce 创始人兼 CEO）。Dylan 认为 Warp 和 Figma 正是可以提升用户十倍工作效率的那种工具，他也承认投资 Warp 有赌博的成分。

Warp 选择使用 Rust 语言来实现。使用 Rust 技术栈（包括 WebAssembly）也方便构建跨平台支持。在底层，使用 Metal （Mac 的 GPU API）直接用 GPU 进行 UI 渲染。之所以使用 GPU 进行渲染，是因为团队想摆脱 CPU 上面的许多软件和架构瓶颈，来适应更高分辨率的显示器。选择 Metal 而不是 OpenGL 作为 GPU API，因为 Warp 把 MacOS 作为第一个平台。Xcode 中的 Metal 调试工具非常出色，使 Warp 团队能够检查纹理资源并轻松测量帧速率和 GPU 内存大小等重要指标。Mac 平台现在也是大多数开发者选择的重要生产力工具。

但是，目前 Rust 对 GPU 支持并不是很完善，没有开箱即用的合适的 UI 库。团队考虑过 [Azul](https://link.zhihu.com/?target=https%3A//azul.rs/)和[Druid](https://link.zhihu.com/?target=https%3A//github.com/linebender/druid)，但这两者都处于实验阶段，所以团队决定和 Atom 编辑器联合创始人 [Nathan Sobo](https://link.zhihu.com/?target=https%3A//github.com/nathansobo) 合作，使用他创建的一个受 Flutter 启发的 Rust UI 框架，不久后应该会开源。在未来，会支持更多的渲染后端，比如OpenGL 和 WebGL（会通过 wasm 支持）。同时也和 Nathan 合作，在 Warp 中构建了一个文本编辑器。Warp 也 fork 了 [Alacritty](https://link.zhihu.com/?target=https%3A//github.com/alacritty/alacritty) 的模型代码，用于处理数据模型，为 Warp 界面中的块实现提供了帮助。

看得出来，Warp 作为一个商业产品，它并没有将其产品的全部代码进行开源。但他们在实现产品过程中，通过解决 Rust GUI 和 GPU 渲染相关的问题，沉淀出一些工具和库，会以开源的方式贡献给社区。虽说要走 PLG 路线，开源社区非常重要，但也并不是说盲目地之间把产品全部开源出来。还是要根据自己的商业模式和产品形态做出最好的权衡。

### 初创数据库领域公司

今年在数据库领域的初创公司可以算得上是扎堆出现了。

 在 2022 年 4 月，Rust 社区知名开发者 Jon Gjengset 宣布成为 [ReadySet 公司](https://link.zhihu.com/?target=https%3A//readyset.io/)的联合创始人，准备将其博士论文中的 Noria 数据库研究成果进行落地为 ReadySet ，为数据库提供 SQL 缓存引擎，可帮助开发人员构建高性能的实时应用程序，而无需更改代码或切换数据库。[该公司目前 A 轮融资 2900 w 美元](https://link.zhihu.com/?target=https%3A//techcrunch.com/2022/04/05/readyset-raises-29m-to-expedite-access-to-enterprise-scale-app-data/)。

在 2022 年 4月，已经融资千万美元的数据库初创企业 Singularity Data [Singularity Data](https://36kr.com/project/1713086132758785)（奇点无限公司）宣布开源 Rust 实现的云原生的支持SQL的流式数据库 RisingWave 。RisingWave 于 2021 年初开始用 Cpp 创建，在七个月之后用 Rust 重写。对于早期创业公司来说，这是一个疯狂的决定。特别是在竞争激烈的环境中，对科技初创公司来说，时间几乎就是一切。


### 流媒体服务

实时事件流媒体公司 InfinyOn 筹集了 500 万美元的种子资金，由 Gradient Ventures 和 Fly Ventures 领投，Bessemer Venture Partners、TSVC 等参投。InfinyOn 使用由 Rust 开发的动态数据可编程平台  [Fluvio](https://github.com/infinyon/fluvio) 。Fluvio 拥有超过 1,000 个 Github star，在开发人员和开源社区中越来越受欢迎。

“在 Java 时代构建的遗留数据平台会生成大型二进制文件，需要大量内存，并且从边缘到核心的操作具有挑战性。这些也缺乏实时决策的在线处理能力，”InfinyOn 的联合创始人兼首席技术官 Sehyo Chang 说。“我们通过消除对 ETL 工具的需求来简化数据架构，提供更具成本效益的平台，内存减少高达 80 倍，并通过内存安全解决方案提供最大的安全性。”

“我们整合来自不同来源的医疗保健数据：物联网、患者和医生的输入。借助 InfinyOn，我们可以使用现代工具快速高效地完成这项工作。它是用 Rust 编写的，与 Kafka 相比，这使得团队更容易集成。” Nammu 首席执行官 Chris Brucker 说。

InfinyOn 可以轻松地从多个来源提取、整形和转换数据，并实时计算结果。虽然仍处于 Beta 阶段，但早期采用者已在 InfinyOn 的概念验证中看到了与替代解决方案相比的显着优势。除了易用性和开发速度之外，与其他供应商相比，供应商还看到了总拥有成本的显着降低。


## Rust 其他领域应用

### 软件定义汽车：Rust  的关键作用

> 关键字：软件定义汽车

汽车标准组织 Autosar——其成员包括福特、通用、宝马、博世、大众、丰田、沃尔沃等——在 4 月份宣布在其功能安全工作组 (WG-SAF) 中成立一个新的子组，以探索 Rust 如何能够用于其参考平台之一。SAE International 还 [成立了一个工作组](https://connexionplus.sae.org/communities/community-home/digestviewer/viewthread?GroupId=31&MessageKey=9e947f64-aefc-45cd-aee6-a787818af963&CommunityKey=c9c80476-9027-4edc-953c-65bda22ba7a7) 来研究汽车行业中与安全相关系统的 Rust 。在 5 月份 Autosar 和 Rust 团队进行了一次[交流](https://standardsworks.sae.org/standards-committees/safer-rust-task-force) ，探讨Safe Rust 在汽车领域是否可以构造一个合规的安全子集，讨论内容就是 Ferrocene Rust 安全子集。

> 随后 Autosar 官网撤销了成立新的 Rust 工作组的新闻，也许是要等待 Ferrocene Rust  的成果。另外，在今年9月份，Volvo 汽车公司的技术专家和系统架构师 [Julius Gustavsson 接受了采访](https://medium.com/volvo-cars-engineering/why-volvo-thinks-you-should-have-rust-in-your-car-4320bd639e09)，他坦言，想在 Volvo 中推动 Rust 开发。

####  Ferrocene Rust 安全子集

[Ferrous Systems ](https://ferrous-systems.com/blog/ferrous-systems-adacore-joining-forces/)和 [AdaCore ](https://blog.adacore.com/adacore-and-ferrous-systems-joining-forces-to-support-rust) 在今年2月份宣布，他们将联手开发 Ferrocene——一种符合安全要求的 Rust 工具链，旨在支持各种受监管市场的需求，例如汽车、航空电子设备、太空和铁路。这意味着根据各种安全标准对 Ferrocene Rust 编译器进行汽车安全性等级 ASIL 的 D 级（D 代表最高程度的汽车危险）认证，这项工作最终将包括必要的动态和静态分析工具的开发和资格认证。Ferrous Systems 和 AdaCore 也在寻找经过安全认证的库，包括语言支持 (libcore) 或其他用户库。我们的目标是针对与这些市场相关的各种架构和操作系统。这一愿景需要时间才能实现，而 Ferrous Systems 和 AdaCore 准备从关注某些特定方面开始。最终，我们的目标是像支持任何其他与高完整性应用程序开发相关的编程语言一样全面地支持 Rust。[Ferrocene 语言规范](https://spec.ferrocene.dev/)目前正在制定中，预计年底发布。

#### 其他公司

在 Rust 基金会银牌会员中还有 [ARM](https://www.arm.com/) 也在致力于推动 Rust 在软件定义汽车中落地。


### 即时通信: Threema

> 关键字：即时通信


[Threema](https://threema.ch/en) 是一款跨平台、隐私安全且开源的即时通信工具。


### 密码管理工具： 1Password

> 关键字：跨平台

1Password  [很早就使用 Rust 来构建其 Windows 客户端](https://serokell.io/blog/rust-in-production-1password)。在 2019 年将其支持浏览器扩展的逻辑引擎从 Go 移植到了 Rust ，然后就开始了 Rust 跨平台的应用实践。直到 2022 年 11 月，1Password 也开源了其[跨多种语言生成一致的类型模式](https://blog.1password.com/typeshare-for-rust/) 的 [Typeshare](https://github.com/1Password/typeshare) 库。Typeshare 可以帮助开发者实现跨语言无缝同步共享数据类型，这是跨平台安全开发的利器。


###  GUI ：目标取代 Qt 

> 关键字： Qt、GUI

全球知名Qt咨询和UI/UX设计服务公司 tQCS 的合作伙伴有两家都加入了 Rust 基金会银牌会员。分别是：
- [KDBA](https://www.kdab.com/) ：在嵌入式系统、3D 图形以及跨桌面、嵌入式和移动平台的工作方面拥有多年经验， KDAB 是 Qt 项目的主要贡献者。
- [Slint](https://slint-ui.com/): 极大地简化了取代 Qt 需求的嵌入式平台的 GUI 开发。支持 Rust/Cpp/Javascript ，有设计友好的 UI 标记语言。其创始人同样来自 Qt 项目主要贡献者，QtQml 引擎的主要开发者。

### 云存储： Dropbox

> 关键字：云存储

Dropbox 是最早使用 Rust 并取得成功的公司之一。Dropbox将 Rust 用于其部分文件同步引擎。以及一个新的视觉交流工具 [Dropbox Capture](https://www.dropbox.com/capture) ，旨在使团队能够轻松地使用屏幕记录、视频信息、屏幕截图或GIF来异步分享他们的工作。

###  边缘计算：Cloudflare

> 关键字：边缘计算、serverless

[Cloudflare](https://github.com/cloudflare) 在其核心边缘逻辑中使用 Rust 来替代内存不安全的 C。Cloudflare worker 支持 Rust 和 WebAssembly 。在今年 9 月份，Cloudflare 还宣布正在用 Rust 实现一款可以替代 Nginx 的代理服务器 [Pingora](https://blog.cloudflare.com/how-we-built-pingora-the-proxy-that-connects-cloudflare-to-the-internet/) 。


###  迪士尼公司（Walt Disney Company）

> 关键字：WebAssembly 、渲染引擎

迪士尼公司正在用 Rust 构建其  NCP GUI 框架，从[迪士尼的这一职位招聘信息](https://www.builtinnyc.com/job/engineer/lead-software-engineer/181881)中可以得出这一结论。从该公司 2021 年发布的信息[“介绍 Disney+ 应用程序开发工具包 (ADK)”](https://medium.com/disney-streaming/introducing-the-disney-application-development-kit-adk-ad85ca139073)来看， 使用 Rust 主要是构建代号为“m5”的 Native Client Platform v2 (NCPv2) 框架。他们选择了 Rust，以 [WebAssembly](https://webassembly.org/) (WASM) 为目标，以便在限制更新基于 C 的运行时的能力的任何固件更新周期之外简化 Web 部署和应用程序可更新性。该项目已经持续进行了快三年了，现在已经达到了从手持终端到电视，网页等全平台使用同一个渲染引擎来渲染它们的动画。


### 特斯拉

> 关键字：高性能机器人模拟器、固件验证

虽然[马斯克](https://twitter.com/elonmusk/status/1496293976692899843?lang=en)在今年2月份于推特上面宣称他是 Rust 语言的粉丝，同时也承认特斯拉主要使用 Cpp 和 Python 。但从今年11月份发布的两个 Rust 职位来看，特斯拉也开始采用了 Rust 。其中一个是[特斯拉机器人模拟引擎团队](https://www.theladders.com/job/rust-or-c-developer-software-engineer-tesla-bot-simulations-tesla-palo-alto-ca_60305636)的招聘，正在寻找 Rust 开发人员来扩展用 Rust 编写的高性能机器人模拟引擎。另外一个是 [Rust 固件验证工程师](https://www.tesla.com/careers/search/job/python-rust-c-firmware-validation-engineer-drive-systems-all-levels--98473) ，但该职位对于 Rust 的要求只是“有任何 Rust 经验者优先，但不是必需的”。


###  Tweedegolf  ： 与太空公司宇宙飞船

> 关键字：PTP、卫星、宇宙飞船、太空

这次 Rust 真的要上天了。[Gama](https://www.gamaspace.com/) 将发射太阳帆宇宙飞船🛰️，并且是公开将 Rust 送入太空的公司之一。提供软件服务的应该是这家公司：[Tweedegolf](https://tweedegolf.nl/en) ，该公司也是 Rust 基金会银牌会员。他们的[开源仓库](https://github.com/tweedegolf)里有一个 Rust 实现的 PTP (精确时间协议) 库，这个PTP一般用在卫星的时间源，比NTP更精确。但这个是 PoC 实现，不知道这次发射的飞船上有没有用。从另外的项目 嵌入式开发板 pcf85063a （一般用于计时闹钟）rust 驱动来看，这次上天的 Rust 程序很可能和精确计时相关。

[Gama 太阳帆的卫星于 2023 年 1 月 3 日由 SpaceX 猎鹰 9 号成功送入轨道](https://www.sail-world.com/news/257330/Gama-launches-its-Gama-Alpha-solar-sail-mission)。


### 荷兰 Lightyear 太阳能汽车公司采用 Rust 

> 荷兰Lightyear公司将在今年晚些时候开始向客户交付全球首款可量产的太阳能汽车

在 [Tweedegolf 公司的博客网站](https://tweedegolf.nl/nl/blog/76/pioneering-rust-high-tech)上透露，由 Lightyear 公司的软件架构师Jorrit 在 Tweedegolf 公司组织的[高科技行业 Rust 线下聚会](https://hightechsoftwarecluster.nl/evenementen/rustmeetup/)分享了 Lightyear 公司如何在Lightyear核心平台的开发中使用 Rust 。 可能是隐私原因，并没有放出该分享的视频和ppt资料。


###  文件数据存储： Qumulo

> 关键字：混合云文件数据管理

 Qumulo（混合云文件数据管理领域领导者） 和 西部数据 这两家公司是合作企业，通过部署基于西部数据UltrastarTM 大容量HDD和高性能SSD的Qumulo可扩展文件数据平台，IHME（健康指标与评估研究所）每天可处理高达2PB数据，推进公共流行病研究、统计和预测。 Qumulo  赞助了 RustConf 2022 大会。

###  老牌数据库公司： PostgreSQL

> 关键字：数据库、postgresql

 PostgreSQL 赞助了 RustConf 2022 大会，没有发现 PostgreSQL 公司内部有使用 Rust 的痕迹。但是在 GitHub 有一个致力于用 Rust 编写 PostgreSQL 扩展的项目 [pgx](https://github.com/tcdi/pgx)，其中核心开发者 [Ana 博客也有很多相关文章](https://hoverbear.org/tags/postgresql/)。

### 企业数据分析：Redjack

> 关键字：数据分析
 
Redjack 号称来自美国国家情报机构的技术，每年监控和保护超过 8% 的互联网公共 IP 空间和超过 100 万亿次商业通信，提高可操作的数据使组织能够提高分析的速度和准确性，从而实现大规模运营的安全性和弹性。Redjack 也赞助了 RustConf 2022 大会，以此推断 该公司也有采用 Rust 的可能性。


### 数据科学与人工智能

> 数据科学、AI

Rust 基金会银牌会员中也包括数据科学和人工智能领域的公司：
- [Watchful](https://www.watchful.io/)，以传统标签解决方案无法实现的速度和规模为 AI 标记数据。

### 汽车物联网

> 关键字： IoT

[Wyliodrin](https://wyliodrin.com/) 使用**Rust** , **Tock OS**和**Android**保护设备并构建安全高效的系统。将 Rust 嵌入式实时操作系统 [Tock OS](https://github.com/tock/tock) 推入商业应用中。该公司也加入了Rust 基金会银牌会员。

###  消息推送服务商：OneSignal

> 关键字：消息推送

 消息推送服务商 OneSignal 在 2017 年就开始使用 Rust 了，提供了 Rust Client 来支持推送通知、电子邮件、短信和应用内自助式客户参与解决方案。

### 自动化货运列车：Parallel Systems

> 关键字：货运自动化列车

自动化货运列车 Parallel Systems，相信货运的未来是铁路，所以研发了零排放的自动化电动货运跑在铁路上，Rust 语言是该公司技术栈的通用语言。该公司也赞助了 RustConf 2022 大会。 


### Rust 开发工具、平台与工具链支持

> 关键字：开发工具

基于 Rust 实现了一些好用的开发工具，比如：
- [tabnine](https://www.tabnine.com/)，一款基于机器学习的代码自动完成开发工具。
- [Open Source Security](https://opensrcsec.com/) ，该公司加入了Rust 基金会银牌会员，致力于为 Rust 生态推广做出贡献，目前主要是赞助 GCC Rust 的实现。截止到 2022 年 12 月，[GCC Rust 前端将在 GCC 13 中合并](https://www.phoronix.com/news/GCC-Rust-v4-Cleared-For-Landing)！
- [Embecosm](https://www.embecosm.com/) ，提供开源软件工具链和嵌入式操作系统服务。Embecosm 也是 GCC Rust 前端的赞助商。
- [grafbase](https://grafbase.com/)，构建和部署 GraphQL 后端的服务平台。
- [Rust for Linux](https://github.com/Rust-for-Linux)，Linux 6.1 内核版本[合并了初始的 Rust 基础设施](https://www.phoronix.com/news/Rust-Is-Merged-Linux-6.1)，为未来的内核驱动程序和其他内核代码启用 Rust 编程语言打好了基础。在 11 月 11 号，Rust for Linux 又提交了很多补丁代码到上游内核中。一旦所有这些 Rust 基础设施就位，我们将看到在更突出的现实世界驱动程序开始过渡到 Rust 代码之前需要多长时间，以获得新的硬件支持或在 Rust 中重写现有的 C 驱动程序代码。Rust 在 Linux 内核中的首批主要用户之一预计将是 Apple M1/M2 图形的 DRM 驱动程序。

### 安全监控

> 关键字： 资产安全、事件监控

该领域目前在 Rust 基金会银牌会员中包括以下公司：
- [Spectralops](https://spectralops.io/)，监控、分类和保护代码、资产和基础设施，以防止暴露的 API 密钥、令牌、凭证和高风险安全错误配置。
- [Sentry](https://sentry.io/welcome/)，应用程序监控平台。


### 软件咨询

> 关键字： 软件咨询

目前也涌现出一些 Rust 咨询公司，下面是加入 Rust 基金会银牌会员的公司：
- [knoldus](https://www.knoldus.com/)，
- [Ferrous Systems ](https://ferrous-systems.com/blog/ferrous-systems-adacore-joining-forces/) 
- [mainmatter](https://mainmatter.com/) 
- [Tag1](https://www.tag1consulting.com/) 

### 游戏 与 渲染引擎

> 关键字： 游戏

Rust 在游戏领域目前还在发展中。游戏公司动视暴雪作为普通赞助商加入了 Rust 基金会，并且在 2021 年发布了一份由动视暴雪旗下工作室 Treyarch 撰写的 [「用于游戏工具的 Rust 编程语言 」](https://www.activision.com/cdn/research/The_Rust_Programming_Language_for_Game_Tooling.pdf) 调研报告。 Treyarch 自 2018 年以来， 一直在逐步将 Rust 集成到我们的工具和管道中。

另外还有一家值得关注的游戏公司是 [Embark](https://www.embark-studios.com/)，该公司赞助了 Rust 游戏引擎 [Bevy](https://github.com/bevyengine/bevy) 和 [Fyrox](https://github.com/FyroxEngine/Fyrox)，并且开源了 [rust-gpu](https://github.com/EmbarkStudios/rust-gpu) 致力于使 Rust 成为 GPU 着色器的一流语言和生态系统。


### 电商

> 关键字：电商

Rust 也被用于电商领域。
- 美国最大的家具电商公司 Wayfair 旗下的开源项目 [Tremor](https://github.com/tremor-rs/tremor-runtime)，已经进入 CNCF。去年 九月份还召开了一次小型的线上的 [Tremor Conf]( https://community.cncf.io/events/details/cncf-tremor-community-presents-tremor-con-2021/) 。从2018年开始， tremor 就是跑在了 wayfair生产环境中，每天处理10兆字节的数据，或每分钟100亿条消息，每秒1000万个指标。tremor 降低了成本，减少了复杂性，巩固和简化了操作环境，以激发SRE的乐趣，减少NOC的工作量，并降低运营成本。[Rust 为 Wayfair 省掉数千个核心和TB级的内存的成本 ]( https://www.tremor.rs/slides/2020-03-31-RustAndTellBerlin-functions.pdf) 
- [cargurus](https://www.cargurus.com/) ，英国的一家二手车电商网站，也成为了 Rust 基金会普通赞助商成员。


### Web3  与 区块链

> 关键字：Web3 、同态加密、隐私计算、区块链、数字货币、零知识证明

Rust 在 Web3 和 区块链领域已经成为了主流语言。在这些领域耳熟能详的公司和项目很多：

- [Diem](https://github.com/diem/diem) ，前身叫 Libra ，曾经是 Facebook 的稳定币项目，但是现在已经被 Silvergate Capital Corporation 收购。
- 超新公链[aptoslabs](https://aptoslabs.com/) 和 [sui](https://sui.io/)，都是 Diem 团队成员离职创业的两个项目，它们的共同点是都使用 Rust 实现的 Move 语言作为智能合约语言。
- [parastate](https://www.parastate.io/)，波卡生态多链智能合约平台，是 Rust 基金会银牌会员。
- [Zama](https://www.zama.ai/)，为数据科学和AI构建开源同态加密解决方案，是 Rust 基金会银牌会员。
- [Keyrock](https://keyrock.eu/)  ，部署了专有且高度可扩展的数字资产做市技术，是 Rust 基金会银牌会员。
- [matter-labs](https://matter-labs.io/) ，扩展以太坊 [零知识证明](https://github.com/matter-labs/awesome-zero-knowledge-proofs/) 。
- 日本区块链技术孵化公司 [TECHFUND](https://techfund.jp/en) ，也加入了 Rust 基金会银牌会员。
- 其他。


## 本节小结

Rust 是一门通用的语言，并且多样化也是 Rust 语言的设计原则之一。本文试图通过罗列 Rust 在各个领域的成功应用案例，来帮助人们了解 Rust 适合落地的业务场景。然而，本文远远未能覆盖 Rust 应用的全部角落，还有我们看不到的地方，正在默默地采用 Rust 。本文也几乎没有罗列国内使用 Rust 的公司，但国内也有公司准备逐步采用 Rust ，只是进展比较慢。

> P.S 你也可以在 GitHub 上查看别人维护的全球范围内[使用 Rust 的公司列表](https://github.com/omarabid/rust-companies)。

Rust 就像一阵“春雨”，随风潜入夜，润物细无声。感谢阅读。

---

# Rust 安全参考 | 2022 年 Rust 安全漏洞分类盘点

本节内容是对 [Rust 安全数据库](https://rustsec.org/ ) 中记录的 Rust 及其生态库安全问题的梳理。希望可以对广大 Rust 开发者的代码安全性有所启发。

## 漏洞分类

Rust 安全数据库中记录的安全问题分为两大类：安全漏洞（Vulnerability）和非健全(Unsound)问题。

安全漏洞又具体分为以下几类：
-   代码执行（Code Execution）
-   内存损坏（Memory Corruption）
-   权限提升（Privilege Escalation，在操作系统级别或应用程序/库内部）
-   文件泄露/目录遍历（File Disclosure / Directory Traversal）
-   网络安全（Web Security，例如 XSS、CSRF）
-   格式注入（Format Injection），例如 shell 转义、SQL 注入（以及 XSS）
-   加密失败（Cryptography Failure，例如机密性破坏、完整性破坏、密钥泄漏）
-   隐蔽通道（例如 Spectre、Meltdown）
-   代码中的恐慌（panic）标榜为“panic-free”（特别是如果对网络 DoS 攻击有用）
- 内存暴露（memory-exposure）
- 线程安全（thread-safety）

此外，RustSec 还会对生态库的[健全性](https://rust-lang.github.io/unsafe-code-guidelines/glossary.html#soundness-of-code--of-a-library) 进行跟踪，而不管它们是否是漏洞。 因为 [当使用来自安全代码的 crate 可能导致未定义行为](https://doc.rust-lang.org/reference/behavior-considered-undefined.html)时，往往伴随着健全性问题。

> 健全性（Soundness）是一个类型系统概念（实际上源于逻辑学研究），意味着类型系统在某种意义上是“正确的”，即类型良好的程序实际上具有所需的属性。对于 Rust，这意味着类型良好的程序不会导致[未定义的行为](https://rust-lang.github.io/unsafe-code-guidelines/glossary.html#undefined-behavior)。然而，这个承诺只适用于安全代码；对于`unsafe`代码，由程序员来维护这份契约。

对于安全漏洞或非健全问题发生的原因或机制，RustSec 则使用关键字来进行标识。但是 RustSec 的关键字太多了，所以我对关键字也进一步做了一个分类。

| 分类                                                               | 漏洞机制                             | 备注                                                                                                                                                                                                                                      | 类型                         |
| ------------------------------------------------------------------ | ------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------- |
| [memory safety](https://rustsec.org/keywords/memory-safety.html)   | alias （多个可变借用）               | 2022 年还未见有该漏洞                                                                                                                                                                                                                     | 漏洞                         |
|                                                                    | double free                          | 2022 年还未见有该漏洞                                                                                                                                                                                                                     |                              |
| [use-after-free](https://rustsec.org/keywords/use-after-free.html) | incorrect-lifetime                   | 2022 年 一例 [RUSTSEC-2022-0028: Vulnerability in neon](https://rustsec.org/advisories/RUSTSEC-2022-0028.html)                                                                                                                            | 漏洞                         |
|                                                                    | wasm                                 | 2022 年 一例 [RUSTSEC-2022-0016: Vulnerability in wasmtime](https://rustsec.org/advisories/RUSTSEC-2022-0016.html)                                                                                                                        | 漏洞                         |
|                                                                    | segfault                             | 2022 年 一例 [RUSTSEC-2022-0002: Vulnerability in dashmap](https://rustsec.org/advisories/RUSTSEC-2022-0002.html)                                                                                                                         | 漏洞                         |
| memory-layout                                                      | cast                                 | 2022 年 一例  [RUSTSEC-2022-0052: Unsoundness in os_socketaddr](https://rustsec.org/advisories/RUSTSEC-2022-0052.html)                                                                                                                    | Unsound                      |
|                                                                    | cell                                 | 2022 年 一例 [RUSTSEC-2020-0164: Unsoundness in cell-project](https://rustsec.org/advisories/RUSTSEC-2020-0164.html)                                                                                                                      | Unsound                      |
| [ddos](https://rustsec.org/keywords/ddos.html)                     | oom                                  | 2022 年两例  [RUSTSEC-2022-0055: Vulnerability in axum-core](https://rustsec.org/advisories/RUSTSEC-2022-0055.html)  和 [RUSTSEC-2022-0035: Vulnerability in websocket](https://rustsec.org/advisories/RUSTSEC-2022-0035.html)            | 漏洞                         |
|                                                                    | untrust data                         | 2022 年一例  [RUSTSEC-2021-0143: Vulnerability in kamadak-exif](https://rustsec.org/advisories/RUSTSEC-2021-0143.html)                                                                                                                    | 漏洞 CVSS分 6.5 MEDIUM       |
| directory-traversal                                                | Windows                              | 2022 年 两例： [RUSTSEC-2022-0069: Vulnerability in hyper-staticfile](https://rustsec.org/advisories/RUSTSEC-2022-0069.html)  和  [RUSTSEC-2022-0043: Vulnerability in tower-http](https://rustsec.org/advisories/RUSTSEC-2022-0043.html) | 漏洞                         |
| html                                                               | xss                                  | 2022 年一例 [RUSTSEC-2022-0003: Vulnerability in ammonia](https://rustsec.org/advisories/RUSTSEC-2022-0003.html)                                                                                                                          | 漏洞                         |
| integer-overflow                                                   | out-of-bounds                        | 2022 年一例 [RUSTSEC-2022-0051: Vulnerability in lz4-sys](https://rustsec.org/advisories/RUSTSEC-2022-0051.html)                                                                                                                          | 漏洞 CVSS Score 9.8 CRITICAL |
| out-of-bounds-read                                                 | out-of-bounds-read                   | 2022 年一例 [RUSTSEC-2022-0046: Vulnerability in rocksdb](https://rustsec.org/advisories/RUSTSEC-2022-0046.html)                                                                                                                          | 漏洞                         |
| side-channel                                                       | timing-attack                        | 2022 年一例 [RUSTSEC-2022-0018: Vulnerability in totp-rs](https://rustsec.org/advisories/RUSTSEC-2022-0018.html)                                                                                                                          | 漏洞 CVSS Score 4.2 MEDIUM   |
| stack-overflow                                                     | stack-overflow                       | 2022 年一例 [RUSTSEC-2022-0004: Vulnerability in rustc-serialize](https://rustsec.org/advisories/RUSTSEC-2022-0004.html)                                                                                                                  | 漏洞                         |
| subtype                                                            | variance/cell                        | 2022 年一例  [RUSTSEC-2020-0164: Unsoundness in cell-project](https://rustsec.org/advisories/RUSTSEC-2020-0164.html)                                                                                                                      | Unsound                      |
| type-confusion                                                     | type-confusion                       | 2022 年一例 [RUSTSEC-2020-0165: Unsoundness in mozjpeg](https://rustsec.org/advisories/RUSTSEC-2020-0165.html)                                                                                                                            | Unsound                      |
| typosquatting                                                      | typosquatting （恶意伪造同名 crate） | 2022 年一例 [RUSTSEC-2022-0042: Vulnerability in rustdecimal](https://rustsec.org/advisories/RUSTSEC-2022-0042.html)                                                                                                                      | 漏洞                         |
| unaligned-read                                                     | windows                              | 20222 年一例  [RUSTSEC-2021-0145: Unsoundness in atty](https://rustsec.org/advisories/RUSTSEC-2021-0145.html)                                                                                                                             | Unsound                      |
| uninitialized-memory                                               | uninitialized-memory                 | 20222 年两例   [RUSTSEC-2022-0067: Unsoundness in lzf](https://rustsec.org/advisories/RUSTSEC-2022-0067.html) 和 [RUSTSEC-2018-0022: Vulnerability in temporary](https://rustsec.org/advisories/RUSTSEC-2018-0022.html)                   | Unsound 和 漏洞              |
| unsound                                                            | covariant                            | 2022 年一例  [RUSTSEC-2022-0007: Unsoundness in qcell](https://rustsec.org/advisories/RUSTSEC-2022-0007.html)                                                                                                                             | Unsound                      |

> 注：CVSS 即通用漏洞评分系统，参见文后安全术语介绍部分。

**CVSS 危害级别划分**：
1.  分值范围 `[0.1 - 3.9]`  –>  低危害性 
2.  分值范围  `[4.0 - 6.9]` –>  中危害性 
3.  分值范围 `[7 - 10]`  -> 高危害性 


## 2022 年漏洞分类排行 Top 3

按出现漏洞次数由多到少的漏洞分类排行：
- [内存损坏](https://rustsec.org/categories/memory-corruption.html) ，2022 年一共出现 19 个此类安全问题。包括一个严重危害等级的漏洞和一个高危害等级的漏洞。导致内存损坏的 Bug  包括：整数溢出、越界访问、数据竞争（无锁并发内存顺序指定错误）、Unsafe Rust 中未做边界验证、Use-After-Free 等。
- [拒绝服务](https://rustsec.org/categories/denial-of-service.html)，2022 年一共出现 14个此类安全问题。包括五个高危害等级的漏洞。导致内存损坏的 Bug  包括：缓冲区溢出、未验证请求长度、深度嵌套、栈溢出、资源泄露、无限循环等。
- [内存暴露](https://rustsec.org/categories/memory-exposure.html)  ，2022 年一共出现 9 个此类安全问题。导致该问题的 Bug 包括：越界读取（验证不充分）、Use-After-Free 、使用未初始化内存、悬垂指针等。



## 2022 年安全漏洞摘要介绍


###   内存相关漏洞


#### RUSTSEC-2022-0002： dashmap 中的引用出现 UAF

由Ref（和类似类型）的一些方法返回的引用可能会超过Ref并逃脱锁。这将导致未定义的行为，并可能导致一个段错误。

- [https://rustsec.org/advisories/RUSTSEC-2022-0002.html](https://rustsec.org/advisories/RUSTSEC-2022-0002.html)
- [https://github.com/xacrimon/dashmap/issues/167](https://github.com/xacrimon/dashmap/issues/167)

#### RUSTSEC-2022-0008： Windows-rs 中 Delegate 函数缺乏 `Send` 限定

- [https://rustsec.org/advisories/RUSTSEC-2022-0008.html](https://rustsec.org/advisories/RUSTSEC-2022-0008.html)
- [https://github.com/microsoft/windows-rs/issues/1409](https://github.com/microsoft/windows-rs/issues/1409)

#### RUSTSEC-2022-0012: Arrow2 在 Safe 代码中出现双重释放（double-free）

`Ffi_ArrowArray` 结构体错误实现 `#derive(Clone)` ，因为它是一个 FFi 绑定，实现 Clone 会导致出现两份指针，从而导致双重释放。

- [https://github.com/jorgecarleitao/arrow2/issues/880](https://github.com/jorgecarleitao/arrow2/issues/880)
- [https://rustsec.org/advisories/RUSTSEC-2022-0012.html](https://rustsec.org/advisories/RUSTSEC-2022-0012.html)

#### RUSTSEC-2022-0003: ammonia 中存在格式化注入漏洞

`clean_text`中错误映射 HTML 的 Form Feed，导致注入漏洞。

```rust
let html = format!("<div title={}>", clean_text(user_supplied_string));
```

- [https://github.com/rust-ammonia/ammonia/pull/147](https://github.com/rust-ammonia/ammonia/pull/147)

#### RUSTSEC-2022-0006: `thread_local` crate 中的 `RawIter::next` 存在数据竞争

主要是因为内存顺序指定错误而引起的，解决起来也比较简单，修改为正确的内存顺序即可。

- [https://rustsec.org/advisories/RUSTSEC-2022-0006.html](https://rustsec.org/advisories/RUSTSEC-2022-0006.html)
- [https://github.com/Amanieu/thread_local-rs/issues/33](https://github.com/Amanieu/thread_local-rs/issues/33)

#### RUSTSEC-2022-0016： `wasmtime` 的 `externref` 在启用 `epoch` 中断时会导致 UAF

epoch 中断会导致 wasmtime 在执行 GC 时错误回收还在使用的内存，从而导致 UAF。

- [https://github.com/bytecodealliance/wasmtime/security/advisories/GHSA-gwc9-348x-qwv2](https://github.com/bytecodealliance/wasmtime/security/advisories/GHSA-gwc9-348x-qwv2)
- [https://rustsec.org/advisories/RUSTSEC-2022-0016.html](https://rustsec.org/advisories/RUSTSEC-2022-0016.html)

###  DoS 漏洞

#### RUSTSEC-2022-0004： `rustc_serialize` 解析深度嵌套的 JSON 时栈溢出

该漏洞会导致 DoS（denial-of-service）风险。

```rust
// 触发漏洞示例代码
fn main() {
    let _ = rustc_serialize::json::Json::from_str(&"[0,[".repeat(10000));
}
```

推荐使用 serde 作为 rustc_serialize 的替代品。

[https://rustsec.org/advisories/RUSTSEC-2022-0004.html](https://rustsec.org/advisories/RUSTSEC-2022-0004.html)



### Unsound


#### RUSTSEC-2022-0007: qcell crate 中 `TCell` 或 `TLCell` 的内存能被恶意代码访问

因为生命周期参数型变未使用正确而引起的问题，导致恶意代码可以对同一片内存获取两个可变引用。解决方法是把类型参数的协变（Covariant）改为不变（Invariant）。

```rust
struct Invariant<T>(fn(T) -> T);

pub struct TCellOwner<Q: 'static> {
    // Allow Send and Sync, and Q is invariant
    typ: PhantomData<Invariant<Q>>,
}

pub struct TCell<Q, T: ?Sized> {
    // use Invariant<Q> for invariant parameter, not influencing
    // other auto-traits, e.g. UnwindSafe (unlike other solutions like `*mut Q` or `Cell<Q>`)
    owner: PhantomData<Invariant<Q>>,
    // It's fine to Send a TCell to a different thread if the containted
    // type is Send, because you can only send something if nothing
    // borrows it, so nothing can be accessing its contents.
    //
    // `UnsafeCell` disables `Sync` and already gives the right `Send` implementation.
    // `Sync` is re-enabled below under certain conditions.
    value: UnsafeCell<T>,
}
```

- [https://rustsec.org/advisories/RUSTSEC-2022-0007.html](https://rustsec.org/advisories/RUSTSEC-2022-0007.html)
- [https://github.com/uazu/qcell/issues/20](https://github.com/uazu/qcell/issues/20)


#### RUSTSEC-2022-0010：Enum错误实现 trait时 enum_map 宏可能会导致 UB

`enum_map!`受影响版本在使用宏时未正确检查枚举的长度，信任用户提供的长度。

当`Enum` trait 中的 `LENGTH` 与 `EnumArray` trait 中的数组长度不匹配 时，可能会导致枚举映射初始化为未初始化的类型，进而允许攻击者执行任意代码。

这个问题只能在手动实现 Enum trait 时发生，它永远不会发生在使用#[derive(Enum)].

触发此漏洞的示例代码如下所示：

```rust
enum E {
    A,
    B,
    C,
}

impl Enum for E {
    // LENGTH 长度不等于 EnumArray 长度
    const LENGTH: usize = 2;

    fn from_usize(value: usize) -> E {
        match value {
            0 => E::A,
            1 => E::B,
            2 => E::C,
            _ => unimplemented!(),
        }
    }

    fn into_usize(self) -> usize {
        self as usize
    }
}

impl<V> EnumArray<V> for E {
    type Array = [V; 3];
}

let _map: EnumMap<E, String> = enum_map! { _ => "Hello, world!".into() };
```

- [https://rustsec.org/advisories/RUSTSEC-2022-0010.html](https://rustsec.org/advisories/RUSTSEC-2022-0010.html)
- [https://gitlab.com/KonradBorowski/enum-map/-/blob/master/CHANGELOG.md#version-202](https://gitlab.com/KonradBorowski/enum-map/-/blob/master/CHANGELOG.md#version-202)



##  Rust 官方安全通告

### Cargo 安全公告

在 2022 年 9月份，Rust 安全响应工作组被告知 Cargo 没有阻止提取从备用注册表下载的一些格式错误的包。  当 Cargo 下载包时，能够将包上传到备用注册表 的 攻击者可能会填满文件系统或损坏任意文件。这些问题已分配给 CVE-2022-36113 和 CVE-2022-36114。这些漏洞的严重性对于备用注册表的用户来说是“低”的。 依赖[crates.io](http://crates.io/)的用户不受影响。

- 任意文件损坏 (CVE-2022-36113)。 Cargo 允许包包含一个 `.cargo-ok`  *符号链接*，Cargo 将提取该链接。然后，当 Cargo 尝试将 “ok”写入“.cargo-ok”时，它实际上会将符号链接指向的文件的前两个字节替换为“ok”。这将允许攻击者使用 Cargo 提取包来破坏机器上的一个文件。
- 磁盘空间耗尽 (CVE-2022-36114)。Cargo 没有限制从压缩档案中提取的数据量。 攻击者可以将一个特制的包 上传到备用注册表，该 包提取的数据远远超过其大小（也称为 “zip 炸弹”），使用 Cargo 耗尽计算机上的磁盘空间下载包。

这两个漏洞都存在于 Cargo 的所有版本中。Rust 1.64  已包括对它们的修复。

### Regex 安全公告

在 2022 年 3月份，Rust 安全响应工作组被告知 `regex` 包没有正确限制它解析的正则表达式 (regex) 的复杂性。攻击者可以利用此安全问题执行拒绝服务，方法是  
将特制的正则表达式发送到接受不受信任的正则表达式的服务。使用受信任的正则表达式解析不受信任的输入时，不存在已知漏洞 。 此问题已分配为 CVE-2022-24713。当 `regex` 包用于解析不受信任的正则表达式时，此漏洞的严重性 为“高”。`regex` crate 的其他用途 不受此漏洞影响。

建议使用  regex 1.5.5 版本及之上的版本。

## 安全术语介绍

[CVSS 通用漏洞评分系统](https://www.first.org/cvss/) (Common Vulnerability Scoring System, CVSS)。旨在评估安全漏洞的严重性，是全球各组织使用的公开标准。该标准由FIRST制定，并由其组织团队SIG（The CVSS Special Interest Group）改进和推广。

通过漏洞难易程度以及对机密性、完整性、可用性的影响综合评估后，生成一个0到10分之间的评分值，此分值即是CVSS得分。CVSS 主要用于评估漏洞的严重性，而不是对风险的评估。风险评分是需要每个企业根据企业特性的风险要素，进行识别后再进行风险判别。

CVSS 通过三个方面进行评估：
- **基础得分(Base Score)**：根据漏洞的固有特征反映漏洞的严重程度，不受时间因素影响，并假定在不同部署环境中产生合理的最坏情况的影响；
- **时间得分(Temporal Score)**：评价漏洞被利用的时间窗的风险大小，比如官方发布了补丁则会降低评估分数；
- **环境得分(Environment Score)**：需要在特定环境下评估。通常由最终用户根据自己的使用环境给出。
使用业界通用的CVSS标准需遵循以下原则：
1. 一般使用CVSS基础得分进行漏洞严重等级评估；
2. 评估时必须基于攻击场景，且攻击后能对系统造成了机密性、完整性、可用性的影响；
3. 有多个攻击场景时，最终得分选择最高得分场景；
4. 被嵌入调用的库存在漏洞，要根据该库在产品中的使用方式，确定漏洞的攻击场景后进行评估；
5. 不考虑攻击目标的环境缓解措施（如设置防火墙），以体现漏洞真实严重程度；
6. 不考虑特定配置，即如果攻击成功需要特定的配置则在该配置存在的情况下进行评分；
7. 安全缺陷不能被触发的场景或不影响CIA（机密性/完整性/可用性），CVSS评分为0分。


---

# Rust 2022 开源项目盘点

Rust 语言是开源的，其生态中开源项目也是必不可少的一部分。Rust 语言也是通用的，其应用覆盖诸多领域，我们将从以下几个领域来进行盘点。

- crates 行业系数（Industry Coefficient）
- 操作系统
- 数据库与数据分析
- 网络服务
- Web开发
- 云原生
- 游戏
- 工具
- 图形渲染和处理
- UI
- 游戏
- 人工智能
- 物联网与嵌入式
- 编程语言

本文分类梳理的开源项目，只是选举 Rust 生态中各个领域具有代表性和有潜力的项目，以此来观察 Rust 生态的发展。实际上，在撰写本文时，crates.io 上发布的 crate 数量已经达到了 10 万个，在 GitHub 上面的 Rust 开源项目也是不计其数，在 GitLab 社区也有很多的 Rust 开源项目，本文不可能罗列那么全，选取的项目仅供大家参考。


## crates 行业系数（Industry Coefficient）

David Tolnay 根据 crates.io 中 crate 下载量统计了 crates 行业系数，从侧面反应 Rust crate 的应用状况。

行业系数的计算公式为：周二至周四下载量/周末下载量 - 总体平均水平（周一和周五有跨时区问题，所以未参与统计）

这个行业系数表明，如果一个 crate 在 工作日（周二到周四） 经常被下载，则系数为正，如果在 周末 经常被下载，则系数为负。比如，Serde 的工作日下载量与周末下载量的比率几乎与 crates-io 的总体比率相同。Prost 在工作日的下载量比例较大，而在周末较小，因为没有人在周末做 protobuf 相关的东西。周末被认为是 Rust 爱好者在“玩” Rust。

下图罗列了 （9月份统计结果）90 天内超过 100 万下载量的某些 crate 系数。

![crates](./images/crates.png)

从图中系数简单地得出一个粗略笼统的结论，仅供参考：
- cxx 是 Rust 和 Cpp 安全交互的库，工作日用的比较多，说明 Rust 目前在 Cpp 生态上非常活跃。实际上，在 Android 代码中 Cxx 用的很多。
- 网络服务库和 Web 框架，比如tokio和axum ，在工作日用的也比较多，说明 Rust 在网络服务和 Web 领域存在一定应用。
- wasi 在工作日用的比较多，从侧面说明，Rust 和 WebAssembly 的应用领域主要集中在 Sever Side 。现实也是如此，WebAssembly 在 Server Side 的 Severless 领域在今年得到了很大的发展。

这是统计相关代码：[https://github.com/dtolnay/db-dump/blob/master/examples/industry-coefficient.rs](https://github.com/dtolnay/db-dump/blob/master/examples/industry-coefficient.rs)  ，感兴趣可以自行执行代码进行统计。


## 操作系统


### Rust for linux  支持状况

Linus Torvalds于 2022 年 12 月 11 日[发布了](https://lore.kernel.org/lkml/CAHk-=wj_HcgFZNyZHTLJ7qC2613zphKDtLh6ndciwopZRfH0aQ@mail.gmail.com/T/#u)Linux Kernel 6.1，作为 2022 年的最终主线内核版本。出于多种原因，这个版本很重要。也许最重要的是在未来几天内，主线内核中对 Rust 语言的初始支持，以获得更好的安全性和内存安全代码。越是从 C 转向 Rust，这势必越会减少内核漏洞的数量。

Linux Kernel 6.1 中最重要的变化是引入了[初始的 Rust 框架代码](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=8aebac82933ff1a7c8eede18cab11e1115e2062b)。高达 12k 行的代码仅带来了 Rust 的基本基础设施。有了这个基础，新的驱动程序、子系统和内核模块有望通过 Rust 编程语言登陆内核。 

主要支持包括以下四个方面：

-   内核内部
-   Rust 构建规则和脚本
-   Rust crates 和 bindings 以尽可能减少构建
-   文档和 Rust 示例

一直领导 Rust for Linux 工作的 Miguel Ojeda 在11月份又发出了一组 28 个补丁，为内核提供了更多的 Rust 核心添加。很可能会在 Linux 6.2 合并窗口中及时看到这项工作。

Miguel （Rust for linux 核心开发者）对 2023 年 Rust-for-Linux 的期望：

-  Rust 没有被踢出内核  ;-)
- 更多的人致力于 Rust 驱动程序
- 拥有第一个生产级用户
- 稳定更多内核库中用到的 Rust 不稳定特性
- 更多内核人员拥抱 Rust


### 嵌入式安全操作系统 TockOS 2.1 发布

[TockOS 2.1 发布](https://github.com/tock/tock/blob/master/CHANGELOG.md) 。 在 TockOS 迈向 2.0 时，许多核心的内核API被重新设计和重写。并且支持11个新的硬件平台，包括 RISC-V。

TockOS 的贡献者之一 Alexandru ，创办了 [OxidOS](https://oxidos.io/) 公司，为汽车软件OEM和开发商提供安全操作系统和开发工具。


### Redox 发布 0.8 版

[Redox 在今年发布了 0.8 版](https://www.redox-os.org/news/release-0.8.0/) 。该版本确保真正的硬件正常工作，添加了 i686 支持，启用了音频和初步多显示器支持等功能，并且简化了引导和安装基础结构并使其更加健壮。

0.8 的一些重要改进摘要：
- [Redox Book 内容大量更新](https://doc.redox-os.org/book/)，该书介绍了如何构建和使用 RedoxOS
- 添加了对 i686（奔腾 II 及更高版本的 32 位 x86）的支持，并且通常可以在真实硬件上运行
- 改进了对 aarch64（64 位 ARM）的支持，并且正在启动以登录 QEMU。真正的硬件还不能工作
- 现在普遍支持音频
- BIOS 和 EFI 映像已合并，一个安装可以在任何一个上启动
- clone 和 exec 系统调用已移至用户空间。此更改还涉及 [bootstrap](https://gitlab.redox-os.org/redox-os/bootstrap)和 [escalated](https://gitlab.redox-os.org/redox-os/escalated)的引入。`bootstrap`是一个非常简单的链接程序，内核加载到用户空间，然后可以处理加载 ELF 文件，例如`init`. 为 .等程序`escalated`提供支持。`setuid``sudo`
- 使用[redox-daemon crate](https://gitlab.redox-os.org/redox-os/redox-daemon) 来简化守护进程的设置
- 更新大多数存储库上的 cargo lock 文件

另外一件有趣的事是，Redox OS 在今年收到了一笔多达 400,000 美元的匿名捐款。匿名的方式使得目前无法使用。目前，Redox 作者正在与一个法律团队合作，具体确定 [OFAC 对 Tornado Cash 的制裁](https://home.treasury.gov/news/press-releases/jy0916)如何 适用于通过 Tornado Cash （米国数字货币交易平台）进行的这笔捐赠。目前，由于作者是米国公民，目前已阻止这笔捐款的转移，以遵守可能的 OFAC 制裁。如果作者被允许使用这笔捐款，他将在另一篇文章中描述它对 Redox OS 的意义。

###  KataOS ： 用于进行机器学习的嵌入式设备的操作系统

[谷歌今年宣布发布 KataOS](https://opensource.googleblog.com/2022/10/announcing-kataos-and-sparrow.html)，它是用于进行机器学习的嵌入式设备的操作系统。KataOS 从设计上就具备安全考虑，不但几乎完全是由 Rust 实现的，而且是建立在 seL4 微内核的基础之上，seL4 在数学上被证明是安全的，具有保证保密性、完整性和可用性。

KataOS 提供了一个可验证的安全平台来保护用户的隐私，因为应用程序在逻辑上不可能破坏内核的硬件安全保护，并且系统组件是可验证的安全。KataOS 也几乎完全用Rust实现，它为软件安全提供了一个强大的起点，因为它消除了整类错误，例如差一错误和缓冲区溢出。  
  
当前的 GitHub 版本包括大部分 KataOS 核心部分，包括用于 Rust 的框架（例如 sel4-sys crate，它提供 seL4 系统调用 API），一个用 Rust 编写的备用根服务器（动态系统范围的内存管理需要） )，以及内核对 seL4 的修改，可以回收根服务器使用的内存。[此外还与Antmicro](https://antmicro.com/platforms/renode/)合作，通过 Renode 为目标硬件启用 GDB 调试和模拟。   
  
为了全面证明一个安全的环境系统，团队还为 KataOS 构建了一个名为 Sparrow 的参考实现，它将 KataOS 与一个安全的硬件平台相结合。因此，除了逻辑上安全的操作系统内核之外，Sparrow 还包括一个逻辑上安全的信任根，它是在 RISC-V 架构上使用[OpenTitan构建的。](https://opentitan.org/)然而，对于我们的初始版本，我们的目标是使用 QEMU 模拟运行的更标准的 64 位 ARM 平台。  
  
最终目标是开源所有 Sparrow，包括所有硬件和软件设计。目前，仅[在 GitHub 上发布 KataOS](https://github.com/AmbiML/sparrow-manifest)的早期版本。


### dora-rs： 机器人中间件项目

[dora](https://github.com/dora-rs/dora) 是一个基于 Rust 的机器人框架，目标是成为一个低延迟、可组合和分布式的面向 SDV 和 无人驾驶的数据流计算平台。，旨在比当前机器人应用标准 ROS/ROS 2 好 10 倍，成为 ROS/ROS2/Autosar 的替代者。

Rust-os Blog的作者 Philip Opperman是 dora 主力开发者之一 。

dora 通信层暂时依赖于 [eclipse-zenoh/zenoh](https://github.com/eclipse-zenoh/zenoh)，关于zenoh 的介绍可以参考文章 [开源产品 | eclipse zenoh 助力雾计算和边缘计算](https://rustmagazine.github.io/rust_magazine_2021/chapter_4/zenoh.html)。[dora-rs 的通信层正在被重新设计](https://github.com/dora-rs/dora/pull/162)，目标是将数据面的控制和传输技术分离，比如算子都在一台机器部署的时候，就会用共享内存，这样延时很低。

更多文档参考：[https://dora-rs.github.io/dora/](https://dora-rs.github.io/dora/)

并且还配套有基于dora的自动驾驶入门套件 [dora-drives](https://github.com/dora-rs/dora-drives)。

虽然是早期项目，但发展不错，目前正在加入开放原子基金会的过程中，并且在 2023 年春季会基于 dora 开展国际智能驾驶大赛（Openatom Carsmos全球开源自动驾驶算法大赛）。

### drone-os： 嵌入式操作系统

[drone-os](https://github.com/drone-os) 是 嵌入式操作系统，旨在将不影响性能的现代开发方法带入嵌入式编程领域。开发者来自乌克兰，在 2022 年局势动荡下更新不多但是还在维护中，看上去工作重点在 Raspberry Pi Pico (RP2040) 的支持上面。

**DroneOS 遵循以下设计原则**

-   低能耗。Drone 鼓励中断驱动的执行模型。
-   硬实时。Drone 依赖于原子操作而不是使用临界区。
-   具有严格优先级的完全抢占式多任务处理。优先级较高的任务优先，延迟最小。
-   高并发。遵循 Rust 的 Fearless Concurrency 原则，多任务既便宜又安全。
-   消息传递并发。Drone 附带开箱即用的同步原语。
-   启用动态内存。Drone 让您可以使用方便的数据结构，如可变字符串或Vector，同时仍然保持确定性和代码效率。


### ros2_rust: ROS2 的 Rust 绑定

[ros2_rust](https://github.com/ros2-rust/ros2_rust) 是一个用于编写与 ROS 2 集成的 Rust 机器人应用程序的库。ROS 2 是一个流行的开源机器人框架，用于各种领域（自动驾驶汽车、无人机、人形机器人等）。

ros2_rust 旨在使开发人员能够使用 Rust 编写 ROS 2 应用程序。目前尚未达到与 C++ 和 Python ROS 2 库同等的功能，但正在努力实现这一目标。

该库今年发布到了 0.3 版本。

随着 Rust for Linux 进入 Linux 6.1 ，[Brandon Minor ](https://www.therobotreport.com/linux-embracing-rust-will-boost-robotics-community/) （传感器融合公司[Tangram Vision](https://www.tangramvision.com/)的创始人兼CEO）认为这将对机器人社区起到巨大的推动作用。

> 他如是说：“有一个巨大的机器人工具和范例生态系统，如[ROS](https://www.ros.org/)和[OpenCV](https://opencv.org/)，它们在 Linux 生态系统中运行得最好，不管喜欢与否，大多数机器人工程师都开始在这些沙箱中尝试。然而，我可以证明机器人领域越来越多的工程师认识到需要更强大、更可靠的软件，并正在寻找替代解决方案。那些这样做的人往往会[转向 Rust](https://www.tangramvision.com/blog/why-rust-for-robots)。这导致了一个充满热情的开发人员的新兴机器人生态系统，他们只想用周围[最受欢迎的编程语言](https://survey.stackoverflow.co/2022/#section-most-loved-dreaded-and-wanted-programming-scripting-and-markup-languages)编写更好的工具。尽管这些开发人员可能很热情，但这些工具大体上还没有准备好迎接黄金时段。它们缺少大多数工程师认为理所当然的功能，或者没有得到足够大的社区的信任。在旧工具、新编程语言和自动化兴起之间，机器人技术正处于变革时期。将 Rust 包含到 Linux 内核中似乎只是一个小细节，但它来得正是时候。多年来，机器人社区一直在推动 Rust 的发展；对于 Linux 来说，支持这些努力并被这些努力所支持是一股托起所有船只的潮流“。

[`https://robotics.rs/`](https://robotics.rs/) 该网站记录了 Rust 在开源机器人解决方案方向的开源库。


### Aero：现代、实验性的类 Unix 操作系统

[Aero](https://github.com/Andy-Python-Programmer/aero) 灵感来自于 Linux 内核，遵循宏内核设计。支持现代 PC 特性，如 长模式、5级分页和SMP（多核）。Aero 并非一个 Linux 发行版，它运行自己的内核，不与 Linux 内核共享任何源码或二进制文件。

### Rust 与 NuttX 操作系统

Apache NuttX 是一个实时嵌入式操作系统 RTOS，可在许多平台（如：8 位到 64 位平台）上移植，并且像 Linux 的小型版本一样工作（因为它符合 POSIX 标准）。现在，我们可以在 NuttX 上使用 Rust 创建更安全的嵌入式应用程序，也可以定制自己的驱动程序。[详细请参考文章：https://lupyuen.github.io/articles/rust2](https://lupyuen.github.io/articles/rust2) 。


### 将Rust的std移植到 rustix 上

[Rustix](https://github.com/bytecodealliance/rustix) 是一个具有多个后端的系统调用封装库。它有一个原始的Linux系统调用后端，以及一个libc后端，其他后端也在开发中。Rustix是为内存安全、I/O安全和性能而设计的。

将std移植到rustix的第一个原因是rustix从std中剔除了很多不安全的块。与操作系统的对话仍然需要不安全，但在rustix中，Unsafe 块被集中在单个系统调用上。Rustix还为系统调用提供了地道的 Result 错误处理。它还使用了Rust引用和切片，而不是原始指针。这些都使得阅读std的代码更加容易，并专注于系统调用的重要语义，而不会受到libc API机制的干扰。

rustix 也是向Linux上不依赖libc的Rust工具链迈出的一步。Rustix能够从Rust代码中直接调用Linux系统。

###  Aya :  专注于可操作性和开发者体验的 eBPF  Rust 库

[aya](https://github.com/aya-rs/aya) 不依赖于[libbpf](https://github.com/libbpf/libbpf)或[bcc](https://github.com/iovisor/bcc) 。它完全是用 Rust 从头开始构建的，只使用[libc](https://docs.rs/libc) crate 来执行系统调用。借助 BTF 支持并与 musl 链接，它提供了真正的[一次编译，随处运行的解决方案](https://facebookmicrosites.github.io/bpf/blog/2020/02/19/bpf-portability-and-co-re.html)，其中一个独立的二进制文件可以部署在许多 linux 发行版和内核版本上。在大多数环境中，Rust Nightly 是构建所需的唯一依赖项。rustc 不公开其内部 LLVM.so 库（即 aarch64）的某些环境需要安装共享的 LLVM 库。但是不需要 libbpf、clang 或 bcc！

> eBPF（扩展的 Berkeley 数据包过滤器）是一种技术，它可以使用指令集在虚拟机内运行沙盒程序。它起源于 Linux 内核，当系统中发生特定事件时，eBPF VM（作为内核的一部分）触发 eBPF 程序。新的 Linux 内核版本中添加了越来越多的事件。对于每种类型的事件，都有一种单独的 eBPF 程序。

基于 Aya 的项目的用户空间部分可以是异步的，同时支持 Tokio 和 async-std。Aya 可以加载 eBPF 程序，在异步上下文中对 eBPF 映射和 perf 缓冲区执行操作。如果想了解 Aya 更多信息可以查看[Aya Book](https://aya-rs.dev/)。




## 数据库与数据分析


### RedisJSON: Redis 官方支持 JSON 

RedisJSON 是一个 Rust 实现的 Redis 模块，实现了 ECMA-404 JSON 数据交换标准作为原生数据类型。它允许从 Redis 键（文档）存储、更新和获取 JSON 值。主要特点：

-   完全支持 JSON 标准
-   在文档中选择元素使用类似 JSONPath 的语法
-   文档存储为树结构中的二进制数据，允许快速访问子元素
-   所有 JSON 值类型支持类型化原子操作
-   基于 RediSearch 的二级索引支持

- 文档：[https://oss.redis.com/redisjson/](https://oss.redis.com/redisjson/)
- GitHub：[https://github.com/RedisJSON/RedisJSON](https://github.com/RedisJSON/RedisJSON)

### Arrow2 与 Arrow DataFusion

Apache Arrow 是大数据列式内存数据平台，有一个非常大的愿景：提供内存数据分析 (in-memory analytics) 的开发平台，让数据在异构大数据系统间移动、处理地更快。它采用 Cpp 实现，目前已经被业内大量使用。

[Arrow 从 2.0 版本开始引入 Rust](https://arrow.apache.org/blog/2020/10/27/rust-2.0.0-release/) ，从 4.0 开始 Rust 实现迁移到了独立仓库[arrow-rs](https://github.com/apache/arrow-rs)。随后社区也有人发布了 [Arrow2](https://github.com/jorgecarleitao/arrow2) 。Arrow2 是 arrow-rs 的竞争者，两者的主要区别：
- Arrow2 API 设计比 arrow-rs 更符合人体工效学，且实现 Arrow 规范更加完整，支持异步I/O
- Arrow2 比 arrow-rs 的安全性更好
- arrow-rs 是官方实现，用户基数大

Arrow DataFusion是一个可扩展的查询规划、优化和执行框架，用Rust编写，使用Apache Arrow作为其in-memory格式。鉴于 Arrow 这两个 Rust 库的生态分裂， DataFusion 的贡献者们正在[讨论是否将 DataFusion 的依赖改为 Arrow2](https://github.com/apache/arrow-datafusion/issues/1532) 。这样有助于 Arrow 的贡献者们把力量都集中在一个库中，实际上 Arrow2 和 arrow-rs 的贡献者们比较重叠。但是现在还未有什么结果。

###  surrealdb：文档图数据库

[surrealdb](https://github.com/surrealdb/surrealdb) 是一个可扩展的、分布式的、协作的、文档图（document-graph）云原生数据库。 适用于 Web、移动、无服务器、Jamstack、后端和传统应用程序。SurrealDB 通过简化数据库和 API 堆栈，消除对大多数服务器端组件的需求，并允许您更快、更便宜地构建安全、高性能的应用程序，从而缩短现代应用程序的开发时间。SurrealDB 既充当数据库又充当现代、实时、协作的 API 后端层。

目前客户端已支持 JavaScript、WebAssembly 和 Ebmer.js；服务端已支持 JavaScript、Node.js、Golang、Rust 和 Deno。其他语言也即将支持。


### Cube： 无头商业智能平台

[cube.js](https://github.com/cube-js/cube.js) 是 Rust 实现的一个开源无头商业智能（ Headless Business Intelligence）平台。无头意味着没有前端展现层，只提供分析 API 。Cube旨在与所有支持SQL的数据源一起工作，包括像Snowflake或Google BigQuery的云数据仓库，像Presto或Amazon Athena的查询引擎，以及像Postgres的应用数据库。Cube有一个内置的关系型缓存引擎，为API请求提供亚秒级的延迟和高并发性。

> 借助商业智能平台，人们能够导入、清理和分析来自数据库、电子邮件、视频、调查回复等来源的数据。这些数据分析可以提供支持移动和桌面设备的实时商业智能，让决策者能够根据见解采取行动，从而提高其组织的效率。


### Rust 实现的一些 K/V 存储引擎

-   [Engula](https://github.com/engula/engula) ：分布式 K/V 存储。它似乎是最活跃的项目。如果按照版本 0.4.0，其仍然没有为生产使用做好准备。
-   [AgateDB](https://github.com/tikv/agatedb) ：由 PingCAP 新创建的存储引擎，试图在 Tikiv 数据库中替换 RocksDB。
-   [Marble](https://github.com/komora-io/marble) ：一个新的 K/V 存储，旨在成为 Sled 的底层存储引擎，本身仍在开发中。
-   [PhotonDB](https://github.com/photondb/photondb) ：一种高性能存储引擎，旨在利用现代多核芯片、存储设备、操作系统和编程语言的强大功能。Github 上的 star 不多，但它似乎在积极地工作，而且看起来不错。
-   [DustData](https://github.com/rustbase/dustdata) ：[Rustbase](https://github.com/rustbase/rustbase) （一个 NoSQL K/V 数据库） 的存储引擎。
-   [Persy](https://crates.io/crates/persy) ：是用 Rust 编写的事务存储引擎.
-   [ReDB](https://github.com/cberner/redb) ：一种简单、可移植、高性能、ACID、嵌入式键值存储，其灵感来自 [LMDB](https://github.com/LMDB)。


###  greptimedb : 完全分布式的云原生时间序列数据库

[greptimedb](https://github.com/GreptimeTeam/greptimedb) 是一个使用 Rust 从头构建的完全分布式的云原生时间序列数据库。它提供多租户、开箱即用、完全托管的服务，每个用户都运行一个安全高效的数据生命周期：摄取、存储、分析、数据管理、可视化、异常检测、预测等。

GreptimeDB Cloud 服务主要由三个组件组成：
-   **Frontend**：无状态，负责网关协议和分布式写入和查询；
-   **Datanode**：工作节点，无状态，内置时序存储引擎和计算引擎；
-   **分布式WAL**：多租户共享的Write-Ahead-Log服务，用于支持Datanode的容错和容灾。

GreptimeDB 创始团队来自蚂蚁集团，更多信息可以参考 [GreptimeDB 官网](https://www.greptime.com/blogs/2022-11-15-this-time-for-real)。

### Xline : 用于元数据管理的地理分布式 KV 存储

[Xline](https://github.com/datenlord/Xline)  是基于  [CURP](https://www.usenix.org/system/files/nsdi19-park.pdf)的新共识协议实现的用于元数据管理的地理分布式 KV 存储
。

跨数据中心网络延迟是影响地理分布式系统性能的最重要因素，尤其是在使用共识协议时。我们知道共识协议很流行用于实现高可用性。例如，Etcd 使用[Raft](https://raft.github.io/) 协议，该协议在最近开发的系统中非常流行。

Raft虽然稳定且易于实现，但从客户端的角度来看，需要2个RTT（往返时间， Round trip time）才能完成一个共识请求。客户端和领导服务器之间发生一个 RTT，领导服务器使用另一个 RTT 将消息广播到跟随者服务器。在地理分布式环境中，RTT 很长，从几十毫秒到几百毫秒不等，因此在这种情况下 2 个 RTT 太长了。

Xline 采用名为 [CURP](https://www.usenix.org/system/files/nsdi19-park.pdf)的新共识协议来解决上述问题。有关详细说明，请参阅论文。该协议的主要好处是在竞争不太激烈时减少 1 个 RTT。Xline 是第一个使用 CURP 的产品。


### PingCAP Rust 重新实现的 Tidis 现在已开源

[Tidis](https://github.com/tidb-incubator/tidis) 是 TiKV 的服务层，旨在提供基于 PingCAP 的 Redis 协议兼容的分布式存储服务。它实现了多种数据类型（`string/hash/list/set/sortedset`），已被社区广泛使用。

之前是 go 语言实现的 1.0 版，现在已经完全用 Rust 重新设计和重写，以便获得更好的性能和更低的延迟。以及更重要的功能，例如 Lua 脚本、TLS 连接、锁优化等。

###  Databend v0.8 发布

[Databend](https://github.com/datafuselabs/databend) v0.8 的开发于 3 月 28 号开始，在过去的几个月中，新增了几十万行代码，相当于把 Databend 重写了一遍。该版本对 SQL Planner 框架做出了重大改进，并将所有的 SQL 语句都迁移到了新的 Planner 上，提供了完整的 JOIN 和子查询支持。该版本目前还在积极开发中。

Databend 在今年也使用 [sqllogictest-rs](https://github.com/risinglightdb/sqllogictest-rs) 成功地将 sqllogictest 框架（[Sqllogictest](https://www.sqlite.org/sqllogictest/doc/trunk/about.wiki)是一个用于验证 SQL 数据库正确性的测试框架）从 Python 切换到 Rust了 。 


###  warpgate: 无需客户端的 Mysql 堡垒机

[warpgate](https://github.com/warp-tech/warpgate) 是一款 Rust 实现的适用于 Linux 的智能 SSH、HTTPS 和 MySQL 堡垒主机，不需要特殊的客户端应用程序。

该项目目前处于**alpha**阶段，正在收集社区反馈。



### BastionLab ： 用于数据科学协作的 Rust 隐私框架

[BastionLab](https://github.com/mithril-security/bastionlab/) 专为敏感数据协作而构建。

由于安全和隐私问题，数据所有者和数据科学家之间的协作对于健康、金融或广告等高度监管的领域来说是一个巨大的挑战。远程协作时，数据所有者必须打开他们的整个数据集，通常是通过 Jupyter 笔记本。这种过于广泛的访问会造成巨大的隐私漏洞，因为允许的操作太多，这使得数据科学家能够从远程基础设施中提取信息（打印整个数据库、将数据集保存在权重中等）。

BastionLab 通过提供细粒度的访问控制解决了这个问题。它向数据所有者保证，数据科学家只能对他们的数据执行隐私友好的操作，并且只能与他们共享匿名输出。

BastionLab 确保数据所有者的远程数据永远不会被数据科学家直接访问。三个主要元素确保了这一点：

-   首先，数据所有者定义了一个“安全区”来过滤数据科学家的查询，在允许交互的同时加强控制。
-   其次，表现力有限。这意味着数据科学家可以执行的操作类型受到限制，以避免任意代码执行。
-   最后，数据科学家从不在本地访问数据集。他们只操纵包含元数据的本地对象与远程托管的数据集进行交互——数据所有者始终可以看到该对象发出的调用。


### mvsqlite : 分布式 MVCC SQLite

[mvsqlite](https://github.com/losfair/mvsqlite) 项目是一个在 FoundationDB 上运行的分布式 MVCC SQLite。SQLite 是一个单写数据库——由于其基本的设计选择，这不会轻易改变。但是一组（N 个）sqlite 数据库是一个 N-writer 数据库。 mvsqlite 提供了必要的机制来执行可序列化的跨数据库事务，而无需额外的开销。

###  lnx ： Elasticsearch 和 Aloglia 的快速替代品

[lnx](https://github.com/lnx-search/lnx) 是基于tokio 和  [tantivy 搜索引擎](https://github.com/tantivy-search/tantivy) 构建的Elasticsearch 和 Aloglia 的快速替代品。lnx 可以同时为数以万计的文档插入提供毫秒级索引（不再等待事物被索引！），每个索引事务和处理搜索的能力，就像它只是哈希表上的另一个查找一样。

**同类型开源项目**：
- [Toshi](https://github.com/toshi-search/Toshi) ，一个类似 Elasticsearch 的全文搜索引擎，但是在 2022 年已经不怎么维护了。

### ReadySet ： 轻量级 SQL 缓存引擎

[readyset](https://github.com/readysettech/readyset) 是一个用 Rust 编写的轻量级 SQL 缓存引擎，可帮助开发人员增强现有应用程序的性能和可扩展性。它可以预先计算经常访问的查询结果，并随着数据库中基础数据的变化自动使这些结果保持最新。ReadySet 与 MySQL 和 Postgres 兼容，无需更改代码即可采用。ReadySet 既充当 SQL 缓存又充当代理。

Readyset 在 2022年融资了 2900 万美元。ReadySet 的产品起源于 Marzoev 和该公司的第二位联合创始人 Jon Gjengset 在麻省理工学院攻读博士学位时所做的研究 [noria](https://github.com/mit-pdos/noria)。



## 网络服务


### tokio 生态 2022 发展

[tokio](https://github.com/tokio-rs/tokio)  在 2022 年进入了稳定维护期，今年的侧重点在于 tokio 生态：
- 发布了 [tokio-metrics](https://tokio.rs/blog/2022-02-announcing-tokio-metrics) ，提供对生产中运行时行为的可见性，使 Tokio 用户更容易调试其应用程序的性能问题。如今，Tokio 已成功用于亚马逊、微软、Discord 等公司的大规模生产部署，tokio-metrics 可以帮助开发人员确定生产环境中的性能问题所在。
- 发布 [async-backtrace](https://crates.io/crates/async-backtrace) ，使得开发者能够有效地跟踪和查看应用程序中异步任务的状态。无需配置开箱即用，适合在生产环境中部署。
- 发布 [axum](https://crates.io/crates/axum) 0.6 版本。axum 是一个符合人体工效学的模块化 Web 框架，使用[`tokio`](https://crates.io/crates/tokio)、[`tower`](https://crates.io/crates/tower)和构建[`hyper`](https://crates.io/crates/hyper)。 新的版本增加了新的  `State` extractor ，并且增加了 WebAssembly 的支持等。


### Volo:  国内首个 Rust 语言的 RPC 框架 

[volo](https://github.com/cloudwego/volo) 是字节跳动服务框架团队研发的轻量级、高性能、可扩展性强、易用性好的 Rust RPC 框架，使用了 Rust 最新的 GAT 和 TAIT 特性。Volo 使用 [Motore](https://github.com/cloudwego/motore) 作为中间件抽象层，Motore 基于 GAT 设计。

在和 Kitex 相同的测试条件（限制 4C）下，Volo 极限 QPS 为 35W；同时，我们内部正在验证基于 [Monoio](https://github.com/bytedance/monoio)（CloudWeGo 开源的 Rust Async Runtime）的版本，极限 QPS 可以达到 44W。

Volo 框架更多说明参考[Volo官方文档](https://www.cloudwego.io/zh/docs/volo/overview/)。


### hyper 1.0 rc 版本发布

hyper 1.0 第一个候选版本发布，产品进入“抛光期”。在这个阶段 hyper 将从四个方面进一步完善以便顺利发布 1.0 版本“：
- 文档。hyper 1.0 应该有一流的文档，并且成为 Rust crates 的榜样。hyper.rs 网站需要被改进。
- 实用程序。
- 升级。让用户升级到 1.0 尽可能地顺利。
- 收集反馈。
此抛光计划预计几个月后完成，所以 hyper 1.0 快来了。

目前 HTTP/3 也正在被整合进 hyper 过程中。hyper 生态中还有 [Tower](https://github.com/tower-rs) 中间件等值得被关注。

hyper 是一个非常完善且“正确的” HTTP 协议实现，广泛应用于各个项目中，有位网友在 reddit 上发帖问：[像 hyper 这样的 HTTP 协议实现，声称是“正确的”，这到底意味着什么？](https://www.reddit.com/r/rust/comments/xzxin3/what_is_meant_by_correct_http_implementation/) 

以下节选自高赞回答：
- 协议类似于一组规则。其规定了可接受的数据格式、在不同站点中允许哪些指令、应当采取的行为......。超文本传输​​协议（HTTP）也对应一个这样的规则列表，例如：
	- 请求的第一行必须以动词（GET、POST 等）、url 和 HTTP 版本开头，然后是换行符；
	- 标头必须采用特定格式。例如，标题的名称不能包含 “:” 字符；
	- 如果请求包含正文，则必须声明长度。
	- 如果说 HTTP 协议的实现是“正确的”，背后的想法是，用户必须不可能生成无效的 HTTP 请求。例如，一旦您开始发送正文，就不可能设置 HTTP 头部，因为这样做是无效的。
- 从另一个角度来看，特别是对于像 HTTP 这样的协议，它比 RFC 规定的内容更难实现。最“正确的”实现，在应用于现实世界时，总会遇到一长串奇怪但合法的行为，这将使一些客户端或服务器在某些时候崩溃。
- 有时候在现实世界中，你需要忍受一些不正确的实现。例如 Cloudflare 就没有将 Hyper 应用于他们的 Rusty Proxy 服务中，因为它太严格了，不满足 Cloudflare 对于现实应用的需求。




### mmids: Rust编写的多媒体收发系统

[mmids]((https://github.com/KallDrexx/mmids/) (multimedia Ingestion and Distribution System)是一个功能强大、用户友好、开源的实时视频工作流服务器。

目前 mmids 能做什么?

-   通过RTMP 接收音频/视频
-   提供RTMP 音频/视频服务
-   从外部源接收音频和视频
-   直播视频转码
-   生成视频的HLS流
-   将实时视频推到外部RTMP服务器。

[github地址](https://github.com/KallDrexx/mmids/)

### zbus 2.0 发布

D-Bus 是一种在 Linux（尤其是桌面和嵌入式系统）上非常流行的进程间通信 (IPC) 机制。 而 zbus 是一个纯粹的 Rust 库，旨在使 D-Bus 处理尽可能简单，许多服务（例如 systemd、NetworkManager、Geoclue 等）都使用它。

而大家期待已久的2.0 稳定版发布了！ 😎 虽然 1.x 版本很受欢迎，但缺少异步 API。 2.0 使用了全新的设计，将异步 API 作为主要的 API，阻塞 API 只是一个包装器。

- [zbus](https://docs.rs/zbus/latest/zbus/)  
- [zbus book ](https://dbus.pages.freedesktop.org/zbus/)


###   非透明 UDP 代理 quilkin 0.4.0 发布

[Quilkin](https://github.com/googleforgames/quilkin/releases/tag/v0.4.0) 是一种非透明 UDP 代理，专门设计用于大型多人专用游戏服务器部署，以确保安全性、访问控制、遥测数据、指标等。它旨在用于游戏客户端后面以及专用游戏服务器前面。Quilkin 是 Google 和 Embark Studio 联合开发的。



## Web 开发

Rust 在 Web 开发领域一直不温不火，有些人认为将 Rust 用于 Web 开发是大材小用，也有些人认为 Rust 也非常适合开发 Web 项目。

无论你持有何种观点，也不能否认 Rust 在 Web 领域确实出现了很多库与框架：

- [Poem](https://github.com/poem-web/poem) 是 一款由国人开发的 Rust 异步 Web 框架。
-  [axum](https://github.com/tokio-rs/axum)，是 tokio 官方新发布的 Web 框架，它的特色是无宏（macro-free），并且基于 Tower 中间件抽象，充分利用 Tower 生态。缺点就是泛型用的太多。
- [perseus](https://github.com/arctic-hen7/perseus)， 比如增加了plugin系统，支持i18n，i18n是基于fluent来做的。fluent之前帮rust官网翻译时候用过，非常方便。
-  [SeaORM](https://github.com/SeaQL/sea-orm) 是一款异步动态 ORM，要做 Rust 版本的 Active Record。
- [swc](https://github.com/swc-project/swc)，是 Speedy Web Compiler 缩写，是一款用 Rust 编写的超快 TypeScript / JavaScript 编译器。swc 目前已经被 deno、next.js、Vite 4.0等知名项目使用。
- [sycamore](https://link.zhihu.com/?target=https%3A//github.com/sycamore-rs/sycamore) 是一个响应式的无虚拟dom 的 前端库，同样是基于 Rust 和 WebAssembly 。它的特点是，不支持 JavaScript ，因为不需要。
- [seed](https://link.zhihu.com/?target=https%3A//github.com/seed-rs/seed) ，基于 Elm 架构的 Rust 前端框架。
- [sauron](https://link.zhihu.com/?target=https%3A//github.com/ivanceras/sauron), 一个多功能的 Web 框架和库，用于构建客户端和/或服务器端 Web 应用程序，非常注重简单性。它适用于开发使用渐进式渲染的 Web 应用程序。
- [MoonZoon](https://link.zhihu.com/?target=https%3A//github.com/MoonZoon/MoonZoon)，正在开发的一款全栈 Rust 框架，号称没有 JS/CSS/HTML等，开发进度较慢。
- [Yew](https://link.zhihu.com/?target=https%3A//github.com/yewstack/yew) 是一个设计先进的 [Rust](https://link.zhihu.com/?target=https%3A//www.rust-lang.org/) 框架，目的是使用 [WebAssembly](https://link.zhihu.com/?target=https%3A//webassembly.org/) 来创建多线程的前端 web 应用。它基于组件，灵感来自于 React 和 Elm，高性能，且支持与 JavaScript 交互。目前还在活跃开发中。

2022 年也涌现出一些值得关注的新库和框架。

### submillisecond:  围绕 WebAssembly 的 Rust  Web 后端框架

[submillisecond](https://github.com/lunatic-solutions/submillisecond)  是 lunatic 在今年推出的一个 Web 框架。注重 WebAssembly 安全性，基于 lunatic 调度运行时。submillisecond 框架编写的程序会先编译为[WebAssembly](https://webassembly.org/)，然后才能由运行时执行。

> [lunatic](https://link.zhihu.com/?target=https%3A//github.com/lunatic-solutions/lunatic)，是受 Erlang 影响的一个 WebAssembly 运行时。你可以使用它**快速**、**健壮**和**可扩展**的服务器端应用程序，但是你可以通过任意可以编译为 WebAssembly 的语言来使用它。Lunatic 的并发是基于超轻量级进程，类似于绿色线程或 [go-routines](https://link.zhihu.com/?target=https%3A//golangbot.com/goroutines)。Lunatic 的进程创建速度快，内存占用小，调度开销低。它们专为**大规模**并发而设计。在一般的应用程序中同时运行数十万个这样的进程并不少见。Lunatic 进程彼此完全隔离，它们有自己的栈、堆甚至系统调用。如果一个进程失败，它不会影响系统的其余部分。这允许开发者创建强大且容错的抽象。

submillisecond 的另一个特色是支持 [Liveview](https://github.com/lunatic-solutions/submillisecond-live-view) 。 Liveview 的灵感来自于Elixir的[Phoenix web 框架](https://hexdocs.pm/phoenix_live_view/Phoenix.LiveView.html) 。 LiveView 编程模型是声明式的：LiveView 中的事件不是说“一旦事件 X 发生，就在页面上更改 Y”，而是可能导致其状态发生变化的常规消息。一旦状态发生变化，LiveView 将重新渲染其 HTML 模板的相关部分并将其推送到浏览器，浏览器以最有效的方式进行自我更新。这意味着开发人员像编写任何其他服务器呈现的 HTML 一样编写 LiveView 模板，LiveView 负责跟踪更改并将相关差异发送到浏览器。



###  Turbopack: Webpack 的继任者

[Turbopack](https://turbo.build/)， Vercel 公司发布的新的 Webpack 的继任者，Rust 实现，性能是 Webpack 的 700 倍。

Turbopack 真正的优势应该在哪？来自[知乎相关问题的一个答案](https://www.zhihu.com/question/562349205/answer/2735222403  )如是说：

-   冷启动性能优势。Vite 虽然服务启动快，但浏览器按需加载的时间比较久，导致首屏加载时间可能会很长，这个问题尤也提过多种解决方案，比如给 Vite 加上物理缓存(持久化缓存)，利用 web bundles 标准来优化级联请求，但在 Turbopack 的下面，这个问题可以很好的解决，官方给出的数据是冷启动快 5 倍左右，个人觉得这是值得 Turbo 去大力宣传的一个方面。
-   开发和生产环境的一致性。说到一致性，Vite 现在默认模式下是存在一些打包行为不一致的问题的，主要是对依赖的处理，开发阶段走 Esbuild，生产环境走 `@rollup/plugin-commonjs`。但在 Turbopack 当中可以统一打包方案，避免了这种不一致问题导致的各种疑难杂症。
-   极致的缓存复用。Turbo 中的缓存可以达到函数级别，可以达到极细粒度的缓存复用，并且结合 Turbo 的远端缓存，你把某个模块编译完了，你的队友可以复用编译结果，从而跳过编译，想想都觉得不要太爽。

###  Canyon-SQL: 新的 Rust ORM 框架

[Canyon-SQL](https://github.com/zerodaycode/Canyon-SQL) 同时处理多个数据库的高级抽象。建立在`async` 特性之上以提供高速、高性能的库来处理消费者的数据访问。

目前还是早期开发状态，值得关注。


### Diesel 2.0 发布

经过 135 人历时 3 年 的努力，Diesel 2.0 发布了，这里是 [Release 日志](https://diesel.rs/news/2_0_0_release.html) 。

Diesel 2.0 的亮点：

 • 支持完全类型检查 GROUP BY
 • 支持表别名
 • 支持通过相应类型定义选择子句
 • 支持UNION/INTERSECT查询

此版本中有一个影响所有用户的重大变化：Connection trait 上的任何方法现在都需要一个可变引用，而不是像 1.x 那样的共享引用。此更改的主要动机是支持将结果加载为迭代器。

Diesel 2.0 目前还未打算支持异步，因为这方面的生态系统还不够成熟。从长远来看，Diesel 生态系统可能由多个部分组成：一个提供 DSL 和任何与 io 无关的核心 crate，然后其他 crate 可以提供实际的异步和同步连接实现。 这可能是未来几年的事情，因为这需要首先解决语言级别的问题，还需要进一步扩大 Diesel 团队，这样就不需要由同一个人维护所有的 crate。

异步 Diesel 的稳定步伐目前受以下 Rust 语言未完成的部分所阻止：
 • 能够在不使用某些诸如`#[async_trait]`或类似解决方法的情况下将异步函数作为trait 函数。这可能需要对任何涉及的生命周期进行很好的控制。
 • 能够接受一个返回未装箱 Future 的闭包，同时处理生命周期的东西。这基本上被 rustc 阻止了，无法在那里计算出正确的生命周期。严格来说，这不是异步的问题，而是当前借用检查器实现中的一个缺点/错误。（有关基本问题的简化版本，[请参见此](https://play.rust-lang.org/?version=nightly&mode=debug&edition=2018&gist=edf21096f32305763ed0e4dcee8b832f) [playground）](https://play.rust-lang.org/?version=nightly&mode=debug&edition=2018&gist=edf21096f32305763ed0e4dcee8b832f)


###  博客联盟 ActivityPub协议支持

今年马斯克收购 Twitter 事件引发了 Mastodon（长毛象，Ruby实现） 的使用狂潮，Rust 社区也开始支持 ActivityPub协议。

相关项目：
- [Plume](https://github.com/Plume-org/Plume) 一个基于ActivityPub协议开发的社区联盟博客系统，基于rocket和diesel实现。
- [lemmy](https://github.com/LemmyNet/activitypub-federation-rust) 也开始支持 ActivityPub 协议了。

### ApolloRouter：统一GraphQL

[ApolloRouter](https://github.com/apollographql/router)  正在构建软件平台帮助用户在应用程序和服务中统一 GraphQL。包括：

-   [Apollo Studio](https://www.apollographql.com/studio/develop/)：管理 GraphQL 生命周期的免费的端到端平台。
-   [Apollo Federation](https://www.apollographql.com/apollo-federation/)：用于构建分布式图的行业标准开放架构。
-   [Apollo Client/](https://www.apollographql.com/apollo-client/)：Web 开发最流行的 GraphQL 客户端，同时也有 IOS 和 Android 端。
-   [Apollo Server](https://www.apollographql.com/docs/apollo-server/)： 一个用于生产的 JavaScript GraphQL 服务器，可连接到任何微服务、API 或数据库。





## 云原生


### spin: 基于Rust 和 WebAssembly 的微服务框架

[spin](https://github.com/fermyon/spin) 是  fermyon 团队开源的一款用于使用 WebAssembly 构建和运行快速、安全且可组合的云微服务的框架。它旨在成为开始使用 WebAssembly 微服务的最简单方法，并利用 [WebAssembly 组件模型](https://github.com/WebAssembly/component-model) 和[Wasmtime](https://wasmtime.dev/)运行时的最新发展。

spin 团队还开源了一个 [Bartholomew](https://github.com/fermyon/bartholomew) 项目 ，它是一个简单的类似 CMS 的网站托管工具。它完全编译为 WebAssembly，可以在任何支持 Spin 的系统中运行。

自动缩放和缩放到零（Scale-to-zero）是所有无服务器平台以及平台即服务 (PaaS) 解决方案提供商的关键功能要求，因为它有助于最大限度地降低基础设施成本。Scale-to-zero 是 Kubernetes devops 长期以来一直追求的策略。并且有充分的理由！成功意味着省钱。在 Kubernetes 生态系统中，许多项目试图实现规模为零。当使用 Spin 构建 WebAssembly 项目时，可以将其构建为默认缩放到零，Fermyon 平台时[从一开始就添加了Scale-to-zero这个能力](https://www.fermyon.com/blog/scale-to-zero-problem)，这意味着不仅可以节省成本，还可以改善开发人员的体验，以及一个长期更易于操作的平台。


### Wasmtime 发布 1.0 稳定版

[Wasmtime](https://github.com/bytecodealliance/wasmtime) 是一个 Rust 编写的 WebAssembly 编译器，是 WebAssembly 用于云原生领域的重要基础设施工具。2022年9月，[Wasmtime 发布 1.0 稳定版](https://bytecodealliance.org/articles/wasmtime-1-0-fast-safe-and-production-ready)。

以下是wasmtime的一些生产应用实践，为改进 wasmtime做了贡献：

- Shopify — 14 个月的生产。Shopify 于 2021 年 7 月从另一个 WebAssembly 引擎切换到 Wasmtime。切换后，Shopify 的平均执行性能提高了约 50%。
- Fastly ——6个月的生产。Fastly 于 2022 年 3 月从另一个 WebAssembly 引擎切换到 Wasmtime。Fastly的执行时间也提高了约 50%。此外，Fastly的每秒请求数增加了 72% 到 163%。此后，Fastly使用 Wasmtime 处理了数万亿个请求。
- DFINITY — 16 个月的生产。DFINITY 于 2021 年 5 月使用 Wasmtime 推出了 Internet Computer 区块链。自那时以来，Internet Computer 已为超过 150,000 个智能合约执行了 1 quintillion (10^18) 指令，没有任何生产问题。
- InfinyOn — 14 个月的生产。自 2021 年 7 月以来，InfinyOn Cloud 一直在生产中使用 Wasmtime。与 Kafka 等基于 Java 的平台相比 ，InfinyOn 能够在端到端流处理中提供超过 5 倍的吞吐量提升。
- Fermyon——6个月的生产。自 2022 年 3 月发布以来，Fermyon 的 Spin 一直在使用 Wasmtime。从那时起，Fermyon 发现数以万计的 WebAssembly 二进制文件可以在单个 Spin 实例中运行，同时将启动时间保持在毫秒以内。
- Embark — 生产 2 年。自 2020 年以来，Embark 一直在他们的游戏引擎中使用 Wasmtime。从那时起，Embark 对 Wasmtime 出色的稳定性、安全性和性能印象深刻，使游戏以 60 FPS 运行。
- SingleStore — 生产 3 个月。自 2022 年 6 月以来，SingleStoreDB Cloud 一直在使用 Wasmtime，将开发人员的代码安全、快速且可扩展地引入数据中。
- Microsoft — 11 个月的预览版。自 2021 年 10 月以来，Microsoft 已在 Azure Kubernetes 服务中为其 WebAssembly 系统接口 (WASI) 节点池提供 Wasmtime 预览版。

wasmtime被用于以下领域：

- 微服务和serverless
- 第三方插件系统
- 数据库、分析和事件流
- 可信的执行环境
- 便携式客户端，比如浏览器
- 区块链（智能合约）

###  Wasmer 3.0 发布

[Wasmer](https://wasmer.io/) 是一个用于在服务器上执行 WebAssembly 的开源运行时。
Wasmer有什么新功能？

- Wasmer现在能够直接通过wasmer运行WAPM包了
- 更好的API和内存管理
- 简化了引擎的工作方式
- 支持为任何平台创建本地可执行文件
- WASI的改进
- 其他

详情可以参考 [Wasmer 官网信息](https://wasmer.io/posts/announcing-wasmer-3.0) 



### 云原生搜索引擎 Quickwit 0.4 发布

[Quickwit](https://github.com/quickwit-oss/quickwit) 是一个用Rust编写的用于日志管理和分析的云原生搜索引擎。它被设计成非常具有成本效益，易于操作，并可扩展到PB级。目前发布了 0.4 版本。新版本基于 Kafka 进行分布式索引，并正式支持Kubernetes作为部署平台。更多细节可以参考[其官方博客](https://quickwit.io/blog/quickwit-0.4/) 。


### CrosVM : 基于Linux的KVM管理程序的虚拟机监控器（VMM）

[CrosVM](https://github.com/google/crosvm) 是Chrome操作系统中用于创建虚拟机的应用。是一个Rust编写的轻量级的虚拟机。亚马逊的Firecracker从crosvm开始。借助于CrosVM 用户可以很容易的在ChromeOS中运行Linux、Android以及Windows应用程序。


### Deno  ： 发布 Deno Deploy

[Deno](https://github.com/denoland/deno) 是基于 Rust 编程语言和 V8 JavaScript 引擎的 JavaScript、TypeScript 和 WebAssembly 运行时，最初是为 Google Chrome 和 Chromium 网络浏览器开发的。Deno由 Dahl 共同创建，他还创建了[Node.js](https://techcrunch.com/tag/node-js/)，旨在提供一个“高效”且安全的脚本环境，可用于管理服务器、执行科学计算等。

Deno 背后同名公司在 2022年 6 月获得由红杉领投的 2100 万美元 A 轮融资，使其融资总额达到 2600 万美元。融资主要用于构建 Deno 的商业产品[ Deno Deploy](https://deno.com/deploy)，同时扩大营销业务并探索新的业务线。

Deno 在 2022 年发展路线随着 Deno Deploy 发布有所侧重于边缘计算。deno 生态在今年也开始走向兼容 Node 的路线拥抱 Node 生态。

### ockam:  信任动态数据

[ockam](https://github.com/build-trust/ockam) 是一套开源工具、编程库和托管云服务，用于大规模编排端到端加密、相互身份验证、密钥管理、凭证管理和授权策略实施。

现代应用程序是分布式的，并且具有大量必须可靠地交换数据的互连。为了建立对动态数据的信任，应用程序需要端到端的数据真实性、完整性和机密性保证。为了在设计上做到私密和安全，应用程序必须对每个信任和访问决策进行精细控制。Ockam 允许开发者将这些控制和保证添加到任何应用程序。

Ockam 允许开发者在任何传输拓扑上创建端到端加密、经过身份验证的安全通道，以及为分布在许多边缘、云和数据中心专用网络中的应用程序内的可信通信提供加密中继等，详细功能参考[Ockam官方文档](https://docs.ockam.io/)。

###  Docker 与 WasmEdge 合作，发布 WebAssembly 支持

在 KubeCon NA 2022 的 [Cloud native Wasm day](https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fyoutu.be%2F3j915xoDovs) 活动上，Docker 与 CNCF 的 [WasmEdge Runtime](https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fgithub.com%2FWasmEdge%2FWasmEdge) 项目发布了 [Docker+Wasm 技术预览](https://www.oschina.net/action/GoToLink?url=https%3A%2F%2Fwww.docker.com%2Fblog%2Fdocker-wasm-technical-preview%2F)。 只需一个命令 `docker compose up`, 上千万的 Docker 开发者可以立即构建、共享并运行一个完整的 Wasm 应用。

WasmEdge 是 Cpp 实现的 WebAssembly 运行时，也提供了 [Rust SDK](https://github.com/WasmEdge/WasmEdge/tree/master/bindings/rust) 。


###  plane:  基于浏览器的容器编排工具

[plane](https://github.com/drifting-in-space/plane)  允许用户通过 API 启动任何使用 HTTP 的容器的实例。Plane 为每个实例分配一个唯一的子域，通过它代理 HTTPS/WebSocket 连接。当容器的所有入站连接都被丢弃时，Plane 将其关闭。

Plane 实现了一个被称为[会话后端](https://driftingin.space/posts/session-lived-application-backends)的架构。

> Web 浏览器已成为新应用软件事实上的交付渠道。 人们很容易将所有基于浏览器的软件统称为“网络应用”，而将构建它们的人统称为“网络开发人员”。但是开发人员在浏览器中构建类似于桌面的体验的方式与构建 Web 原生应用程序（如博客和社交媒体网站）的方式有所不同。出现的一个区别是我们称之为**会话后端**的模式。
> 在传统的 Web 架构中，后端层由一组无状态、可互换的服务器组成。
> 随着越来越复杂的应用程序迁移到浏览器，这种方法就会失效。此时开发人员可用的选项分为三种通用方法，其中之一就是会话后端，即，1.  在服务器上为每个用户启动一个专用进程，并在该进程中维护状态。为前端提供与其专用进程的持久连接，并在用户关闭应用程序时关闭该进程。生产中的案例包括 GitHub Codespaces 和 [Figma 实时多人管理应用](https://www.figma.com/blog/rust-in-production-at-figma/) 。

使用 Plane，开发者可以将后端作为容器镜像（也称为 Docker 镜像）提供，Plane 会为开发者提供一个私有 HTTP API，用于在集群中“生成”该后端的新实例。API 返回一个 URI，然后可用于直接从您的前端代码打开到新后端的 HTTP 连接。Plane 监视后端进程的活动，并在一段时间没有连接后将其关闭。[这是一个演示。](https://www.youtube.com/watch?v=aGsxxcQRKa4) 

>  编者按： Plane 弃用 Docker 而采用 fermyon  [spin](https://github.com/fermyon/spin)  是不是更轻量呢？


###  mirrord: 一款致力于改善开发工作流的开发工具

[mirrord](https://github.com/metalbear-co/mirrord) 是第一个把本地进程完全封装在 Kubernetes 集群上下文中的版本 —— 将网络流量、文件访问、环境变量通通连接在一起，开发者可以在熟悉的舒适的本地环境中继续运行程序进程，但是输入、配置和状态都来自于云。通过 mirrord 开发者将会得到一个与模拟环境相符合的开发环境，代码一经编写完成即可上云。

目前发布了 3.0 版本，该版本是第一个完整且稳定的 mirrord 版本。完全用 Rust 实现。

###  Apache APISIX  拥抱 Rust 和 WebAssembly

[Apache APISIX](https://blog.frankel.ch/rust-apisix/1/) 是**Apache** 软件基金会下的云原生API 网关，它兼具动态、实时、高性能等特点，提供了负载均衡、动态上游、灰度发布（金丝雀发布）、服务熔断、身份认证、可观测性等丰富的流量管理功能。

APISIX 是基于 Nginx 和 OpenResty 构建的，这让 APISIX 提供可以满足大多数业务需求的开箱即用Lua插件. 但总有一天, 通用插件无法满足开发者的需求，所以现在 APISIX 支持使用 Rust 来编写这类自定义插件。

APISIX  是通过集成 `api7.ai` 开源的 [wasm-nginx-module](https://github.com/api7/wasm-nginx-module) （C 语言实现） 来支持 WebAssembly，`api7.ai`是 Apache APISIX 的主要贡献者之一。顾名思义，集成是在 Nginx 级别完成的，在 Nginx 上实现[proxy wasm ABI](https://github.com/proxy-wasm/spec) 。APISIX 提供了 [proxy wasm Rust SDK](https://github.com/proxy-wasm/proxy-wasm-rust-sdk) 来支持 Rust 编写插件。

#### Kong Gateway 3.0 发布，包含 Rust 实现的新组件

和 Apache APISIX 同类型的云原生 API 网关 Kong ，也开始使用 Rust 来实现一个[全新的路由引擎 `atc-router`](https://github.com/Kong/atc-router)，使用DSL来增加路由层的表达能力。

在 Kong 的 GitHub 开源组织中也看到了 `proxy-wasm`  Rust SDK 的hello world 项目，以及 fork 了 wasmtime ，从这个迹象表明，Kong 也许也会学习 APISIX 来支持 WebAssembly 引入自定义插件功能。

### nixpacks：构建docker 镜像

**App source + Nix packages + Docker = Image**

[Nixpacks](https://github.com/railwayapp/nixpacks) 由[Railway团队启动，作为](https://railway.app/)[Buildpacks](https://buildpacks.io/)的替代方案，并试图解决在将数千个用户应用程序部署到 Railway 平台时出现的许多缺点和问题。

该项目采用源目录生成一个兼容 OCI 的 image，该 image 可以部署在任何地方。核心原则：

-   符合直觉的默认值：在大多数情况下，使用 Nixpacks 构建和部署应用程序应该无需任何配置即可工作。
-   可定制：管道的每个部分都应该是可配置的。其中包括要添加到环境中的 Nix 包和构建/启动命令。
-   易于扩展：可以使用最少的 Nix 和 Docker 知识讲新的提供者（语言）轻松添加到 nixpacks 中。

###  inspektor: 使用 wasm 来执行 OPA 策略

[inspektor](https://github.com/inspektor-dev/inspektor) 是一种协议感知代理，用于执行访问策略。 旨在与所有数据库一起使用，例如 Postgres、MySQL 和 MongoDB。

> OPA（Open Policy Agent）是一种策略执行引擎，可用于多种用途。OPA 用于跨云原生技术栈的统一工具集和策略框架。使用 OPA 发布、分析和审查策略，而不会牺牲可用性或性能。

Inspecktor 包含 2 个主要组件：控制平面和数据平面。控制平面充当管理服务，动态配置数据平面以执行策略。数据平面与数据服务一起部署，通过拦截网络流量对进入数据库的所有查询实施访问策略。Inspecktor 是通过运行 WebAssembly 模块来执行 OPA 策略。



##  工具

### 分布式版本管理工具 Pijul 1.0 beta 版发布

[pijul](https://pijul.org/) 是一个免费的开源 (GPL2)**分布式版本控制系统**。经过了 53 个alpha版本的Pijul 1.0 beta终于发布了。

Git 目前占据版本控制工具的主导地位，但是未来版本控制工具该如何发展呢？Pijul 也许是一个视角。

Pijul 的架构和设计方法受到Darcs项目的影响，Pijul 使用类似于Darcs的以补丁程序为中心的模型，该模型在重新排序，挑选或重组补丁程序时不需要重写历史记录。所有补丁程序都将永久保留其身份，无论其上下文，顺序，执行的操作或团队工作流程如何。这是一个非常优雅的解决方案，并且可以说是一种更自然的创建此类系统的方法。这与Git相反，在Git中，某些操作（例如重新设置基数和Cherry-Picks）可以更改提交ID（和其他标识符），即使内容本身没有更改。此外，由于重写了最初的 cherry-pick 的提交ID，因此来自Git远程分支的后续 cherry-pick 可能导致不自然的冲突。 Pijul完全避免了此问题，因为补丁程序始终保留其身份，无论它们在分支中的位置如何。

看得出来，Pijul 解决了 Git 的一些问题，但目前它并未正式稳定。

### Sapling： Meta开源的源码版本控制系统

[sapling](https://github.com/facebook/sapling) 是 Meta（原 facebook）开源的兼容 Git 的源码版本控制系统，强调可用性和可扩展性。Meta 花了大约十年时间创建了 sapling，为了能让 Meta 内部巨大的单体代码仓库（简称monorepo）在增长时能够更好地扩展。Sapling可以为Meta的内部资源库提供服务，包括数千万个文件、数千万个提交和数千万个分支。Sapling 是基于 [Mercurial](https://www.mercurial-scm.org/ ) 发展而来的。

Sapling SCM的可扩展性目标是确保所有的源控制操作随着开发者使用的文件数量而扩展，而不是随着资源库本身的大小而扩展。这使得即使在拥有数百万文件和极长的提交历史的大规模资源库中也能实现快速、高性能的开发者体验。

目前开源的 Rust 实现是 SCM 客户端。未来还会开源其高度可扩展的分布式源代码控制服务器 Mononoke 和 用于有效地签出大型资源库的虚拟文件系统 [EdenFS](https://github.com/facebook/sapling/blob/main/eden/fs/docs/Overview.md) 。

### Fornjot: 世界需要另一个CAD程序

[Fornjot](https://github.com/hannobraun/Fornjot) 是一个早期的爱好者项目，旨在创建新一代的Code-CAD应用程序：因为世界需要另一个CAD程序。

这个项目的目标是创建一个有如下特色的CAD应用程序：

-   使用代码优先的方法；
-   是开源的；
-   广泛使用，支持所有主要平台；
-   基于一个新的CAD内核，用Rust语言编写；
-   提供一个全面的功能集；
-   以及对不同建模语言的支持；

这个目标还没有实现。事实上，还远远没有! 但Fornjot正在一步一步地慢慢变得更好。Fornjot正在积极开发中，但仍然是实验性的。目前的工作重点是提供一套稳定的基本CAD功能。


### Weylus：移动设备作为输入板/触屏

[Weylus](https://github.com/H-M-H/Weylus) 可将平板电脑或智能手机用作计算机上的图形输入板 / 触摸屏。

主要特征：

-   使用平板电脑控制鼠标
-   将屏幕镜像到平板电脑
-   使用物理键盘发送键盘输入
-   硬件加速视频编码

上述功能在所有操作系统上都可用，但 Weylus 在 Linux 上效果最好。

### flux: 用 Rust 和 wasm 重新创建 macOS的 Drift 屏幕保护程序

[flux](https://github.com/sandydoo/flux) 是一个 Drift 屏幕保护程序。作者一直迷恋Macos 中的 Drift 屏幕保护程序。作者使用 Rust 和 wasm 重新在浏览器中创建了该效果。


### nushell 发布了 0.72 版本

[nushell](https://www.nushell.sh/blog/2022-11-29-nushell-0.72.html) ，或简称 Nu，是一种新的 shell，它采用现代的、结构化的方法来处理命令行。它与来自文件系统、操作系统和越来越多的文件格式的数据无缝协作，使构建强大的命令行管道变得容易。

NuShell 专注于实现以下目标：

-   创建具有现代感的灵活的跨平台Shell
-   允许你将命令行应用程序与可理解数据结构的Shell进行混合和匹配
-   具有现代命令行应用程序提供的用户体验优化

更多 nushell 功能可以参考 [nushell book](https://www.nushell.sh/zh-CN/book/) 


###  git-cliff:  根据 git 历史生成 ChangeLog 

[git-cliff](https://github.com/orhun/git-cliff) 可以通过 Git 的历史提交来生成 changlog. 并且可以自定义格式,过滤内容等。目前发布 1.0 版本。


### zellij :  终端工作区 

[zellij](https://github.com/zellij-org/zellij) 是一个终端工作区。它具有终端多路复用器的基本功能（类似于`tmux`或`screen`），但包含许多允许用户扩展它并创建自己的个性化环境的内置功能。zellij 支持 WebAssembly 和 WASI 来加载插件，因此可以使用任何能编译到 WebAssembly 的语言来编写插件。


###  gitoxide:  纯 Rust 编写的 git 实现

[gitoxide](https://github.com/Byron/gitoxide) 是一个 简洁, 快速, 安全的 纯 Rust 编写的 git 实现。

gitoxide 的性能超越了 Git ，可以在[一分钟内 clone linux 内核](https://github.com/Byron/gitoxide/discussions/579) 。 在 16 核 AMD 工作站上，`gitoxide`可以在 30 秒内实现相同的克隆，而`git`需要 141 秒。用数字表达，`gitoxide`性能比 `git` 好大约4.8倍。

### Hyperpom 基于 Apple Silicon 管理程序的 64 位 ARM 二进制模糊器

在没有源代码的情况下有效地对二进制文件进行模糊测试并不容易。Hyperpom 是纯 Rust 实现的基于 Apple Silicon 管理程序的 64 位 ARM 二进制模糊器，完全用 Rust 开发。它是基于变异测试（mutation-based）和覆盖率引导（coverage-guided）的。使用虚拟机管理程序可以完全控制目标二进制文件，并允许非常轻松地添加内省（introspection）机制。例如，我们可以实现代码覆盖率收集、挂钩系统、添加检测等。

Hyperpom 的架构非常标准。每个虚拟 CPU 运行一个 worker 来模糊其自己的二进制实例。然后这些实例共享信息，例如语料库和覆盖率数据，以加快该过程。目前 Hyperpom 还是很早期的项目，但值得关注。更详细信息可以参考[Hyperpom官方介绍](https://blog.impalabs.com/2211_hyperpom.html) 。


###  lapce: 快如闪电且功能强大的代码编辑器

[lapce](https://github.com/lapce/lapce) 纯 Rust 编写的，基于 [Druid](https://github.com/linebender/druid) 实现 UI （也是用 Rust 编写的）。它采用[Rope Science](https://xi-editor.io/docs/rope_science_00.html) 的  [Xi-Editor](https://github.com/xi-editor/xi-editor)设计，可实现闪电般的快速计算，并利用[OpenGL](https://www.opengl.org/)进行渲染。

虽然 Lapce  目前还处于 Pre-Alpha 阶段，不是一个完整的产品，但它可以提供很多东西，值得关注。

### helix: 后现代模态文本编辑器 

[helix](https://github.com/helix-editor/helix) 是一款用 Rust 实现的受 Kakoune / Neovim 启发的基于终端的文本编辑器。该编辑器的特点是：
- 类似 Vim 的模态编辑
- 多项选择
- 内置语言服务器支持
- 通过 tree-sitter 智能、增量语法高亮和代码编辑

目前发布了 22.12 版本，该版本是一个巨大的改进，新增了很多特性、完善了很多可用性改进点和 更多 Bug 修复等等。详细可以参考[Helix 官方信息](https://helix-editor.com/news/release-22-12-highlights/) 。

**同类型编辑器**：

- [zee](https://github.com/zee-editor/zee) ，灵感来自于 Emacs，一个实验性的现代终端编辑器。


### Spacedrive ： 开源的跨平台文件浏览器

[spacedrive](https://github.com/spacedriveapp/spacedrive) 是一个开源的跨平台文件浏览器，由用 Rust 编写的虚拟分布式文件系统( [VDFS](https://github.com/spacedriveapp/spacedrive#what-is-a-vdfs) )提供支持。

> VDFS（虚拟分布式文件系统）是一种旨在跨各种存储层工作的文件系统。通过统一的 API 来跨多个设备操作和访问内容，VDFS 不限于一台机器。它通过维护所有存储位置的虚拟索引、实时同步客户端之间的数据库来实现这一点。此实现还使用[CAS](https://en.wikipedia.org/wiki/Content-addressable_storage)（内容可寻址存储）来唯一标识文件，同时记录相对于存储位置的逻辑文件路径。可以在 Haoyuan Li 的这篇加州大学伯克利分校[论文](https://www2.eecs.berkeley.edu/Pubs/TechRpts/2018/EECS-2018-29.pdf)中找到 VDFS 的第一个实现。

`Spacedrive` 这个项目正在使用被称为“PRRTT（Prisma、Rust、React、TypeScript、Tauri）”的技术栈。2022 年还在积极开发中。Spacedrive 在 2022年得到了来自 OSS Capital 领投的 200 万美元融资。

###  Arti 1.0.0：准备用于生产

Arti 是 Rust 实现的 Tor 浏览器，目前已经可用于生产。更多信息可以参考[Arti 官方介绍](https://blog.torproject.org/arti_100_released/)。


### bytehound：Linux内存分析器

[bytehound](https://github.com/koute/bytehound) 是一款适用于 Linux 的内存分析器，由 C 和 Rust 实现。开销比 Valgrind 低很多，并且它具有更丰富的分析功能。（但当然它不能替代Valgrind，因为bytehound只能分析内存，而 Valgrind 还具有其他功能）。

有以下特点：

-   可用于分析内存泄漏，查看内存的确切位置，识别临时分配并调查过多的内存碎片。
-   收集每个分配和取消分配，以及完整的堆栈跟踪。
-   可动态剔除临时分配。
-   使用定制的堆栈展开实现，使其比其他工具更快。
-   可以将收集到的数据导出为各种不同的格式。
-   拥有基于 Web 的 GUI，可用于分析。
-   可以将分析数据动态流式传输到另一台计算机。
-   支持 AMD64、ARM AArch64 和 MIPS64 架构。
-   支持分析使用 jemalloc 作为其分配器的应用程序。
-   支持给予 Rhai 的嵌入式 DSL，允许编程和/或自动数据分析


### sniffnet : 多线程跨平台的网络分析器

[sniffnet](https://github.com/GyulyVGC/sniffnet)  由网络数据包嗅探器/过滤器组成，可以生成图形和文本报告，并提供丰富的统计信息。

###  privaxy: 下一代跟踪器和广告拦截器

[privaxy](https://github.com/Barre/privaxy) 是下一代跟踪器和广告拦截器，它通过 MITMing HTTP(s) 流量来阻止广告和跟踪器。

> MITMing HTTP(s) ，位于 HTTP(s) 对话应用程序（例如 Web 浏览器）和 HTTP 服务器（例如为网站提供服务的应用程序）之间。

通过在两端之间建立双向隧道，Privaxy 能够基于 URL 模式阻止网络请求，并将脚本和样式注入 HTML 文档。

Privaxy 优势：
- Privaxy 在更底层运行，比基于浏览器插件的拦截器更高效、更精简。小型虚拟机、服务器上的单个 Privaxy 实例，甚至是与流量来源相同的计算机上，每秒可以过滤数千个请求，同时需要非常少量的内存。
- Privaxy 不受浏览器 API 的限制，可以处理任何 HTTP 流量，而不仅仅是来自 Web 浏览器的流量。
- Privaxy 也比基于 DNS 的拦截器更强大，因为它能够直接操作 URL 并将资源注入网页。



## 图形渲染和处理


### Wgpu : 基于 WebGPU API的 Rust 图形库

[wgpu](https://wgpu.rs/) 适用于GPU上的通用图形和计算。使用wgpu的应用程序可以在Vulkan、Metal、DirectX 11/12和OpenGL ES上原生运行；也可以通过WebAssembly在WebGPU和WebGL2上运行浏览器。

wgpu 在 2022 年改进了不少功能。值得一提的是，现在 wgpu 可以通过独立的 features 来选择要支持的平台后端。默认情况下，wgpu 会根据目标操作系统和架构自动选择平台后端。并且，wgpu的DX12后端现在可以重新分配缓冲区和纹理，这可以显著提高性能。更多改进可以参考：[CHANGELOG](https://github.com/gfx-rs/wgpu/blob/master/CHANGELOG.md) 。

### rust-gpu:  旨在使Rust成为一流的GPU编程语言和生态系统

[EmbarkStudios 公司开源的 rust-gpu](https://github.com/EmbarkStudios/rust-gpu) 最新发布了 0.4 版本。截至目前，rust-gpu使用的是相当于Rust 1.66的Rust nightly。有一件事要特别强调：Rust-gpu现在[支持光线追踪](https://docs.rs/spirv-std/latest/spirv_std/ray_tracing/index.html)。使用`#[spirv(..)]`属性，你可以为各种光线追踪事件定义入口：相交、任意击中、最接近击中和错过。`#[spirv(ray_generation)]`可以用来定义一个光线生成着色器。

虽然该项目目前许多东西还没有实现，还远远没有达到可以投入生产的程度，但是该项目的前景是相当不错的。在游戏中，GPU编程以往都是通过编写HLSL或在较小程度上编写GLSL完成的。这些都是简单的编程语言。然而，随着游戏引擎的发展，这些语言未能提供处理大型代码库的机制。Embark 凭借拥有优秀的渲染工程师团队，希望通过将现有的、低级别的、安全的、高性能的 Rust 语言带到GPU上，来推动这个行业的发展。而随之而来的是一些不可忽视的额外好处：一个业界最好的包/模块系统，针对竞赛条件或越界内存访问的内置安全，广泛的工具和实用程序，以改善程序员的工作流程，以及其他许多东西。

rust-gpu 项目为 rustc编译器后端生成SPIR-V，通过`-Z codegen-backend`插入。
这与`rustc_codegen_cranelift`和`rustc_codegen_gcc`使用的机制相同。目前只计划支持SPIR-V，Vulkan的开放编译器目标。未来的版本可能会支持DXIL（DirectX的目标）或WGSL（WebGPU的着色语言，与SPIR-V是双投影的）。

###  forma: 实验性矢量图形渲染器

[forma](https://github.com/google/forma) 是 Google 开源的一个（完全）并行化的**实验性**Rust 矢量图形渲染器，具有软件（CPU）和硬件（GPU）后端，具有以下目标，顺序如下：

1.  **便携性**；支持 Fuchsia、Linux、macOS、Windows、Android 和 iOS。
2.  **性能**；利用在指令级和线程级都高度并行化的以计算为中心的管道。
3.  **简单**；实现一个易于理解的 4 级流水线。
4.  **尺寸**；最小化依赖项的数量并仅关注矢量图形。

它依靠 Rust 的 SIMD  auto-vectorization/intrinsics 和[Rayon](https://github.com/rayon-rs/rayon)在 CPU 上具有良好的性能，同时使用[WebGPU](https://github.com/gpuweb/gpuweb) ( [wgpu](https://wgpu.rs/) ) 来利用 GPU。


### Graphite:  重新定义最先进的图形编辑器

[Graphite](https://github.com/GraphiteEditor/Graphite) 是一个 Rust 实现的轻量级的光栅和矢量 2D 图形编辑器，它是免费和开源的。

Graphite 软件的第一要务是提供令人愉悦的用户体验。与其他一些开源应用程序不同，UI、UX 和产品设计不是事后才想到的，而是软件开发过程中的中心指路明灯。Graphite 建立在这样一种信念之上，即最好的创意工具可以是强大的并且触手可及。

目前 Graphite 已经可用于 alpha 测试。

### Mesa 22.3 的 Rusticl OpenCL 实现可以胜过 Radeon 的 ROCm 计算平台

[Mesa 22.3 发布](https://www.phoronix.com/news/Mesa-22.3-Released)，Mesa 是一个在MIT许可证下开放源代码的三维计算机图形库，以开源形式实现了OpenGL的应用程序接口。

Mesa 22.3 最值得注意的是 RDNA3“GFX11”AMD Radeon 图形支持有望在 Radeon RX 7000 系列中保持良好状态。Mesa 22.3 同样令人兴奋的是 Vulkan 光线追踪 (RT) 支持比之前的版本更加成熟和快速。

Mesa 22.3 向前迈出的另一个重要步骤是引入了[Rusticl](https://gitlab.freedesktop.org/mesa/mesa/-/tree/main/src/gallium/frontends/rusticl)作为 Gallium3D 的 Rust 编写的 OpenCL 实现。Rusticl 提供 OpenCL 3.0 支持，以及完整的图像支持。Red Hat 的 Karol Herbst 一直领导 Rusticl 的工作，作为现代 OpenCL 替代 Mesa 休眠的“Clover”OpenCL 状态跟踪器。随着这个新的 OpenCL 驱动程序出现在 Mesa 22.3 中，至少在他的 Radeon RX 6700 XT 显卡 (RDNA2) 测试中，[他发现 Rusticl 在相同的系统/硬件上可以胜过 ROCm 的流行 LuxMark 基准测试](https://www.phoronix.com/news/Rusticl-Outperformed-ROCm)。

###  lyon: 1.0 版本发布

[lyon](https://github.com/nical/lyon) 一个用 Rust 编写的路径细分库，用于基于 GPU 的 2D 图形渲染。 目前[lyon 正式发布 1.0 版本](https://nical.github.io/posts/lyon-1-0.html)。

lyon 从 2016 年开始开发，之所以迟迟发布 1.0 ，是因为作者希望 lyon 成长为一个功能齐全的 2D 渲染器。在达成这个目标的过程中，作者发现开发一个快速而健壮的曲面细分器本身就是一个大项目，所以就有了现在的 1.0 。





## UI


### Tauri  1.0 发布

[Tauri](https://tauri.app/) 是一个应用程序构建工具包，让你可以任何前端框架来构建桌面操作系统软件。核心库是用Rust编写的。2022 年发布了 1.0 版本，并且也发布了针对移动设备的 Tauri Mobile Alpha 版本。

Tauri 被认为是 Electron 的替代品，与 Electron 的区别：

- Tauri 程序安装包只有大约 2.5MB，而 Electron 程序安装包却有 85MB。
- Tauri 启动时间更快
- Tauri 占用内存更少（Linux 环境测试结果）
- Tauri 编写程序目前只支持 Rust，Electron 支持 JS 。但这一点 Tauri 正在改进。
- Tauri 使用系统 WebView；Electron 使用 Chromium
- Tauri 比 Electron 更加安全

**基于 tauri 开发的一些第三方工具**：

- [ChatGPT](https://github.com/lencx/ChatGPT)，用 tauri 打包的 ChatGPT 官网，并添加了一些其他方便的功能。
- [wirefish](https://github.com/stefanodevenuto/wirefish) ，一个类似 Wireshark 的跨平台数据包嗅探器。
- [tauri-tray-app](https://github.com/jondot/tauri-tray-app)，tauri 构建的桌面托盘应用。


####  tao ：Tauri 维护的窗口管理工具

[tao](https://github.com/tauri-apps/tao) 是 [winit](https://github.com/rust-windowing/winit) 的 Fork 版本，对 winit 增加了序列化反序列化和托盘（tray）特性支持。 


### Makepad Framework 发布第一个完整示例应用程序 Ironfish

[Ironfish](https://github.com/makepad/makepad/tree/master/examples/ironfish) 是一款功能丰富的合成器，该example crate [展示](https://makepad.nl/makepad/examples/ironfish/src/index.html)了 Makepad 框架的一些功能。

[makepad](https://github.com/makepad/makepad)，是一个 VR，Web和本机渲染UI框架 和 IDE，基于 Rust 和 WebAssembly （WebGL） 技术。 作者是 Cloud9 IDE 的创始人。该项目也包含[白皮书](https://link.zhihu.com/?target=https%3A//github.com/makepad/makepad_docs)，阐述了它的愿景。目前开发进度不是很频繁。

Makepad 由 Makepad Framework 和 Makepad Studio 组成。

Makepad Framework 是 UI 框架。它由多个板条箱组成，但顶级板条箱是[makepad-widgets](https://crates.io/crates/makepad-widgets)。有关 Makepad Framework 的进一步说明，请参阅该 crate 的自述文件。

Makepad Studio 是使用 Makepad Framework 构建的 IDE 的原型。它仍在大力开发中，但使用 Makepad Studio 的最终目标是创建一个 IDE，使应用程序的设计能够在运行时更改。Makepad Studio 的主要 crate 是[makepad-studio](https://crates.io/crates/makepad-studio)。Makepad Framework 应该是目前最快的 UI 框架。



### iced-rs : 

[iced](https://iced.rs/) 是用 [Rust](https://rust-lang.org/) 开发的跨平台 GUI 库。它受到[Elm](https://elm-lang.org/)的启发，Elm是一种用于构建 Web 应用程序的函数式语言。iced 非常注重**简单性**和**类型安全**。因此，iced 试图提供简单的构建块，而不是可以将它们与强类型放在一起以减少**运行时错误**的机会。

虽然 2022 年 iced 发展较慢，但是在System76 公司 `Pop!_OS`  的 [COSMIC 桌面中得以应用](https://www.phoronix.com/news/COSMIC-Desktop-Iced-Toolkit)。为什么用 iced 替换 GTK ，[System76 的工程师如是说](https://www.reddit.com/r/pop_os/comments/xs87ed/is_iced_replacing_gtk_apps_for_the_new_cosmic/)：

“由于 GObject、C 及其一般的布局和渲染方法，GTK 是效率最低的 GUI 工具包之一。每个小部件和数据片段都是一个单独的堆分配动态分配。布局算法必须通过从一个堆地址跳到另一个堆地址来从根小部件向下遍历到它的所有后代，以连接到树的每个小部件。现代处理器导航的最慢方式之一。

在 Iced 中，数据与小部件是分开的。您从一个应用程序结构开始作为您的模型，它存储您的应用程序在构建其布局时所需的所有状态。每当收到消息且状态已更改时，都会调用一个视图方法，此视图方法将整个布局一次性描述为状态机。然后比较和比较之前的布局，以便渲染器只渲染两者之间的差异。还有一些聪明的技术可以在未来用来减少所需的视图更新次数。

最好的部分之一是我们不需要在运行时使用 Iced 加载几十个大块的库。有一个完全静态二进制文件的选项。

GTK 的每个方面都被认为是当今软件开发和 GUI 架构的不良做法。除非丢弃所有代码并以与 Iced 类似的方式在 Rust 中从头开始创建新工具包，否则无法解决缺点。

最大的问题之一是您将数据、逻辑和 UI 深深地纠缠在一起。没有明确的分离，小部件是不纯的。您应该在需要与其数据或逻辑交互的任何地方创建和传递对小部件对象的引用的克隆。过去我已尽最大努力明确避免在我的 GTK 代码中这样做，因为这可能会导致难以维护的意大利面条怪物。

如果您在专业 Java 领域工作过一段时间，您可能听说过 MVC 模式。模型管理数据和逻辑，而视图管理布局和显示。控制器是将它们绑定在一起的粘合剂，将消息从视图传递到模型，反之亦然，从模型更新视图。

Elm 本质上是将数据和逻辑与 UI 隔离开来的另一种演变。所以当我说这是不好的做法时，这就是我所指的。将这些东西彼此分开通常被认为是一种好的做法。

在 GTK 中，小部件接受回调，调用者为这些回调提供函数。按预期使用它是一个巨大的错误。修复 GTK 应用程序的一般解决方案是通过基于消息的回调使其类似于 Elm。这可以通过为回调提供一个闭包来实现，该闭包拥有向应用程序或组件的事件循环发出消息的通道发送方的句柄。

但是无论你做什么，你都无法逃避这样一个事实，即每个小部件都是一个 GObject，它是从一个类实例化而来的，而这个类可能是另一个类的子类。创建自定义小部件所需的代码在 C 中非常乏味，在 Rust 中更是如此。

考虑到 GTK 是在面向对象编程非常流行的时候开发的面向对象框架。从那时起，情况发生了变化，今天设计的所有 GUI 框架都基于 Elm 架构，这更多地是在函数式编程方面。随着时间的推移，这种开发应用程序的方式只会越来越流行，一个接一个的 Web 框架采用它。

这是一种非常不同的 GUI 编程方式，其中状态与 UI 完全分离。您有一个事件循环，它存储生成其 UI 所需的所有状态，它负责响应 UI 消息，然后在其状态更改后生成更新的布局。获取该布局的差异并仅渲染更改的部分。这使得它非常高效，同时又易于读写。您的代码库可以保持干净，因为处理逻辑的代码与更新 UI 的代码完全分开。

实际上每个 Rust 框架都在使用这种方法，因为它与 Rust 的内存模型兼容。GTK 使用的面向对象架构与 Rust 的内存模型不兼容。这种方法对于开发 Web 应用程序和服务和 GUI 布局同样有效。我们已经可以看到 Elm 模型的优势非常大，以至于现在甚至 GTK 应用程序都在尝试用 Relm4 复制它。

就目前而言，使用 JS Web 框架开发界面已经大大超过了桌面工具包的体验，达到了令人尴尬的程度。我们需要赶上而不是忽视这一进展”

#### Relm4: 另一个受 Elm 启发的 GUI 框架

[Relm4](https://github.com/Relm4/Relm4) 是[受Elm](https://elm-lang.org/)启发并基于[gtk4-rs](https://crates.io/crates/gtk4)的惯用 GUI 库。Relm4 是 relm 的新版本，[它](https://github.com/antoyo/relm)是从头开始构建的，并且与[GTK4](https://www.gtk.org/)和[libadwaita](https://gitlab.gnome.org/GNOME/libadwaita)兼容。


### egui： 即时模式的 GUI 框架

[egui](https://github.com/emilk/egui) 是一个即时模式（immediate mode）、易于使用、可移植的库，用于在 Rust 中构建在网络、计算机和游戏引擎（开发中）上运行的 GUI。它的目标是成为用 Rust 构建本地和 Web 应用程序的最简单的库，也可以轻松地将它集成到游戏引擎中。

egui 在 2022 年也是积极开发中。egui 目前也被用到了商业环境，比如 [亚马逊 Prime Video](https://www.amazon.science/blog/how-prime-video-updates-its-app-for-more-than-8-000-device-types) 使用 egui 构建了一个用于调试场景渲染的应用程序。


###  slint:  GUI 工具包

[slint](https://slint-ui.com/blog/2022-in-review.html) 是一个GUI 工具包，可以高效地为任何显示器开发流畅的图形用户界面：嵌入式设备和桌面应用程序。支持多种编程语言，例如 Rust、C++ 或 JavaScript。

2022 年，slint 作为开源商业化产品，取得了很大的进展。2022 年 slint 发展回顾：
- 讲 SixFPS 改名为 slint，定义了品牌。
- 在2022第一季度被公认为[增长最快的 OSS 初创公司](https://runacap.com/ross-index/q1-2022)之一，年增长率为 470%！
- slint的[免费专有许可证](https://slint-ui.com/ambassador-program.html)开始受到关注：已有 15 位大使正在使用此免费许可证构建他们的项目
- 参加 [嵌入式世界展览和会议](https://twitter.com/slint_ui/status/1539920183351037952)，在那里展示了[Slint 在各种嵌入式设备上](https://slint-ui.com/thisweek/2022-06-27.html)的强大功能，包括功率非常低的[Raspberry Pi Pico](https://raspberrypi.social/@Raspberry_Pi/109473174195257886)
- 与多家设计和服务公司建立了[合作伙伴](https://slint-ui.com/#partners)关系计划
- 获得了六位数的种子资金来扩大团队：用于产品开发、销售和业务发展
- [作为白银会员加入 Rust 基金会](https://foundation.rust-lang.org/members) 
- 参加了[EuroRust 2022](https://eurorust.eu/)会议，Tobias 在会上介绍了[Rust 和 C++ 的互操作性](https://slint-ui.com//blog/rust-and-cpp.html)
- [Florian 在将 Slint 移植到Redox OS](https://redox-os.org/) 方面取得了惊人的进展 ，一些 [实用程序](https://gitlab.redox-os.org/redox-os/orbutils) 已经基于 Slint 
- 与PopOS 合作，使 Slint 成为开发人员的替代工具包

Slint 创始团队都是来自于 Qt 社区。


###  cxx-qt： 用于创建与[Qt](https://www.qt.io/)的双向 Rust ⇄ C++ 绑定

[cxx-qt](https://github.com/KDAB/cxx-qt) 是 KDAB数据咨询公司 （slint 的竞争对手/合作伙伴）创建的 与[Qt](https://www.qt.io/)的双向 Rust ⇄ C++ 绑定。可用于使用 CMake 将 Rust 集成到 C++ 应用程序中，或用于使用 Cargo 构建 Rust 应用程序。CXX-Qt 提供了在 Rust 中实现[QObject](https://doc.qt.io/qt-6/object.html)子类的工具，可以从 C++、QML 和 JavaScript 中使用。

目前处于早期开发阶段，API 经常更改。可以参考 [cxx-qt book](https://kdab.github.io/cxx-qt/book/) 来了解更多。


###  dioxus:  类 React 的 GUI 框架

[dioxus](https://github.com/dioxuslabs/dioxus) 是一个可移植、高性能且符合人体工程学的框架，用于在 Rust 中构建跨平台用户界面。可用于交付网络应用程序、桌面应用程序、静态站点、移动应用程序、TUI 应用程序、实时视图应用程序等。Dioxus 完全与渲染器无关，可以用作任何渲染器的平台。灵感来自于 React。

2022 年 Dioxus团队为了准备下一个大版本，主要贡献者之一Demonthos增加了一个期待已久的功能：子树记忆化（subtree memoization）。

子树记忆化减少了Dioxus将你所需要的UI状态传送到屏幕上所需要做的整体工作，提升了性能，以至于它将Dioxus推向了网络框架性能的前沿，与SolidJS等相提并论，甚至超过了Sycamore 0.8和Leptos 0.0.3等库。

dioxus 在 0.3 版本中即将引入新的LiveView渲染器。与其对应的Phoenix LiveView非常相似，Dioxus LiveView可实现完全由服务器渲染的应用程序和组件，同时向客户端发送最小的JS。在LiveView模型中，最大限度地减少延迟和带宽对保持应用程序的快速性至关重要，特别是对于低端客户端。



### flutter_rust_bridge:  用于 Flutter/Dart 和 Rust 的高级内存安全绑定生成器

[flutter_rust_bridge](https://github.com/fzyzcjy/flutter_rust_bridge)   是跨平台热重载快速开发 UI 工具包[Flutter和](https://flutter.dev/)[Rust](https://www.rust-lang.org/)之间的最佳结合。

Flutter 和 Rust 都是业界非常新颖的技术。为了实现跨平台，Flutter 自带了一个[MethodChannel的概念](https://docs.flutter.dev/development/platform-integration/platform-channels)，一个允许编写和调用平台本地代码的跨界接口。然后，它可以实现无缝集成，这在使用操作系统特定用户界面或本地访问设备外围设备时必不可少。得益于适当的集成机制，无需再进行调整。另一方面，Rust 在各种生态系统中越来越受欢迎，它作为通用编程语言变得越来越流行至少有几个原因。

当可用的原生编程语言`FlutterMethodChannel`无法派上用场时，比如想用 Rust 实现跨平台组件（Rust 实现跨平台组件是目前 Rust 应用的一个趋势），[flutter_rust_bridge](https://pub.dev/packages/flutter_rust_bridge)可能是解决方案。它允许通过外部生成的库在 Flutter 应用程序中使用 Rust 代码。


### Gtk-rs  发布了新版本

GTK是一个流行的跨平台、面向对象的部件工具包，由[GNOME项目](https://link.juejin.cn/?target=https%3A%2F%2Fen.wikipedia.org%2Fwiki%2FThe_GNOME_Project "https://en.wikipedia.org/wiki/The_GNOME_Project")开发。它被用来构建可移植的GUI应用程序，可以在Unix、Windows和macOS系统上使用多种语言，从Python到JavaScript、C和Rust。

`GTK4`是其`GTK`最新版本。`gtk-rs`是提供`rust`语言的`GTK`相关 库绑定。GTK库在开发者社区很受欢迎。许多流行的Linux GUI应用程序使用GTK库和GNOME栈。`gtk-rs` 库只是众多准备投入生产的Rust GUI库中的一个，已经在500多个项目中使用。

[Gtk-rs](https://github.com/gtk-rs) 在 2022 年的各个组件都有相应升级，比如，[gtk4-rs](https://github.com/gtk-rs/gtk4-rs) 发布到了 0.5.4 版本，升级了绑定的API，增加了更多异步支持。学习 Gtk-rs 可以参考官方 [Gtk-rs book](https://gtk-rs.org/gtk4-rs/stable/latest/book/) 。

###  fltk-rs ： FLTK Rust 绑定

[`fltk-rs`](https://link.juejin.cn?target=https%3A%2F%2Fgithub.com%2Ffltk-rs%2Ffltk-rs "https://github.com/fltk-rs/fltk-rs") 库为FLTK工具包提供Rust绑定。`fltk-rs` crate支持旧的架构，有80多个可定制的小部件和超过4个支持的主题方案，包括GTK方案。你也可以使用 [`fltk-theme`](https://link.juejin.cn?target=https%3A%2F%2Fcrates.io%2Fcrates%2Ffltk-theme "https://crates.io/crates/fltk-theme") crate来进行更多的定制。

[FLTK（Fast Light Toolkit）](https://link.juejin.cn?target=https%3A%2F%2Fwww.fltk.org%2F "https://www.fltk.org/")是一个轻量级、跨平台支持的工具包，用于构建GUI。FLTK支持Windows、macOS和UNIX系统，最初是为C++构建的。如果你使用FLTK工具包来创建一个GUI应用程序，该应用程序在所有支持的操作系统上看起来都是一样的。

fltk-rs 在 2022 年一直积极开发，最新发布了 1.3.25 版本。


### XiEditor 作者 Raphl 对未来Rust 生态中即将出现的十几个 GUI 工具的建议

[文章](https://raphlinus.github.io/rust/gui/2022/07/15/next-dozen-guis.html)关键摘要如下：

Raphl 断言，未来一两年 Rust 生态中会出现十几个 GUI 工具，所以他对这些即将出现的工具作出了中肯的建议。他认为，虽然可能大部分会是玩具，但是 Rust 中 GUI 还是非常有潜力的，Rust 将成为 GUI 工具包下一个主流语言。

他目前看好 [Druid](https://github.com/linebender/druid) 。Druid 主要是一个研究项目，特别关注高性能，但也解决了“真实 UI”的问题。研究目标是长期的；它不是一个旨在尽快发布可用工具包的项目。

目前 Rust GUI 基础设施存在着碎片化的状况，虽然有 egui、iced、tauri和druid等，但每隔几个月就会有新的GUI 工具包出现的文章。使用 Rust 构建 GUI 的动机非常强烈，因为社区非常渴望一种资源消耗较少的替代 Electron 的方案。但目前尚未达成一种替代方案共识。但是碎片化也不是坏事。UI 方法的多样性为实验和探索提供了丰富的基础，因为 Rust 中的 GUI 有很多方面我们仍然不知道最好的方法。

关于 GUI 的一个重要事实是，很少有明显正确的方法来做事，而且有很多很多的权衡。目前，这种权衡空间非常敏感，因为需求和优先级的微小差异可能最终导致相当不同的实现选择。我相信这是导致 Rust GUI 碎片化的主要因素。许多权衡与将平台功能用于各种事物的程度有关（其中文本布局和合成可能是最有趣的），而不是在平台抽象之上分层的这些功能的跨平台实现。

Raphl 的建议摘要：

1. 建议不要尝试确定 GUI 工具包是否是原生的，因为使用这种方法很难提供高质量的体验，主要是因为平台之间的阻抗不匹配，并且很少有成功的应用程序以这种方式交付。而是提出一组更精确的问题：
    - 简单应用程序的二进制大小是多少？
    - 一个简单的应用程序的启动时间是多少？
    - 文本看起来像平台原生文本吗？
    - 应用程序在多大程度上支持在系统级别设置的首选项？
    - 提供了预期文本控制功能的哪个子集？ （文本渲染、键盘布局、复制粘贴等等）

如果一个工具包在所有这些轴上都做得很好，那么我认为它是用“本地”技术构建的并不重要。

2. 在考虑窗口库时考虑替代方案。采用一个后，向其他人学习，看看如何改进你的。计划投入一些时间和精力来改善这一重要的基础设施。 社区中流行的一个窗口库winit，但是在实践中，我认为 winit 已经发展到对游戏用例非常满意，但对于 GUI 而言则不太令人满意。缺少大量功能，例如访问本机菜单（tauri的tao fork 背后的主要动机，以及iced 不支持系统菜单的原因）
3. 新的 UI 工具包应该弄清楚它们与系统合成器的关系。如果目标是提供真正流畅的本地内容集成（例如视频播放），那么他们必须投资于底层机制，就像浏览器一样。为合成器构建适当的跨平台基础设施是一项艰巨且有点吃力不讨好的任务。这些接口的表面积很大，我确信主要平台之间存在许多令人讨厌的差异，毫无疑问，需要大量的兼容性工程才能在旧平台上正常工作。浏览器已经投入到这项工作中（在 Safari 的情况下不需要跨平台），这实际上是使用 Web 技术堆栈的一个很好的理由。
4. 找出正确的文本策略。在短期内这样做是不可行的，但从长远来看，这是对“真实” UI 的要求。可能这也是 UI 工具包联合起来的一个领域。从长远来看，我希望拥有 Rust 生态系统基础设施crate来很好地处理文本，但这是一场艰苦的战斗。只是如何设计接口抽象边界是一个难题，而且很可能即使发布了一个好的 crate，也可能会遇到阻力，因为集成起来并非易事。有一些棘手的问题，例如富文本表示，以及文本布局crate如何与 2D 绘图集成。
5. 当然要尝试找出一个好的架构，但也要计划好它的发展。生态中还没有出现一个真正适合 Rust 语言的架构，直接采用其他语言的设计架构并不适合。Druid 本身有三个主要架构：将 ECS 模式应用于 UI 的初步尝试、当前严重依赖镜头的架构以及Xilem对未来架构的提议。中间是两次没有成功的探索。还有其他人体工程学方面的坑。因为 Rust 在函数调用中缺少命名参数和可选参数，所以向现有小部件添加可选修饰符是很痛苦的。 关于 Rust 中 UI 架构可以参考另一篇文章： https://raphlinus.github.io/rust/gui/2022/05/07/ui-architecture.html 
6. 尽早开始考虑可访问性，并尝试构建原型以充分了解高质量体验所需的内容。公平地说，除非 UI 工具包支持可访问性功能，例如支持视障用户的屏幕阅读器，否则不能将其视为生产就绪。不幸的是，可访问性支持经常退居二线，但幸运的是，情况看起来可能会有所改善。特别是，AccessKit项目希望为 Rust 生态系统中的 UI 工具包提供通用的可访问性基础设施。可访问性是 Web 技术栈的一大优势。在定义一个可以实际实现的跨平台抽象时花了很多心思，很多用户每天都依赖它。AccessKit 大量借鉴了 Web 方法，包括在 Chromium 中的实现。

关于 Druid 发展

随着时间的推移，Druid 可能会演变成一个可用于生产应用程序的工具包。与此同时，我们不想创造不切实际的期望。Druid 的主要受众是学习如何在 Rust 中构建 UI 的人。这篇文章不适合放置完整的路线图和愿景文档，但我希望及时写更多关于它的内容。


### GaiaX：动态化卡片跨端解决方案

[GaiaX](https://github.com/alibaba/GaiaX) 动态模板引擎是阿里巴巴优酷技术团队研发的一套轻量级的纯Native动态化卡片跨端解决方案。动态模板引擎是阿里巴巴优酷技术团队研发的一套轻量级的纯Native动态化卡片跨端（支持 Android 和 iOS）解决方案。

除了客户端渲染SDK，还提供了配套的模板可视化搭建工具和详情的功能Demo（模板示例，以及扫码预览），支持从模板搭建/编辑、真机调试/预览等研发链路技术支撑，优酷动态模板引擎的目标是在保证Native体验性能的同时，帮助客户端开发领域实现低代码。

更多介绍可参考[GaiaX 官方信息](https://developer.aliyun.com/article/1074185)。


### taffy：高性能的 Rust 驱动的布局库

[taffy](https://github.com/DioxusLabs/taffy) 是一个用 Rust 编写的灵活、高性能、跨平台的 UI 布局库，实现了基于 CSS 的布局算法，0.2.x 版稳定实现了 Flexbox 布局，对 CSS Grid 的支持处于预览状态。

未来计划支持更多的布局算法，详细可以参见 [官方跟踪Issue](https://github.com/DioxusLabs/taffy/issues/28)。

taffy 旨在用作其他 UI 和 GUI 库的依赖项。目前被以下项目所应用：

- [Dioxus](https://dioxuslabs.com/)：一个类似 React 的库，用于使用 Rust 构建快速、可移植和漂亮的用户界面
- [Bevy](https://bevyengine.org/)：符合人体工程学、ECS 优先的 Rust 游戏引擎

相对于另一个 Facebook 使用C++开发的库 [yoga](https://github.com/facebook/yoga)，taffy 支持的布局类型更多，并且性能更好。


## 游戏

### Fyrox : 2D/3D 游戏引擎

[Fyrox](https://github.com/FyroxEngine/Fyrox) （曾用名 rg3d）是一个功能丰富开箱即用的通用游戏引擎，适用于任何类型的游戏。使用该引擎制作的游戏能够在桌面平台（PC、Mac、Linux）和网络（WebAssembly）上运行。移动平台计划在未来发布。该引擎由两部分组成，你将积极使用：框架和编辑器。框架是引擎的基础，它管理着渲染、声音、脚本、插件等。而编辑器包含很多工具，可以用来创建游戏世界、管理资产、编辑游戏对象、脚本等。

2022 年该引擎进行了很多新的功能和现有的改进。包括新的动画编辑器、新的动画系统，以及更好的 WebAssembly 支持等等。目前发布版本为 0.28，已经可以用于生产环境。学习该引擎可以参考 [Fyrox book](https://fyrox-book.github.io/introduction.html) 。

### Bevy：0.9 发布

[Bevy](https://bevyengine.org/news/bevy-0-9/) 是一个用Rust构建的简单得令人耳目一新的数据驱动的游戏引擎。

今年 Bevy 主要的改进有如下方面：
- ECS 的人机工效学和性能改进，查询系统的人机工效学和可用性改进，以及 ECS 系统内部重构（V2 版本）。
- 反射系统改进，支持更多反射类型，包括枚举。
- 引入新的材质系统。
- 渲染器优化等等。

Bevy 虽然距离生产环境可用越来越近，但实际还有有很多工作要做：
- Bevy UI 还需要重新设计，之后才能进一步完善 Bevy Editior 
- 组件动画和三维骨骼动画
- ECS 系统进一步改进，比如 ”stageless“ 功能
- 3D 照明系统
- 更多 Bevy 场景功能和可用性改进

Bevy 是 Rust 生态最有潜力的游戏引擎之一，值得持续关注。


### godot-rust：  Godot 游戏引擎的 Rust 绑定

Godot 是一个跨功能、开源和免费的游戏引擎，根据 MIT 许可发布。它由阿根廷软件开发人员 Juan Linietsky 和 Ariel Manzur 于 2014 年开发，可在 Linux、Microsoft Windows 和 BSD 等多种操作系统上运行。除了为 PC、Web 和移动平台设计 2D 和 3D 游戏外，Godot 还可用于创建编辑器和其他非游戏软件。Godot 的架构是建立在节点的概念之上的，节点又在“场景”中组织起来。场景是可重用、可实例化和可嵌套的节点组。在 2D 游戏领域，Godot 可谓是相当成熟了。

2022 年 9月份 Godot 发布了 V4.0 版本。[godot-rust](https://github.com/godot-rust)  也跟随 Godot 的脚步在 11 月发布了 Godot V4.0 的 Rust 绑定库 [gdextension](https://github.com/godot-rust/gdextension) 。因为刚起步，目前该绑定库还处于早期，很多功能还未完善。但该库还在持续积极开发中。


### unreal-rust: Rust 与 虚幻引擎的一次尝试

[unreal-rust](https://github.com/MaikKlein/unreal-rust) 是Embark工作室的开发人员Maik Klein 将Rust集成到虚幻引擎中的一次成功尝试。但该项目仅仅是一次个人尝试，距离真正可用还有很多工作要做。



### pixels 像素帧缓冲器

[pixels](https://github.com/parasyte/pixels) 一个轻量的硬件加速的像素帧缓冲器。使用 pixels 可以迅速为一个简单的2D游戏、基于像素的动画、软件渲染器或你最喜欢的平台的仿真器制作原型。

建立在由[wgpu](https://crates.io/crates/wgpu)驱动的现代图形API上：Vulkan、Metal、DirectX 12、OpenGL ES3。对DirectX 11、WebGL2和WebGPU的支持还在进行中。

参考： [康威的生命游戏示例](https://github.com/parasyte/pixels/blob/main/examples/conway/README.md)



### Kira, 一个用于游戏开发的音频库

[Kira](https://rustcc.cn/github.com/tesselode/kira) 是用 [Rust](https://twitter.com/search?q=%23rustlang) 编写的用于游戏开发的音频库，并且具有不太常见的功能，例如平滑的补间参数和声音的精确定时，作者正在用它来制作一个动态生成的音乐游戏。

-   Repo github.com/tesselode/kira

同类型的库还有 [fundsp](https://github.com/SamiPerttu/fundsp) ，一个专注于可用性的音频 DSP（数字信号处理）库。

可用于：

-   游戏和应用程序的音频处理和合成
-   教育
-   音乐制作
-   声音 hacker 和音频 golfing
-   DSP 算法原型














## 人工智能



###  GraphScope: 

[GraphScope](https://github.com/alibaba/GraphScope)  是阿里巴巴达摩院智能计算实验室研发并开源的一站式图计算平台。GraphScope 的实现包含了 35% 的 Rust 代码。

GraphScope通过用户友好的 Python 界面提供一站式环境，用于在集群上执行各种图操作。GraphScope 依托于阿里海量数据和丰富场景，与达摩院的高水平研究技术，使计算集群上大规模图形数据的多阶段处理变得简单：包括用于分析、交互和图形神经网络 (GNN) 计算的 GRAPE、MaxGraph 和 Graph-Learn (GL) ，以及提供高效内存数据传输的[vineyard ](https://github.com/v6d-io/v6d)。

### burn:  深度学习框架 

[burn](https://github.com/burn-rs/burn) 是一个新的深度学习框架，支持CPU和GPU，使用新的 Rust 特性 GAT 功能来支持多个后端作为插件。

> 作者如是说：“总的来说，我一开始并没有 GAT，但我很快意识到有它比没有它要容易得多。”

这个库旨在成为一个用 Rust 编写的具有极高灵活性的且完整的深度学习框架。目标将是满足研究人员和从业者，使实验、训练和部署您的模型更容易。

用Rust编写的其他机器学习框架要么限制性太强（比如要求在编译时就知道矩阵的大小），要么API不够理想，要么缺少关键的功能，比如GPU支持。Burn 不一样，Burn 基于 `Backend` trait 架构来支持不同的后端。Burn 的目标是使创建优化的后端非常容易，并支持不同的设备和使用情况。目前，只有3个后端。[NdArray](https://github.com/rust-ndarray/ndarray)是一个纯粹的Rust解决方案，[Tch](https://github.com/LaurentMazare/tch-rs)是一个易于访问CUDA和cuDNN优化的操作，ADBackendDecorator使任何后端都可以区分。Burn 现在正在重构内部的后端API，使其尽可能容易插入新的API。

### BlindAI：机密 AI 推理服务器

Mithril Security 公司开源了[BlindAI](https://github.com/mithril-security/blindai)，这是一种用于机密推理的开源 AI 部署解决方案。

如今，大多数 AI 工具的设计机制都没有提供隐私保护，因此当数据被发送给第三方进行分析时，数据可能会遭到恶意使用或可能泄露。

与常规 AI 推理解决方案一样，BlindAI 帮助 AI 工程师为最终用户提供模型以从他们的预测中受益，但增加了隐私层。用户发送给 AI 模型的数据从传输到分析始终保密。这样，用户就可以从 AI 模型中受益，而无需向任何人公开他们的数据：AI 服务提供商和云提供商（如果有）都看不到这些数据。

BlindAI 通过使用特殊的硬件强制执行的可信执行环境来确保机密性。[要了解更多相关信息请在此处](https://blog.mithrilsecurity.io/confidential-computing-explained-part-1-introduction/)阅读官方博客系列。

BlindAI 包括了用 Rust 开发的安全推理服务器 和 用于安全使用远程 AI 模型的 Python 客户端 SDK。

### async-openai: OpenAI 接口的异步绑定

[async-openai](https://github.com/64bit/async-openai) 是 OpenAI REST API 的非官方 Rust 绑定，基于 [OpenAPI 规范](https://github.com/openai/openai-openapi) 。当API 服务器[限制速率](https://help.openai.com/en/articles/5955598-is-api-usage-subject-to-any-rate-limits)时，将使用指数退避重试非流式请求。


### faer-rs: 新的线性代数库

[faer-rs](https://github.com/sarah-ek/faer-rs) 是一个用 Rust 实现的线性代数例程的 crates 集合。目标是为线性代数提供一个功能齐全的库，重点关注可移植性、正确性和性能。


### 2022 年依旧积极开发维护的之前介绍过的机器学习框架和库

#### Linfa ： 机器学习工具包

[Linfa](https://link.zhihu.com/?target=https%3A//rust-ml.github.io/linfa/) 是一个 Rust 实现的 类似于 python scikit-learn 的库，旨在提供一个全面的工具包，可以使用 Rust 构建机器学习应用程序。该团队还创建了 Rust-ML 组织。

> “ scikit-learn，又写作sklearn，是一个开源的基于python语言的机器学习工具包。 它通过NumPy, SciPy和Matplotlib等python数值计算的库实现高效的算法应用，并且涵盖了几乎所有主流机器学习算法。  

更多资料可参考[Rust 机器学习之书](https://link.zhihu.com/?target=https%3A//rust-ml.github.io/book/)

#### tokenizers ： 自然语言处理分词库

[tokenizers](https://link.zhihu.com/?target=https%3A//github.com/huggingface/tokenizers) 是 Hugging Face 公司开源的一款 Rust 实现的分词库。

> Hugging Face 是一家总部位于美国纽约的聊天机器人初创服务商。该公司在 NLP界鼎鼎大名，三月份刚刚完成4000万美元B轮融资。在GitHub上发布了开源 NLP 库 Transformers。

基于深度学习的现代 NLP 管道中的瓶颈之一就是tokenization，尤其是通用性强且独立于框架的实现。所以，该分词器的核心是用Rust编写的，并且存在Node和Python的绑定。提供当今最常用的分词器的实现，重点是性能和通用性。

在 2022 年 tokenizers 被 [blindai](https://github.com/mithril-security/blindai) 团队[移植到了 WebAssembly 客户端](https://blog.mithrilsecurity.io/porting-tokenizers-to-wasm/)。


#### tch-rs ： PyTorch 的 Rust 绑定

[tch-rs](https://link.zhihu.com/?target=https%3A//github.com/LaurentMazare/tch-rs)是Pytorch的Cpp API的Rust绑定。 Tch Crate的目标是围绕 Cpp Pytorch API 提供一些薄的包装器。 它旨在尽可能接近原始的Cpp API。 然后可以在此之上开发更加惯用的 Rust 绑定。










##  物联网与嵌入式

### Rust 嵌入式生态库一些常用基础库

- [Probe-rs](https://probe.rs/)是一个调试工具包，用于将您的程序闪存到使用调试探针连接的 MCU。它支持 ST-Link、J-Link 和 CMSIS-DAP 硬件。用[Probe Run](https://github.com/knurling-rs/probe-run)最容易使用，所以大多数情况下不需要直接安装它。
- [Probe Run](https://github.com/knurling-rs/probe-run)用于刷新固件。设置完成后，`cargo run`如果连接了硬件探测器，则可以使用 ，从终端进行编译、刷新和调试。
- [cargo-embed](https://github.com/probe-rs/cargo-embed)是一个更灵活的`probe-run`替代品；它支持独立闪烁和 GDB 支持等功能。
- [Defmt](https://defmt.ferrous-systems.com/)是一个日志框架，能够提供一系列日志输出和级别。它包含一个`println!`类似于用于非嵌入式 Rust 的宏。它比 ITM 和其他日志记录库快得多。
- [Flip-Link](https://github.com/knurling-rs/flip-link)使用巧妙的技巧提供栈溢出保护。
- [Open OCD](https://openocd.org/)是一个开源的片上调试器，支持 Probe Run。
- [esp-rs](https://github.com/esp-rs)  提供的开源库旨在使[Rust 编程语言能够在](https://www.rust-lang.org/)[Espressif Systems](https://www.espressif.com/)生产的各种 SoC 和模块上使用。
- [stm32-rs](https://github.com/stm32-rs/stm32-rs) 为所有 STM32 微控制器提供 Rust 设备支持包，使用 [svd2rust](https://github.com/rust-embedded/svd2rust)和社区构建的基本 SVD 文件补丁集合为该设备的外围设备提供安全的 API。
- [ravedude](https://github.com/Rahix/avr-hal/tree/main/ravedude) 用于在 AVR 微控制器上无缝运行 Rust 代码。它是一个`avrdude`包装器，可以轻松访问目标的串行控制台，类似于 Arduino IDE。


###  embassy: 嵌入式异步运行时

[embassy](https://github.com/embassy-rs/embassy) 是 Rust 实现的嵌入式异步开发框架，旨在使 async/await 成为嵌入式开发的一流选择。它可以被视为 Tokio 的嵌入式等价物。它使用 Rust 的内置异步语法来处理并发。在内部，Embassy 的异步功能封装了中断和 DMA。

embassy 包括自己的 HAL 和自己的 STM32 PAC。它的独特目标是为所有受支持的 STM32 设备提供统一的 API 和单一库。这使得在不同 STM32 变体之间调整代码变得更加容易，并提供更小的维护表面。[通过使用独立的metapac crate](https://crates.io/crates/stm32-metapac)，它可以用作独立的库，无需 Embassy Async 框架或 HAL 。


### embedded-hal 发布 1.0 alpha 9 版本

[embedded-hal](https://github.com/rust-embedded/embedded-hal) 是构建平台无关驱动程序生态系统的基础。目前正在努力稳定 1.0 版本过程中。

这个库提供了许多 Rust 特性，每个特性都用于描述外围设备的功能。它的优势在于，通过将驱动程序编写为驱动程序之上的通用库，`embedded-hal`作者可以支持任意数量的目标平台（例如 Cortex-M 微控制器、AVR 微控制器、嵌入式 Linux 等）。


###  RustSBI 0.3.0 正式版现已发布

[RustSBI](https://github.com/rustsbi/rustsbi) 是 RISC-V 下 SBI 标准的实现，旨在为裸机平台、虚拟化和模拟器软件提供良好的 SBI 接口支持。它有机结合了 Rust 嵌入式生态与 RISC-V 系统软件，加快开发速度的同时，保证 Rust 语言具备的良好安全性和运行性能。本次 0.3.0 版本主要包括增加了实例化的 SBI 接口支持及相关的构造器结构，可以在 stable Rust 编译，去除了对堆内存和全局变量的依赖，完善了相关文档，以及若干的小修复。0.3.0 版本更新将为 Rust 编写的 RISC-V 虚拟化软件和 RISC-V 模拟器提供良好的支持，并进一步完善裸机 RISC-V 开发的实用性，可以启动 Linux 等在内的成熟操作系统和 zCore 等在内的科研操作系统。


###  rumqtt:  构建  mqtt  的 Rust 生态

[rumqtt](https://github.com/bytebeamio/rumqtt) 是一组用 rust-lang 编写的开源库，用于实现 MQTT 标准，同时力求简单、健壮和高性能。

rumqtt 是 Bytebeam 物联网咨询公司开源的 MQTT 代理。rumqtt 目前版本已经发布到了 R19 版，并未按语义化版本来发布。

新版本改进：
- 新的版本提升了性能和可靠性（可以支持 多达 10,000 多个 MQTT 客户端，使用 [mqttwrk](https://github.com/bytebeamio/mqttwrk) 进行基准测试）
- 添加了一个用于测试 rumqttd 的公共服务器
- 添加了 Prometheus 集成和其他优化更改
- 加了对存储支持的持久性的实验性支持，以确保消息的零数据丢失

rumqtt 将在 2023 年初推出对 MQTT v5 的支持。

### NTP 用 Rust 重写了

互联网安全研究小组的[Prossimo项目与 weedegolf 合作](https://www.memorysafety.org/initiative/ntp/)，用 Rust 重写 Network Time Protocol (NTP) ，以提供[内存安全的 NTP](https://github.com/memorysafety/ntpd-rs)。此举是将互联网最关键的基础设施转移到内存安全代码的任务的一部分。

NTP是互联网跟踪时间的方式，今天在数十亿设备上运行。网络时间协议（network time protocol）使连接到网络的设备之间的时间达成同步。该项目源自 Prosimo 的倡议，并得到 Cisco 和 AWS 的支持。其首要的短期目标是在 Let's Encrypt 部署该实现。而长期目标是开发一个可广泛使用的、功能齐全的网络时间协议替代实现。




  



  






##  编程语言

目前生态中用 Rust 实现新的语言有很多，具体可以参考[langs-in-rust](https://github.com/alilleybrinker/langs-in-rust) 。

### Rhai :  Rust 实现的嵌入式脚本语言和执行引擎

[rhai](https://github.com/rhaiscript/rhai) 是一种类似于 JavaScript+Rust 的[动态](https://rhai.rs/book/language/dynamic.html)类型的简单语言，也称为 RhaiScript。它提供了一种安全、简单的方法来向任何 Rust 应用程序添加 DSL 脚本。与其他脚本语言（如 JavaScript）相比，Rhai 是内存安全的。Rust 的核心原则之一是内存安全，因此 Rhai 始终在受控环境中运行——Rhai 脚本无法更改其环境中的任何值，并且始终在沙箱中运行。

Rhai 的一些局限：
-   脚本编写能力有限：Rhai 不支持类或其他复杂的数据结构，因此 Rhai 最适合编写实用程序脚本而不是完整的应用程序。
-   没有正式的语言语法：与 JavaScript 或 Lua 等脚本语言不同，Rhai 缺乏正式的语言语法。这限制了 Rhai 在面向对象语法方面的能力，例如使用继承、接口或泛型。

**Rhai 其他替代语言**

- [glsp](https://github.com/fleabitdev/glsp) ，即Gamelisp， 可以轻松地与 Rust 集成，并且在编写游戏方面比 Rhai 具有更多的功能。GameLisp 有一个独特的垃圾收集器，专为游戏开发而设计。它每帧运行一次，每一帧，而不会导致任何延迟峰值。还有内存安全以及与 Rust api 的无缝集成。
- [goscript](https://github.com/oxfeeefeee/goscript) ，Go语言风格的脚本语言，可嵌入到Rust项目。

###  gleam :  Rust 实现的运行在 Erlang 虚拟机的语言

[gleam](https://github.com/gleam-lang/gleam) 是一种友好的语言，用于构建 可扩展的类型安全系统！除了 Erlang 虚拟机也可用于 JavaScript 运行时。Gleam 语言被设计为尽可能小和一致，从 Elm、Go 和 Lua 等其他语言中汲取灵感，所以 Gleam 缺少异常、宏、类型类、提前返回和各种其他功能，而只使用一流的函数和模式匹配。Gleam 程序中的所有流程控制都是显式的，所有功能都是根据传递给函数和从函数返回的数据构建的。

Gleam 带有内置的编译器、构建工具、格式化程序、编辑器集成和包管理器，因此创建一个 Gleam 项目只是运行`gleam new`。作为更广泛的 BEAM 生态系统的一部分，Gleam 程序可以使用数千个已发布的包，无论它们是用 Gleam、Erlang 还是 Elixir 编写的。

目前 Gleam 发布了 V0.25 版本，引入了一种新的语法：`use` 表达式。它是一种语法糖，它将所有后续表达式转换为一个匿名函数，该函数作为附加参数传递给函数调用。


### 纯 Rust 实现的 JS 引擎

Boa 是一个用 Rust 编写的实验性 Javascript 词法分析器、解析器和编译器。目前，它支持某些语言。它可以很容易地嵌入到 Rust 项目中，也可以从命令行使用。Boa 也作为 EcmaScript 规范的 Rust 实现而存在，在某些领域我们可以利用 Rust 及其出色的生态系统来制作快速、并发和安全的引擎。

Boa 目前[发布了 v0.16 版本](https://boa-dev.github.io/posts/2022-09-25-boa-release-16/) 。Boa目前支持部分JavaScript语言。v0.16 版本对官方 ECMAScript 测试套件 (Test262) 中的一致性覆盖率达到 74.53%。目前已经支持 ECMAScript Promises。

Boa 也支持 WebAssembly 。如何在 Rust 项目中支持 JS 可以参考： https://boa-dev.github.io/posts/2022-10-24-boa-usage/

**其他同类项目：**

- [dune](https://github.com/aalykiot/dune) ，同时支持 JavaScript 和  TypeScript 的运行时。


### HVM :  纯函数式运行时

[HVM](https://github.com/Kindelia/HVM) （High-order Virtual Machine）是 Rust 实现惰性、非垃圾收集和 大规模并行的纯函数式运行时。它可以比替代方法（包括 Haskell 的 GHC）性能指数级的快，与 GHC 相比，HVM 有两个主要优势：自动并行性和 beta 最优性。由于一种新的计算模型**Interaction Net**取代了**图灵机**和**Lambda 微积分**，该模型以前的实现在实践中效率低下，但是，最近的突破大大提高了它的效率，从而产生了 HVM。HVM 类似于函数式语言领域的 LLVM。

> 开源项目[Kind](https://github.com/kindelia/kind)和[HVM](https://github.com/kindelia/hvm)的作者 Victor Taelin ，收到一位社区中有影响力的人的如是批评：“这个项目背后的人往往会建立令人印象深刻的东西，但后来他突然放弃了这些东西，然后去做点别的……”。 这份批评让 Victor 非常难过，因为这位来自社区有影响力的人也给予了 Victor 很多灵感。Victor 公开声明：“**我们只是没有资金**！看，这不是大公司的工作，甚至不是大团队的工作。80% 的代码仍然是我做的。有一些朋友帮忙，但他们大多是兼职，自愿，还在学习这东西，所以帮助有限。然而，什么都没有被放弃。我们只是受到我们微小规模的限制。我没有报酬，这不是一家营利性公司，我只是一个创造酷炫、免费技术以推动人类进步的人。我热爱我的工作！不过，如果您确实希望看到我的想法更快地发展，请考虑对它们进行投资”。Victor 说：不管怎样，HVM 和 Kind 都在积极、热情的开发中，并将继续向前发展，即使有点慢！
>  来自社区的另一位回复非常暖心：“老实说，即使你放弃了你的项目，我仍然会感谢你的工作。你的输出是创新的，我可以看到它们影响未来的 PL 发展。就我个人而言，我认为你对我自己产生了积极的影响，并且确实帮助激发了我对类型理论的兴趣。综上所述，请不要让一些误导性的批评使您沮丧。只要继续做你最擅长的事情，你就会知道这些年来你已经赢得了很多感激的支持者。”


### Glicol - 以图为导向的音乐实时编程语言

[Glicol](https://github.com/chaosprint/glicol) 支持用户可以使用代码编写音乐。用 Rust 编写，得益于 WebAssembly，它可以在浏览器中丝滑运行。

###  starlark-rust : starlark 语言的 Rust 实现

Tensorflow， Envoy， Kubernetes， KubeVirt 等等大型项目都是用 Bazel 构建的，要参与开发这些项目或者基于这些项目做开发，不能避开Bazel，且Bazel是当前开源Build System里最先进也最代表着未来方向的产品，非常有必要掌握。

Starlark 是一门配置语言，设计之初是为了作为 Bazel 的配置语言，Starlark语法类似 Python，但不是Python，保持语言类似于 Python 可以减少学习曲线，使语义对用户更加明显。与 Python 显著不同的地方在于，独立的 Starlark 线程是并行执行的，因此 Starlark 工作负载在并行机器上可以很好地伸缩。

[starlark-rust](https://github.com/facebookexperimental/starlark-rust/) 是 Meta（原 facebook） 团队对 Starlark 语言的 Rust 实现。


### KCL: 基于约束的记录及函数语言

K8s已经成为云计算的操作系统，但是目前尚缺少功能完备的SHELL交互界面。目前虽然有很多而且开源方案，但是还没有像UNIX的Shell那种出现比较成熟的方案，特别是尚无法满足头部互联网企业大规模工程化的要求。云原生技术与企业落地之间存在Gap需要填补，这正是云原生工程化要解决的问题，也是设计KCL语言的出发点。

蚂蚁集团 Kusion 配置语言（KCL）是一个开源的基于约束的记录及函数语言。[KCL](https://github.com/KusionStack/KCLVM) 通过成熟的编程语言技术和实践来改进对大量繁杂配置比如云原生场景的编写，致力于构建围绕配置的更好的模块化、扩展性和稳定性，更简单的逻辑编写，以及更快的自动化集成和良好的生态延展性。


###  stc: 用 Rust 重新实现 TypeScript 类型检查器

[stc](https://github.com/dudykr/stc) 是 tsc 的直接替代品，支持 "所有类型和类型推理"，包括所有复杂的泛型、条件类型和模板字面。

stc 是 swc 作者 [Donny (GitHub id 是 kdy1）](https://github.com/kdy1) 新的目标。用 Donny 的话来说，“官方 TypeScript 类型检查器`tsc`非常慢”。这意味着在 VSCode 中，红线和警告需要很长时间才能在大型项目上更新。

主要问题是它`tsc`本身是“用不支持并行处理的 TypeScript 编写的”。用原生语言重写`tsc`，比如 Rust，可以极大地加快速度。

但是有一个问题。重写像 TypeScript 这样的库是极具挑战性的。首先，TypeScript 的行为“缺乏规范”。Donny's 不得不推断 TypeScript 的行为，主要是单独测试用例。

TypeScript 的纯粹大小令人望而生畏。它有十年的时间来迭代、发展和添加功能。看一眼 TypeScript 的[2.6MB`checker.ts`文件](https://github.com/microsoft/TypeScript/blob/main/src/compiler/checker.ts)就足以吓跑大多数人。

TypeScript 的速度非常快。用唐尼的话来说，这“太快了”。它是世界上最活跃的开源项目之一。对于一个开发人员来说，跟上一个庞大的团队似乎是不可能的。

但 Donny 有信心。“我认为地球上没有其他人能够也愿意这样做。[...]许多人没有足够的精力来研究这样的长期项目。”


###  pomsky:  现代化的正则表达式语言

[pomsky](https://github.com/rulex-rs/pomsky) 是 Rust 实现的现代化的正则表达式语言。

普通的正则表达式非常简洁，但是当它们变长时，它们会变得越来越难以理解。默认情况下，他们没有注释，空格很敏感。然后是大量的印记和反斜杠转义符，它们没有遵循可辨认的系统： `(?<=) (?P<>) .?? \N \p{} \k<> \g''`等等。由于正则表达式实现之间存在各种不一致，因此很容易造成混淆。

Pomsky 使用一种新的、更简单但也更强大的语法解决了这些问题：

-   它对空格不敏感并允许注释
-   文本必须出现在引号中。这使得表达式更长，但也更容易阅读
-   非捕获组是默认的
-   更直观、一致的语法
-   支持使表达式 DRY 的变量


###  RustPython:  Rust 实现的 Python 解释器

[RustPython](https://github.com/RustPython/RustPython) 可以嵌入到 Rust 程序中以使用 Python 作为应用程序的脚本语言，或者可以将其编译为 WebAssembly 以便在浏览器中运行 Python。

RustPython 2022 年还在积极开发中，目前 RustPython 还不能完全用于生产环境。但考虑到它的发展潜力，还是有一些项目使用了它：
-   [GreptimeDB](https://github.com/GreptimeTeam/greptimedb)：一个开源的、云原生的、分布式的时间序列数据库。使用 RustPython 进行嵌入式脚本编写。
- [Robot Rumble](https://github.com/robot-rumble/logic/)：基于竞技场的人工智能竞赛平台
- [Ruff](https://github.com/charliermarsh/ruff/)：一个极快的 Python linter，用 Rust 编写，也比较受欢迎。
