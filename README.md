[![Latest release](http://img.shields.io/bower/v/purescript-exists-eq.svg)](https://github.com/rgrempel/purescript-exists-eq/releases)
[![Dependency Status](https://www.versioneye.com/user/projects/57adfd69136364003ecc2e23/badge.svg?style=flat-square)](https://www.versioneye.com/user/projects/57adfd69136364003ecc2e23)
[![Build Status](https://travis-ci.org/rgrempel/purescript-exists-eq.svg?branch=master)](https://travis-ci.org/rgrempel/purescript-exists-eq)

# purescript-exists-eq

Ordinarily, you can only check two values for equality if the type-checker
knows that they are the same type.

This module provides an `eqAny` function which loosens that restriction. It
works with any two values, so long as each has an `Eq`
instance. To do so, it checks whether the two `Eq` instances are implemented
with the same function. If so, clearly that function can take both values,
and can be called to determine equality. If not, clearly the values are unequal.

**Note that it turns out that this mechanism currently works only with `*`
kinds, not `* -> *` or higher kinds (see examples below). I am working on a
fix, likely by requiring a
[`Typeable`](https://github.com/joneshf/purescript-typeable) constraint.**

But why would the type-checker not know that the two values are of the same
type? On occasion, it is convenient to "forget" the type of a value, and only
remember some fact about the type -- say, that it has an `Eq` instance.
This is a little like what
[`Data.Exists`](https://pursuit.purescript.org/packages/purescript-exists)
does, except that `Data.Exists` doesn't remember anything at all about the
original type.

So, this module provides a `someEq` function, which turns any value with an
`Eq` instance into a `SomeEq` (with no type variable). All you can do with a
`SomeEq` is check it for equality with another `SomeEq`. The nice thing is
that the two `SomeEq` values may originally have been different types.

## Installation

Try `bower install purescript-exists-eq`

## Development

Try something like:

    git clone https://github.com/rgrempel/purescript-exists-eq
    bower install
    pulp test

## API

Documentation for the API can be found on [Pursuit](https://pursuit.purescript.org/packages/purescript-exists-eq).
Or, if you are already looking at Pursuit, then below ...

