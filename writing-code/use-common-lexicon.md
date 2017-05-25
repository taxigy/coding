# Use common vocabulary

When engineering a feature, use as much of common vocabulary as
possible.

Say, you want to fetch data about bananas from Banana API, check
if it is valid, then output as a collection of bananas.

A really bad way to do is to write semantically-heavy functions,
the ones that depend on exact data so much, they even have
mention of it in their names. Like `getBananas`. The greater the
scope, the uglier this approach appears.

A nice way to do is to use common words every programmer in the
world would understand, compose them (that's one of these words)
and produce a highly universal, highly maintainable code.

A very common example is data traversal and transformation. The
most common example of all in Javascript, for example, is to get
an array of objects and transform it into an object. It's a
classic problem that is solved with
[`reduce`](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce?v=example).

The more you stick to universal patterns in your code, the easier
to maintain it. You may even find that lots of it is actually
pointless [syntactic
duplication](../technical-negotiations/the-holy-duplication-war.md),
because when functions are so tiny and simple, they have so
little semantic load that they can easily be merged or split as
you like.

If you don't know where to start, there's a good [FP
vocabulary](http://zacanger.com/blog/functional-programming-vocabulary.html).
