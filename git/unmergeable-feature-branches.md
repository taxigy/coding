# Unmergeable Feature Branches

You know what they are if you have seen that "Cannot be
automatically merged" and red cross next to your pull-request. It
usually means that while you were working on a new feature on a
separate branch, somebody has changed the same files as you.
Quite a usual thing to happen when both communications and
codebas organization suck. And they do more often than you think.

There are a few typical causes of red PRs. One of them is that
either you or somebody else thought it's a good idea to _quickly
refactor that piece of code nobody would possible touch in the
next few hours._ What a mistake!

To avoid,

- kill your itchiness to fix things that are not directly related
  to a feature you're working right now,
- ask everybody to follow the same rule, and
- when you're going to change a piece of code other features rely
  on, say it _loud and clear_, mentioning `@channel` if
  necessary. It's rude to bother people, but they will be thankful
  soon.

Another cause is _features that take too long to get
implemented._ A general rule for a good feature is that it can be
implemented in a day. It means that on the next day, you'll be
shipping it, or be busy resolving merging conflicts for an hour.
But you'll eventually ship it. Create a PR and get it approved
and merged into master branch. But some features stretch into
several days because they depend on other stuff in progress, or
they are too broad and you'll probably need to do a myriad of
little things to get them finished.

To avoid,

- never start working on a feature until it's totally clear
  _nothing_ is blocking you,
- if you are asked to, divide into little steps, each meaningful,
  and get PRs merged sequentially; never start working on the
  next step until PR for the previous one is in master branch,
  and
- when you're going to split the feature into a bunch of smaller
  tasks, say it _loud and clear_, mentioning `@channel` if
  necessary. Leave the same comment on the issue.
