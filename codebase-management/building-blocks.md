# Building blocks

Every codebase has its own inner culture, and every codebase
consists of blocks that form its structure and content. If you
have a monorepo, large blocks are client code, server code and
shared code. If you store assets in your codebase, it's another
block. If you have a [React](https://facebook.github.io/react/)
project, smaller blocks are components. If you use
[Relay](https://facebook.github.io/relay/), containers, queries
and mutations are even smaller blocks that exist in your
codebase.

When the product is at its very early design phase, what's
typically happening is designers are working on the future UI and
UX of the product. People are going to use it, and of course
people are going to interact with it, but more than that, getting
people attracted and addicted to the product through interesting
interaction mechanics is a nice-to-have, because, you know,
that's where the money is.

These days, a designer is very likely using Sketch (or Photoshop)
to first wireframe and then apply branding and assist developers.
When you have a design doc, it's just clear where to start: take
the first (top left) screen and implement it. But that's not what
you should be doing.

What designers _really_ do is, first, develop a design system
(take a look at
[Salesforce's](https://developer.salesforce.com/lightning/design-system) one or [Material Design](https://material.google.com)). What programmers should be doing is exactly the same:

- develop a system,
- extract building blocks,
- first implement these blocks, and finally
- [start building product using these blocks](https://twitter.com/taxigy/status/788455770878799872).

Again, when you have a design doc, it's easy to do. You simply
follow this doc, pick these little things, cards, buttons and
such, and implement them one by one. Along the way, you'll
probably find out that you don't really know how a user
_actually_ interacts with these elements. This is a huge phase
that designers and developers have overlap in, when
communications matter more than number of PRs merged, and when
things may change significantly.

Always start with building blocks. You'll likely be very happy
and code with less pain in future.

----

Useful links:

- ["Promoting a Design System Across Your Products", A List Apart, June 2016](http://alistapart.com/article/promoting-a-design-system-across-your-products)
