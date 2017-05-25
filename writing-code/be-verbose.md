# Be verbose

When writing code, be verbose.

Verbosity is like autodoc and static type checking: it adds up to
the number of lines of code but makes it way easier to understand
what that code is doing.

You may think verbosity also increases the cost of refactoring,
because when you have direct references to variables instead of
some nice [object
spread](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/Spread_operator)
in many places, it's harder to control.

The opposite of verbosity isn't the opposite of refactoring.
Being short won't make refactoring easier. It will make debugging
harder.

Where is the line? Just stick to [common
vocabulary](use-common-lexicon.md) that is universal, keep the
number of dependencies
[short](least-possible-number-of-dependencies.md), and thing will
go easy. 

A surprising effect of code verbosity is what your subconscious
does with it. The more information you observe while literally
staring at screen and scrolling around, the more you will later
be thinking about it, without even noticing. It may increase the
likelihood of gotcha discovery. Knowing more works better than
knowing less when it comes to progressive improvement of the code
(refactoring).
