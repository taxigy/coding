# The Holy Duplication War

There are two kinds of code duplication: syntactic duplication and semantic duplication.

**Syntactic duplication** means literally "two identically looking pieces of code". If you compare them, they are identical. You can literally copy the two, normalize, do `x === y` (or `(= x y)`, if you like), and come up with `true`. This is a marginal case, as more commonly, the two pieces look identical _but slightly different_.

**Semantic duplication**, in turn, means not two parts of the code that look the same, but _do_ the same. You'll come across multitudes of such examples if you haven't yet. Everything in programming, especially low-level stuff, can be done in a dozen ways, or more.

The problem is that the two look very similar. It's just hard to distinguish between them, especially when codebase is fresh and young. And sometimes, it's not even worth it. But you are a programmer and you definitely want to show your superb coding skills, so you'll remove both, no matter the cost it comes at on the long run.

Consider this:

```javascript
function peelApple(apple) {
  return {
    ...apple,
    peeled: true
  };
}

function peelOrange(orange) {
  return {
    ...orange,
    peeled: true
  };
}
```

If you replace `apple` and `orange` with `x`, the two pieces are identical. That's why you'll probably do this:

```javascript
function peelFruit(fruit) {
  return {
    ...fruit,
    peeled: true
  };
}
```

And then suddenly you need to manage depth of peeling, just because thickness of peel varies for different fruit. With that syntactic duplication you really want to remove completely you'd do it like this:

```javascript
function peelApple(apple) {
  return {
    ...apple,
    peeled: true,
    depth: 1
  };
}

function peelOrange(orange) {
  return {
    ...orange,
    peeled: true,
    depth: 3
  };
}
```

but you are busy removing it. You have a single function now and you need to check for a fruit type:

```javascript
function peelFruit(fruit) {
  const { fruitType } = fruit;

  return {
    ...fruit,
    peeled: true,
    depth: fruitType === 'apple' ? 1 : fruitType === 'orange' ? 3 : null // if you only have apples and oranges, null is unreachable
  };
}
```

Now guess what? You also need to be able to collect peel to a different garbage container, you know, because apple peel and orange peel come bad together. With syntactic duplication, you'd do it like:

```javascript
function peelApple(apple) {
  const { peel } = apple;

  throwAwayApplePeel(peel);

  return {
    ...apple,
    peel: null,
    peeled: true,
    depth: 1
  };
}

function peelOrange(orange) {
  const { peel } = orange;

  throwAwayOrangePeel(peel);

  return {
    ...orange,
    peel: null,
    peeled: true,
    depth: 3
  };
}
```

And without it, you'd probably do something like this:

```javascript
function peelFruit(fruit) {
  const { fruitType, peel } = fruit;

  if (fruitType === 'apple') {
    throwAwayApplePeel(peel);
  } else if (fruitType === 'orange') {
    throwAwayOrangePeel(peel);
  } else {
    // unreachable, but who knows...
  }

  return {
    ...fruit,
    peeled: true,
    depth: fruitType === 'apple' ? 1 : fruitType === 'orange' ? 3 : null
  };
}
```

With time, your code will become unbearably hard to read. You'll forget why you had even done that in the past, man, it should have been just split into two simple functions! Haven't you ever felt it?

## The solution

Keep syntactic duplication. Although apples and oranges are both fruit, it doesn't mean they are semantically identical and can be treated this way. If you believe in your project and expect it to be in development for more than a year, please, just leave this duplication be. You'll see how different apple and orange peel management becomes as you go forward. And you definitely consume them in different ways, too.

Kill semantic duplication. When two things have equal meaning, when you manage two independent parts of the code but they are responsible for exactly the same thing, and keeping both doesn't add any value, reduce to just one.

Keep your eye on what you're doing, and why, and if it really is beneficial on the long run.

Simply removing syntactic duplication doesn't make you smart or your code more maintainable. It helps you flex your brain, that's true. It also helps you feel more human, because humans like to categorize and group similar things. But code is no human. Imagine how much time you'll spend explaining to a newcomer, that will have to pick up your four months old codebase, that you can peel both apples and oranges with the same function, and then give that poor newbie a task: make it peel tomatoes.

If you really want to show off, _curry that function._

----

This is actually [what I learned earlier](https://github.com/taxigy/til/blob/master/programming/syntactic-deduplication.md), and this is what is described in a very nice way in ["Mostly Adequate Guide to Functional Programming" book](https://github.com/MostlyAdequate/mostly-adequate-guide).
