# Least possible number of dependencies

When writing code, keep the number of dependencies as low as possible. There are many ways to implement the same feature, especially when it comes to higher-level things.

First, the front-end.

In Javascript world, the most popular framework-independent lib of 2015 was [lodash](https://github.com/lodash/lodash). It is so useful, you can forget about algorithmic part of majority of technical challenges you encounter in your daily JS programming. Convert a plain-object (hash map) into an array (vector)? Use `_.toArray`. In the opposite direction? No prob, it's `_.groupBy`. Any kind of little operation against a data set is no big deal. You can chain them, you can compose them, and you can use lambdas all around.

Lodash adds extra 24 KB to your bundle, when minified and gzipped. Oftentimes, it's overkill. Simply having a possibility to use type-safe `map` or `reduce` should have way lower cost. And remember, for you, 24 KB may not be much, but [for most of the world, it is](https://danluu.com/web-bloat/).

In 2017, a big part of front-end dev world uses [React](https://github.com/facebook/react). There are pretty many other things around it, but the second most used if [Redux](https://github.com/reactjs/redux). Now, there are tools that are so nice and useful, you can't hold from using them: [reselect](https://github.com/reactjs/reselect), [recompose](https://github.com/acdlite/recompose), [rebass](https://github.com/jxnblk/rebass). And they change like every couple months. No kiddin'. So either you are one who knows it all, e.g. have used each of them once for an hour; or you are a really deep expert in one of those (considering you chose it wisely, of course).

Now, the back-end.

Nobody will notice your back-end bundle size. Whatever it is, as long as the code is performant and the whole thing fits into the size of target container, nobody really cares. However, there's another naval mine awaiting you with all the deps you drag behind: the cost of mental control.

Every time you add a dependency, you bind to it mentally and therefore spend the run-time of your brain, consciously or not, to control it. Whether it needs to be updated, whether it causes problems with peer deps, it all consumes your run-time. Simple code that solves exactly your problem would take a few hours (if not less) to implement and could possibly stay there for ages, but third-party libs want you to update them, to keep them fresh, because it's so tempting.

Another problem is time-to-learn. Imagine a newbie programmer coming at ya and taking over the part of codebase. Not only it's important to learn the whole codebase because of practices followed and features already implemented, but it is important to learn all the third-party libs used there.

The balance is definitely far from any of the extremes.

There's a framework to make the decision process easier (and more enjoyable when involves your fav beverage):

1. Find three programmer friends.
1. Every time you want to use a new lib in prod code, tell them about it, then listen carefully and wait for rational response that usually comes in a bit after emotional.
1. Act.

Good luck!
