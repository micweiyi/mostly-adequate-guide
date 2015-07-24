# Chapter 1: What ever are we doing? 我们到底在做什么？

## Introductions 介绍

Hi I'm Professor Franklin Risby, pleased to make your acquaintance. We'll be spending some time together as I'm supposed to teach you a bit about functional programming. But enough about me, what about you? I'm hoping you're familiar with the JavaScript language, have a teensy bit of Object-Oriented experience, and fancy yourself a working class programmer. You don't need to have a Ph.D in Entomology, you just need to know how to find and kill some bugs.
你好，我是富兰克林 里斯比教授，很高兴认识你。我们会在一起呆一段时间，我将教你们一些关于函数编程的东西。但是这对我来说很充裕，你呢？我希望你熟悉JavaScript语言，有一点面向对象的经验，并认为自己是一个工薪阶级的程序员。你不需要有一个昆虫学的博士学位，你只需要知道怎么找出并解决掉bug。

I won't assume any previous functional programming knowledge because we both know what happens when you assume, but I will expect you to have run into some of the unfavorable situations that arise from working with mutable state, unrestricted side effects, and unprincipled design. Now that we've been properly introduced, let's get on with it.
我不会假定任何之前的函数编程知识，因为我们都知道当你假设时会发生什么，但我希望你能体验一些并不讨喜的情况，因为不稳定状态，非限制性副作用，和无原则性设计。既然我们已经恰当的介绍了，那就步入正题吧。

The purpose of this chapter is to give you a feel for what we're after when we write functional programs. We must have some idea about what makes a program *functional* or we'll find ourselves scribbling aimlessly, avoiding objects at all costs - a clumsy endeavor indeed. We need a bullseye to hurl our code toward, some celestial compass for when the waters get rough.
这个章节意在让你体验当我们写函数程序时之后会怎么样。我们必须知道是什么使程序函数化否则只会发现自己碌碌无为，事倍功半。我们需要一个目标使代码一往直前，当水变混时有指南星指明方向。

Now there are some general programming principles, various acronymic credos that guide us through the dark tunnels of any application: DRY (don't repeat yourself), loose coupling high cohesion, YAGNI (ya ain't gonna need it), principle of least surprise, single responsibility, and so on.
现在有几条通用编程准则，各种首字母缩略信条指引我们通过各种应用的黑暗隧道：DRY(don't repeat yourself 不要自己重复)，低耦合高聚合，YAGNI(ya ain't gonna need it 你不会需要它的)，最低惊喜的原则，个体的责任，等等。

I won't belabor listing each and every guideline I've heard throughout the years... the point is that they hold up in a functional setting, though they're merely tangential to our goal. What I'd like you to get a feel for now, before we get any further, is our intention when we poke and prod at the keyboard; our functional Xanadu.
我不会反复讨论罗列这些你我所听到的每一条指导……关键是尽管他们只是偏离了我们的目标，他们仍存在于函数设置中。现在我想让你们体会的，在我们进行深一步探究前，时当我们敲击键盘时的目的；我们函数的Xanadu。

<!--BREAK-->

## A brief encounter 一个简单的邂逅

Let's start with a touch of insanity. Here is a seagull application. When flocks conjoin they become a larger flock and when they breed they increase by the number of seagulls with whom they're breeding. Now this is not intended to be good Object-Oriented code, mind you, it is here to highlight the perils of our modern, assignment based approach.
让我们想从接触疯狂开始。这里是一个海鸥应用。当群体结合，它们变成了一个更大的群体，当它们繁殖时，它们增多了同它们一起繁殖的海鸥的数量。现在这并不是要写出一份好的面向对象的代码，请注意，就是这突出了我们现代，以任务为基础的方法中的危险。

Behold: 看：

```js
var Flock = function(n) {
  this.seagulls = n;
};

Flock.prototype.conjoin = function(other) {
  this.seagulls += other.seagulls;
  return this;
};

Flock.prototype.breed = function(other) {
  this.seagulls = this.seagulls * other.seagulls;
  return this;
};

var flock_a = new Flock(4);
var flock_b = new Flock(2);
var flock_c = new Flock(0);

var result = flock_a.conjoin(flock_c).breed(flock_b).conjoin(flock_a.breed(flock_b)).seagulls;
//=> 32
```

Who on earth would craft such a ghastly abomination? It is unreasonably difficult to keep track of the mutating internal state. And, good heavens, the answer is even incorrect! It should have been `16`, but `flock_a` wound up permanently altered in the process. Poor `flock_a`. This is anarchy in the I.T.! This is wild animal arithmetic!
究竟谁会费尽心思做这样一件坏事？没有理由纪录易变的内部状态这么难。并且，天哪，甚至答案也是错的！本应该是“16”，但“flock_a”在整个过程中一直不稳定。可怜的“flock_a”。这就是IT中的混乱。这是野生动物算法。

