# Autodocumented Code

Having code that works is awesome, but what is even more awesome is code that works and can also successfully express what it does by just being itself. You have that good feeling when you look at the code, read it once from top to bottom, and have an idea what's going on there.

A classic way to achieve this quality of your code is to write comments. They can be of various usefulness. Consider this:

```javascript
// Here, we check if the list has either two or four items.
if (list.length === 2 || list.length === 4) {
  // ...
}
```

or this:

```javascript
async function getBananas(n) {
  try {
    // Fetch bananas, split them and peel
    const bananas = await fetchBananas(n);
    // Then divide bananas from their hands,
    const split = bananas.split();
    // And finally, peel bananas:
    return split.peel();
  } catch (error) {
    // FIXME: do something when error happens
  }
}
```

The last one looks ridiculous, right? It's not easy to get what's going on there simply looking at this line:

```javascript
return split.peel();
```

but generally, it's all fine. The code can be simplified into this:

```javascript
async function getBananas(n) {
  try {
    return (await fetchBananas(n)).split().peel();
  } catch (error) {
    // FIXME: do something when error happens
  }
}
```

Here, we fetch bananas, split the result, then peel the result. It's simple, easy to read, fits into your head quickly and easily, and generally doesn't need extra comments.

The highest point of this idea is that you don't need better comments, you need better code that goes fine without any comments! If you feel an urge to add comments to your code, refactor it immediately:

1. If it's a huge function, split it into smaller ones. You can just prepare bananas, or you can prepare bananas by fetching, splitting and peeling.
2. If it's a vague name of an entity, just make it specific and self-descriptive.
3. If it's too long to read in a minute and still be able to maintain perfect understanding of what's going on there, simplify.
4. If it can be described using generic terms ("map", "reduce", "split", "fetch", "resolve", "reject") over specific ("checkBananas", "throwAwayBananas"), use generic. Pick the right generic though: something every programmer who has Bachelor in CS would understand in a moment.
5. References should follow from top to bottom. If you use a function after it is defined, even though your compiler hoists, your eyes don't. Take care about your eyes, move entities in order of their appearance, just like in a book.

Generally, you need to reach a point when you don't need to constantly switch tabs to write code. Everything that is important for current task should fit into your brain. Your goal is to maintain both flexibility of your brain _and_ readability of your code.

----

TODO:

- [ ] Work on examples. The ones used now are weak and not impressive.
- [ ] Make the manuscript like a story, not like a bunch of practices.
