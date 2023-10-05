# URL: Regular Expression Tutorial

This article is here as a guide to breakdown and explain the usage, and components of a regular expression. A regular expression (regex), is used when trying to match a character combination with a string, which is a good way to perform validation or pulling information from a body of code. This tutorial will cover the following regex.

## Summary

A regex is used to define a search pattern to search a body of text or string.
The code below is a snippet of the regex used to match a URL:

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]_)_\/?$/`

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

Regex components work together to define a search pattern, the following components are some that can be used.

### Anchors

An anchor is used to match a position before, after, or between characters.

Examples within our regex include:

1. `^` This matches the start of a string, or the end of a string if the multiline flag `(m)` is enabled. This means that it will be looking for something specifically starting with `^(https?:\/\/)`
2. `$` This matches the end of a string, or the end of a line if the multiline flag `(m)` is enabled. This means that it will be looking for something specifically ending with `([\/\w \.-]_)_\/?$` or if none are present since the character grouping specifies the query string which can be `null`, it would look for the preceeding token which is required `([a-z\.]{2,6})`.

### Quantifiers

A quantifier tells the regex to match a certain quantity of the character, token or subexpression immediately to its left.

Examples within our regex include:

1. `*` the asterisk quantifier matches `0` or `more` of the preceeding token. This means that there can be any number of tokens, even zero.
2. `?` the question mark quantifier matches between `0` and `1` of the preceeding token. This means that there can be zero tokens and no more than 1 token.
3. `+` the plus sign quantifier matches `1` or `more` of the preceeding token. This means that there must be at least one token.

### Grouping Constructs

Grouping constructs are a way to group a section of a regex, primarily by using parentheses `()`. Each section within parentheses is known as a subexpression.

Examples within our regex include:

1. `(https?:\/\/)?` This group captures the characters `https://` and matches it to the url string it is followed by a `?` to allow the search to allow the search to find nothing.

2. `([\da-z\.-]+)` This group captures the url domain. The matching guidelines mean that it can only contain digit characters `0-9`, characters `a-z`, followed by `period`, or a `hyphen`.

3. `([a-z\.]{2,6})` This group captures the top-level-domain, such as the .com or .net. The matching guidelines mean that it can only contain characters `a-z`, followed by a `period`, then uses a quantifier to match between `2` and `6` of the preceeding token.

4. `([\/\w \.-]\*)` This group captures any query strings that come after the domain. The matching guidelines mean that it can be `null (empty)`, or contain any word character `(alphanumeric & underscore)`, `space` character, `period`, and `hyphen`.

#### \* The periods, and hyphens are escaped characters and require a back slash in order to be matched.

### Bracket Expressions

Anything inside a set of square brackets `[]` represents a range of characters that we want to match. Bracket expressions are also known as positive character groups, because they outline the characters we want to include.

Examples within our regex include:

1. `[\da-z\.-]`
   This positive character group outlines that it will match any digit `0-9`, characters `a-z`, a `period`, and a `hyphen`.

2. `[a-z\.]`
   This positive character group outlines that it will match and characters `a-z`, and a `period`.

3. `[\/\w \.-]`
   This positive character group outlines that it will match a `forward slash`, any word character `(alphanumeric & underscore)`, a `period`, and a `hypen`.

#### \* The periods, and hyphens are escaped characters and require a back slash in order to be matched.

### Character Classes

In a regex, a character class defines a set of characters, any one of which can occur in an input string to fulfill a match.

Character classes within our URL regex: `\w`, and `\d`which match `word` characters, and `digits` respectively.

### The OR Operator

The OR operator is not used in this URL regex, though I will provide a short explanation of what it is used for.

The OR operator `|`, could take the expression `[abc]` and write it as `(a|b|c)`. Using this example: `(a|b|c):(x|y|z)`, both strings `abc:xyz` and `acb:xyz` would match, as well as `a:z`, but `xyz:abc` would not.

### Flags

Flags are not used in this URL regex, though I will provide a short explanation of what it is used for.

A flag is an optional parameter to a regex that modifies its behavior of searching. A flag changes the default searching behavior of a regular expression.
Possible flags include: `i, g, s, m, y and u`.

### Character Escapes

To escape a character having special meaning within a regex, you need to use a backslash.

Examples within our regex include:

1. `\d` This escaped character matches digits `0-9`.

2. `\w` This escaped character matches any word character `(alphanumeric and underscore)`.

## Author

### Daniel Masefield

This tutorial was written by Daniel Masefield, a full stack web developer.

[GitHub](https://github.com/Staroyee)

[LinkedIn](https://www.linkedin.com/in/danielmasefield03/)

## Resources

- https://regexr.com/
- https://www.freecodecamp.org/news/how-to-write-a-regular-expression-for-a-url/
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions
- https://www.w3schools.com/js/js_regexp.asp
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions/Character_classes
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions/Assertions
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions/Groups_and_backreferences
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions/Quantifiers
- https://www.codeguage.com/courses/regexp/flags#:~:text=A%20flag%20is%20an%20optional,a%20single%20lowercase%20alphabetic%20character.
- https://coding-boot-camp.github.io/full-stack/computer-science/regex-tutorial
- https://www3.ntu.edu.sg/home/ehchua/programming/howto/Regexe.html#:~:text=Escape%20Sequences%20(%5Cchar)%3A,%22%20(back%2Dslash)
