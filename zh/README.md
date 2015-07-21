<img src="images/cover.png"/>

# About this book 关于本书

This is a book on the functional paradigm in general. We'll use the world's most popular functional programming language: JavaScript. Some may feel this is a poor choice as it's against the grain of the current culture which, at the moment, feels predominately imperative. However, I believe it is the best way to learn FP for several reasons:
总之，这是一本关于函数范例的书。我们将采用世界上最流行的函数编程语言：JavaScript。一些人可能会认为这是个差强人意的选择，因为它违背当前文化的成果，在目前，这是感觉非常必要的。然而，我相信这是最好的学习fp的方式，有如下理由：

 * You likely use it every day at work. 你可能每天都会在工作中使用它。

    This makes it possible to practice and apply your acquired knowledge each day on real world programs rather than pet projects on nights and weekends in an esoteric FP language.
    这使得它可以练习并将你每天所得到的知识运用于真实世界的程序中而不是夜晚和周末，在一个深奥的FP语言中的宠物项目。

 * We don't have to learn everything up front to start writing programs.我们不必在写程序前预先学会所有东西。

    In a pure functional language, you cannot log a variable or read a DOM node without using monads. Here we can cheat a little as we learn to purify our codebase. It's also easier to get started in this language since it's mixed paradigm and you can fall back on your current practices while there are gaps in your knowledge.
    在纯粹的函数语言中，不使用 monad 便不能记录变量或读取DOM节点。这里我们在学习净化代码库时，可以作个小弊。由于这是混合范例，在开始学习这种语言时也会更简单，当你知识不够充裕时可以把当前的练习放下回头再看。


 * The language is fully capable of writing top notch functional code.这种语言完全可以编写高级函数代码。

    We have all the features we need to mimic a language like Scala or Haskell with the help of a tiny library or two. Object-oriented programming currently dominates the industry, but it's clearly awkward in JavaScript. It's akin to camping off of a highway or tap dancing in galoshes. We have to `bind` all over the place lest `this` change out from under us, we don't have classes[^Yet], we have various work arounds for the quirky behavior when the `new` keyword is forgotten, private members are only available via closures. To a lot of us, FP feels more natural anyways.
    在一或两个迷你图书馆的帮助下，我们有所有模仿一种语言如Scala或Haskell所需的特征。面向对象编程目前操控着这项产业，但是这在JavaScript中明显有些尴尬。这就像是在公路上露营或者穿着胶套鞋跳踢踏舞。我们要“结合”所有以免“这”改变发生，我们没有类，当一个“新的”关键词被遗忘，对于这个奇怪的行为，我们周围有多种不同的工作，私有成员只能通过闭包获得。对于我们很多人，FP毕竟感觉更自然些。

That said, typed functional languages will, without a doubt, be the best place to code in the style presented by this book. JavaScript will be our means of learning a paradigm, where you apply it is up to you. Luckily, the interfaces are mathematical and, as such, ubiquitous. You'll find yourself at home with swiftz, scalaz, haskell, purescript, and other mathematically inclined environments.
这就是说，写出的函数语言将，毫无疑问，是代表本书风格的最好的编码。JavaScript将是我们学习范例的方式，在哪用它完全取决于你。幸运的是，界面时数学的并且，就其本身而论，它是无处不在的。你将发现你自己在家还有swiftz,scalaz,haskell,purescript,和其他数学倾向环境。

# Table of Contents目录

## Part 1第一部分