If you don't understand this program, it's okay, neither do I. The point is that state and mutable values are hard to follow even in such a small example.
如果你没看懂这个程序，没关系，我也不懂。关键是即使在这么一个小例子中，状态和变量也是很难捕捉的。

Let's try again with a more functional approach:
让我们再试一种更函数化的方法：

```js
var conjoin = function(flock_x, flock_y) { return flock_x + flock_y };
var breed = function(flock_x, flock_y) { return flock_x * flock_y };

var flock_a = 4;
var flock_b = 2;
var flock_c = 0;

var result = conjoin(breed(flock_b, conjoin(flock_a, flock_c)), breed(flock_a, flock_b));
//=>16
```

Well, we got the right answer this time. There's much less code. The function nesting is a tad confusing...[^we'll remedy this sitation in ch5]. It's better, but let's dig deeper. There are benefits to calling a spade a spade. Had we done so, we might have seen we're just working with simple addition (`conjoin`) and multiplication (`breed`).
这次我们得到了正确答案。代码更短了。这个函数嵌套让人有些困惑……［我们会在第五章再讨论这种情况］。这个更好，但是我们来深究一点。实事求是也有好处。我们这么做会发现我们就是在处理一个简单的加法（“conjoin” 结合）和乘法（“breed” 繁殖）。

There's really nothing special at all about these two functions other than their names. Let's rename our custom functions to reveal their true identity.
这两个函数出了名字外没什么特别的。 重新命名定制函数来显示它们真正的特点。

```js
var add = function(x, y) { return x + y };
var multiply = function(x, y) { return x * y };

var flock_a = 4;
var flock_b = 2;
var flock_c = 0;

var result = add(multiply(flock_b, add(flock_a, flock_c)), multiply(flock_a, flock_b));
//=>16
```
And with that, we gain the knowledge of the ancients:

```js
// associative
add(add(x, y), z) == add(x, add(y, z));

// commutative
add(x, y) == add(y, x);

// identity
add(x, 0) == x;

// distributive
multiply(x, add(y,z)) == add(multiply(x, y), multiply(x, z));
```

Ah yes, those old faithful mathematical properties should come in handy. Don't worry if you didn't know them right off the top of your head. For a lot of us, it's been a while since we've reviewed this information. Let's see if we can use these properties to simplify our little seagull program.
是的，那些老旧的数学性质迟早有用。不要担心，如果你一时不能想起他们。我们很多人，都是再重新看这条信息后过了一会才想到的。我们来看看能不能用这些性质来简化我们的小海鸥程序。

```js
// Original line
add(multiply(flock_b, add(flock_a, flock_c)), multiply(flock_a, flock_b));

// Apply the identity property to remove the extra add (add(flock_a, flock_c) == flock_a)
add(multiply(flock_b, flock_a), multiply(flock_a, flock_b));

// Apply distributive property to achieve our result
multiply(flock_b, add(flock_a, flock_a));
```

Brilliant! We didn't have to write a lick of custom code other than our calling function. We include `add` and `multiply` definitions here for completeness, but there is really no need to write them - we surely have an `add` and `multiply` provided by some previously written library.
好极了！我们不必鞋一些定制代码，除了调用函数。我们包含了“加法”和“乘法”定义来复杂化，但是其实没必要写它们——我们确实有“加法”和“乘法”在一些事先声明库中提供。

You may be thinking "how very strawman of you to put such a mathy example up front". Or "real programs are not this simple and cannot be reasoned about in such a way". I've chosen this example because most of us already know about addition and multiplication so it's easy to see how math can be of use to us here.

Don't despair, throughout this book, we'll sprinkle in some category theory, set theory, and lambda calculus to write real world examples that achieve the same simplicity and results as our flock of seagulls example. You needn't be a mathematician either, it will feel just like using a normal framework or api.

It may come as a surprise to hear that we can write full, everyday applications along the lines of the functional analog above. Programs that have sound properties. Programs that are terse, yet easy to reason about. Programs that don't reinvent the wheel at every turn. Lawlessness is good if you're a criminal, but in this book, we'll want to acknowledge and obey the laws of math.

We'll want to use the theory where every piece tends to fit together so politely. We'll want to represent our specific problem in terms of generic, composable bits and then exploit their properties for our own selfish benefit. It will take a bit more discipline than the "anything goes" approach of imperative[^We'll go over the precise definition of imperative later in the book, but for now it's anything other than functional programming] programming, but the payoff of working within a principled, mathematical framework will astound you.

We've seen a flicker of our functional north star, but there are a few concrete concepts to grasp before we can really begin our journey.

[Chapter 2: First Class Functions](ch2.md)
