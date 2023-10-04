# URL: Regular Expression Tutorial

This article is here as a guide to breakdown and explain the usage, and components of a regular expression. A regular expression (regex), is used when trying to match a character combination with a string, which is a good way to perform validation or pulling information from a body of code. This tutorial will cover the following regex.

## Summary

A regex is used to define a search pattern to search a body of text or string.
The code below is a snippet of the regex used to match a URL:

- <span style="color: #FF69B4;">/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]_)_\/?$/</span>

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
The only part of our regex that is an anchor is the <code>$</code>, this matches the end of the string, or the end of a line if the multiline flag (m) is enabled.

### Quantifiers

A quantifier tells the regex to match a certain quantity of the character, token or subexpression immediately to its left.

Examples within our regex include:

1. '<span style="color: #FF69B4;">\*</span>' the asterisk quantifier matches 0 or more of the preceeding token.
2. '<span style="color: #FF69B4;">?</span>' the question mark quantifier matches between 0 and 1 of the preceeding token.

### Grouping Constructs

Grouping constructs are a way to group a section of a regex, primarily by using parentheses <span style="color: #FF69B4;">()</span>. Each section within parentheses is known as a subexpression.

Examples within our regex include:

1. <span style="color: #FF69B4;">(https?:\/\/)?</span> This group captures the characters <span style="color: #FF69B4;">https://</span> and matches it to the url string it is followed by a <span style="color: #FF69B4;">?</span> to allow the search to allow the search to find nothing.

2. <span style="color: #FF69B4;">([\da-z\.-]+)</span> This group captures the url domain. The matching guidelines mean that it can only contain digit characters <span style="color: #FF69B4;">0-9</span>, characters <span style="color: #FF69B4;">a-z</span>, followed by <span style="color: #FF69B4;">period</span>, or a <span style="color: #FF69B4;">hyphen</span>.

3. <span style="color: #FF69B4;">([a-z\.]{2,6}</span>) This group captures the top-level-domain, such as the .com or .net. The matching guidelines mean that it can only contain characters <span style="color: #FF69B4;">a-z</span>, followed by a <span style="color: #FF69B4;">period</span>, then uses a quantifier to match between 2 and 6 of the preceeding token.

4. <span style="color: #FF69B4;">([\/\w \.-]\*)</span> This group captures any query strings that come after the domain. The matching guidelines mean that it can be <span style="color: #FF69B4;">null (empty)</span>, or contain any <span style="color: #FF69B4;">alphanumeric character and underscore</span>, <span style="color: #FF69B4;">space</span> character, <span style="color: #FF69B4;">period</span>, and <span style="color: #FF69B4;">hyphen</span>.

#### \* The periods, and hyphens are escaped characters and require a back slash in order to be matched.

### Bracket Expressions

Anything inside a set of square brackets <span style="color: #FF69B4;">[]</span> represents a range of characters that we want to match. Bracket expressions are also known as positive character groups, because they outline the characters we want to include.

Examples within our regex include:

1. <span style="color: #FF69B4;">[\da-z\.-]</span>
   This positive character group outlines that it will match any digit <span style="color: #FF69B4;">0-9</span>, characters <span style="color: #FF69B4;">a-z</span>, a <span style="color: #FF69B4;">period</span>, and a <span style="color: #FF69B4;">hyphen</span>.

2. <span style="color: #FF69B4;">[a-z\.]</span>
   This positive character group outlines that it will match and characters <span style="color: #FF69B4;">a-z</span>, and a <span style="color: #FF69B4;">period</span>.

3. <span style="color: #FF69B4;">[\/\w \.-]</span>
   This positive character group outlines that it will match a <span style="color: #FF69B4;">forward slash</span>, any <span style="color: #FF69B4;">word character (alphanumeric & underscore)</span>, a <span style="color: #FF69B4;">period</span>, and a <span style="color: #FF69B4;">hypen</span>.

#### \* The periods, and hyphens are escaped characters and require a back slash in order to be matched.

### Character Classes

In a regex, a character class defines a set of characters, any one of which can occur in an input string to fulfill a match.

Character classes within our URL regex: <span style="color: #FF69B4;">\w</span>, and <span style="color: #FF69B4;">\d</span> which match <span style="color: #FF69B4;">word</span> characters, and <span style="color: #FF69B4;">digits</span> respectively.

- /^(https?:\/\/)?([<span style="color: #FF69B4;">\d</span>a-z\.-]+)\.([a-z\.]{2,6})([\/<span style="color: #FF69B4;">\w</span>\.-]_)_\/?$/

### The OR Operator

The OR operator is not used in this URL regex, though I will provide a short explanation of what it is used for.

The OR operator <span style="color: #FF69B4;">|</span>, could take the expression <span style="color: #FF69B4;">[abc]</span> and write it as <span style="color: #FF69B4;">(a|b|c)</span>. Using this example: <span style="color: #FF69B4;">(a|b|c):(x|y|z)</span>, both strings <span style="color: #FF69B4;">abc:xyz</span> and <span style="color: #FF69B4;">acb:xyz</span> would match, as well as <span style="color: #FF69B4;">a:z</span>, but <span style="color: #FF69B4;">xyz:abc</span> would not.

### Flags

Flags are not used in this URL regex, though I will provide a short explanation of what it is used for.

A flag is an optional parameter to a regex that modifies its behavior of searching. A flag changes the default searching behavior of a regular expression.
Possible flags include: <span style="color: #FF69B4;">i</span>, <span style="color: #FF69B4;">g</span>, <span style="color: #FF69B4;">s</span>, <span style="color: #FF69B4;">m</span>, <span style="color: #FF69B4;">y</span> and <span style="color: #FF69B4;">u</span>.

### Character Escapes

To escape a character having special meaning within a regex, you need to use a <span style="color: #FF69B4;">backslash</span>.

Examples within our regex include:

1. <span style="color: #FF69B4;">\d</span> This escaped character matches digits <span style="color: #FF69B4;">0-9</span>.

2. <span style="color: #FF69B4;">\w</span> This escaped character matches any <span style="color: #FF69B4;">word character (alphanumeric and hyphen).</span>

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