* [Chapter 1: What ever are we doing?](ch1.md)第一章：我们到底在做什么？
  * [Introductions](ch1.md#introductions)介绍
  * [A brief encounter](ch1.md#a-brief-encounter)一个短暂的邂逅
* [Chapter 2: First Class Functions](ch2.md)第二章：一级函数
  * [A quick review](ch2.md#a-quick-review)一个快速的回顾
  * [Why favor first class?](ch2.md#why-favor-first-class)为什么赞成一级？
* [Chapter 3: Pure Happiness with Pure Functions](ch3.md)纯粹的快乐和纯粹的函数
  * [Oh to be pure again](ch3.md#oh-to-be-pure-again)哦，再次纯粹
  * [Side effects may include...](ch3.md#side-effects-may-include)副作用可能包含……
  * [8th grade math](ch3.md#8th-grade-math)八年级数学
  * [The case for purity](ch3.md#the-case-for-purity)关于纯粹
  * [In Summary](ch3.md#in-summary)总言
* [Chapter 4: Currying](ch4.md)柯里化
  * [Can't live if livin' is without you](ch4.md#cant-live-if-livin-is-without-you)没你不能活
  * [More than a pun / Special sauce](ch4.md#more-than-a-pun--special-sauce)不止是双关／特别的调料
  * [In Summary](ch4.md#in-summary)总言
* [Chapter 5: Coding by Composing](ch5.md)第五章：创作编码
  * [Functional Husbandry](ch5.md#functional-husbandry)函数农耕
  * [Pointfree](ch5.md#pointfree)自由点
  * [Debugging](ch5.md#debugging)调试
  * [Category Theory](ch5.md#category-theory)范畴论
  * [In Summary](ch5.md#in-summary)总言
* [Chapter 6: Example Application](ch6.md)第六章：范例应用
  * [Declarative Coding](ch6.md#declarative-coding)声明性编码
  * [A flickr of functional programming](ch6.md#a-flickr-of-functional-programming)函数编程浏览
  * [A Principled Refactor](ch6.md#a-principled-refactor)规则重构
  * [In Summary](ch6.md#in-summary)总言

## Part 2 第二部分

* [Chapter 7: Hindley-Milner and Me](ch7.md)第七章：欣德利－米尔纳和我
  * [What's your type?](ch7.md#whats-your-type)你是什么类型？
  * [Tales from the cryptic](ch7.md#tales-from-cryptic)神秘的寓言
  * [Narrowing the possibility](ch7.md#narrowing-the-possibility)缩小可能性
  * [Free as in theorem](ch7.md#free-as-in-theorem)像在定理中一样自由
  * [In Summary](ch7.md#in-summary)总言
* [Chapter 8: Tupperware](ch8.md)第八章：特百惠
  * [The Mighty Container](ch8.md#the-mighty-container)大容器
  * [My First Functor](ch8.md#my-first-functor)我的第一个functor
  * [Schrödinger’s Maybe](ch8.md#schrodingers-maybe)薛定谔的或许
  * [Pure Error Handling](ch8.md#pure-error-handling)单纯错误解决
  * [Old McDonald had Effects…](ch8.md#old-mcdonald-had-effects)老麦当劳有影响……
  * [Asynchronous Tasks](ch8.md#asynchronous-tasks)异步任务
  * [A Spot of Theory](ch8.md#a-spot-of-theory)一些理论
  * [In Summary](ch8.md#in-summary)总言
* [Chapter 9: Monadic Onions](ch9.md)第九章：单细胞洋葱
  * [Pointy Functor Factory](ch9.md#pointy-functor-factory)
  * [Mixing Metaphors](ch9.md#mixing-metaphors)混合隐喻
  * [My chain hits my chest](ch9.md#my-chain-hits-my-chest)我的链子打到了我的胸
  * [Theory](ch9.md#theory)理论
  * [In Summary](ch9.md#in-summary)总言


# Plans for the future 未来计划

* Part 1 is a guide to the basics. I'm updating as I find errors since this is the initial draft. Feel free to help!
* 第一部分是基础引导。由于这是初稿，我在发现错误中会不断更新。乐于解疑。
* Part 2 will address type classes like functors and monads all the way through to traversable. I hope to squeeze in transformers and a pure application.
* 第二部分全程讲类型类如functor和monad。我希望可以压缩变形和单纯的应用。
* Part 3 will start to dance the fine line between practical programming and academic absurdity. We'll look at comonads, f-algebras, free monads, yoneda, and other categorical constructs.
* 第三部分将指出实践性编程和学术谬论之间的完美界限。我们会看一下指令，f－代数，自由monads，yoneda和其他几何结构。

