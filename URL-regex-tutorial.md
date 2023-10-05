# URL: Regular Expression Tutorial

This article is here as a guide to breakdown and explain the usage, and components of a regular expression. A regular expression (regex), is used when trying to match a character combination with a string, which is a good way to perform validation or pulling information from a body of code. This tutorial will cover the following regex.

## Summary

A regex is used to define a search pattern to search a body of text or string.
The code below is a snippet of the regex used to match a URL:

- <code>`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]_)_\/?$/`</code>

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
The only part of our regex that is an anchor is the <code>`$`</code>, this matches the end of the string, or the end of a line if the multiline flag (m) is enabled.

### Quantifiers

A quantifier tells the regex to match a certain quantity of the character, token or subexpression immediately to its left.

Examples within our regex include:

1. '<code>*</code>' the asterisk quantifier matches 0 or more of the preceeding token.
2. '<code>?</code>' the question mark quantifier matches between 0 and 1 of the preceeding token.

### Grouping Constructs

Grouping constructs are a way to group a section of a regex, primarily by using parentheses <code>()</code>. Each section within parentheses is known as a subexpression.

Examples within our regex include:

1. <code>(https?:\/\/)?</code> This group captures the characters <code>https://</code> and matches it to the url string it is followed by a <code>?</code> to allow the search to allow the search to find nothing.

2. <code>([\da-z\.-]+)</code> This group captures the url domain. The matching guidelines mean that it can only contain digit characters <code>0-9</code>, characters <code>a-z</code>, followed by <code>period</code>, or a <code>hyphen</code>.

3. <code>([a-z\.]{2,6}</code>) This group captures the top-level-domain, such as the .com or .net. The matching guidelines mean that it can only contain characters <code>a-z</code>, followed by a <code>period</code>, then uses a quantifier to match between 2 and 6 of the preceeding token.

4. <code>([\/\w \.-]\*)</code> This group captures any query strings that come after the domain. The matching guidelines mean that it can be <code>null (empty)</code>, or contain any <code>alphanumeric character and underscore</code>, <code>space</code> character, <code>period</code>, and <code>hyphen</code>.

#### \* The periods, and hyphens are escaped characters and require a back slash in order to be matched.

### Bracket Expressions

Anything inside a set of square brackets <code>[]</code> represents a range of characters that we want to match. Bracket expressions are also known as positive character groups, because they outline the characters we want to include.

Examples within our regex include:

1. <code>[\da-z\.-]</code>
   This positive character group outlines that it will match any digit <code>0-9</code>, characters <code>a-z</code>, a <code>period</code>, and a <code>hyphen</code>.

2. <code>[a-z\.]</code>
   This positive character group outlines that it will match and characters <code>a-z</code>, and a <code>period</code>.

3. <code>[\/\w \.-]</code>
   This positive character group outlines that it will match a <code>forward slash</code>, any <code>word character (alphanumeric & underscore)</code>, a <code>period</code>, and a <code>hypen</code>.

#### \* The periods, and hyphens are escaped characters and require a back slash in order to be matched.

### Character Classes

In a regex, a character class defines a set of characters, any one of which can occur in an input string to fulfill a match.

Character classes within our URL regex: <code>\w</code>, and <code>\d</code> which match <code>word</code> characters, and <code>digits</code> respectively.

- /^(https?:\/\/)?([<code>\d</code>a-z\.-]+)\.([a-z\.]{2,6})([\/<code>\w</code>\.-]_)_\/?$/

### The OR Operator

The OR operator is not used in this URL regex, though I will provide a short explanation of what it is used for.

The OR operator <code>|</code>, could take the expression <code>[abc]</code> and write it as <code>(a|b|c)</code>. Using this example: <code>(a|b|c):(x|y|z)</code>, both strings <code>abc:xyz</code> and <code>acb:xyz</code> would match, as well as <code>a:z</code>, but <code>xyz:abc</code> would not.

### Flags

Flags are not used in this URL regex, though I will provide a short explanation of what it is used for.

A flag is an optional parameter to a regex that modifies its behavior of searching. A flag changes the default searching behavior of a regular expression.
Possible flags include: <code>i</code>, <code>g</code>, <code>s</code>, <code>m</code>, <code>y</code> and <code>u</code>.

### Character Escapes

To escape a character having special meaning within a regex, you need to use a <code>backslash</code>.

Examples within our regex include:

1. <code>\d</code> This escaped character matches digits <code>0-9</code>.

2. <code>\w</code> This escaped character matches any <code>word character (alphanumeric and hyphen).</code>

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
