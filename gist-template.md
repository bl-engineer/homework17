# 17 - Regular Expression (Regex) tutorial

## Summary

A **regex**, or **regular expression**, is a sequence of characters which defines a specific search pattern. In this Regex tutorial, i am using it to match an HTML tag. Included in a search algorithms, these regular expressions can be used to find some patterns of characters in a string, or to find and replace a character or sequence of characters in a string. They can also be used to validate input. This specific tutorial will give us the different components as shown in the table of content.


This is the regex that we are going to break down and give a summary of the meaning.
* To match an HTML Tag: `/^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/`

SUMMARY:

An opening bracket will be in the first position. <br />
then it looks for at least one of any letter comming next. <br />
If one or more opening tags follow, then, they will be ignored. <br />

then it looks for a `>` to finish the opening HTML tag. <br />
The regex will then look for zero (0) or more of character, minus(-) line breaks. <br />
then look for the beginning of a closing tag: `</` followed by the character in the first position in the regex's sequence, then a alphabet character found in a search [a-z]. <br /> or <br />.

Then one or more white space characters found <br />
With the `/>` ending of a closing tag. <br />


## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Character Escapes](#character-escapes)
 
 <br />

## Regex Components

## Anchors
**Example**
The first anchor `^` will begin a search for the characters that come after it. In this case, `^<` will search for an opening bracket for an HTML tag in the first position.

**Matches**
* `<html></html>` <br />

**Example**
The second anchor `^` is inside a bracket expression, which turns it into a negative character group. In this case, `([^<]+)` means it will ignore if there are one or more opening brackets.

**Matches**
* `<a<<<>`
* `<a>`
* `<html<<<<<<<<<` <br />

**Example**
The `$` anchor symbol signifies that a string should end with the characters that come before it. In this case, `$/` signifies the end of the regex. <br /> <br />


## Quantifiers
Quantifiers set the limits of the string that your regex matches by defining how many times a part should occur. 

**Example**
The first quantifier is included in the first grouping construct, or subexpression `([a-z]+)`. This means the regex should match one or more of any alphabet character.

**Matches**
* `<script`
* `<body` <br />

**Example**
There are two quantifiers in the second subexpression `([^<]+)*`. The `+` means the regex will ignore one or more opening brackets AFTER the first one has occurred, and the `*` means this result could be found zero or more times.

**Matches**
* `<<<<html> </html>`
* `<a<<<></a>`
* `<p></p>` <br />

**Example**
The fourth quantifier is in the third subexpression: `(?:>(.*)`. In this case, the regex will find zero or more of any character (minus line breaks) AFTER the opening tag has been finished.

**Matches**
* `<p> This is a sentence!` <br />

**Example**
The fifth quantifier comes after the "or" pole `|`: `\s+`. This means if the search does not find the previous criteria, it will search for at least one or more white space characters. <br /> <br />


## Grouping Constructs
() are the primary way to group sections, aka subexpressions, of a regex.

**Example**
The first subexpression `([a-z]+)` is saying that after finding an opening bracket `<` in the first position, is will then find any number of alphabet characters. 

**Matches**
* `<html`
* `<p` <br />

**Example**
The second subexpression `([^<]+)*` will ignore one or more opening tags that follow the alphabet characters, and says that this could occur zero or more times. 

**Matches**
* `<a<<<></a>` <br />

**Example**
The third subexpression `(?:>(.*)<\/\1>|\s+\/>)` is... a lot. But here's what it's saying. First, `(?: ... )` specifies a non-capturing group, meaning you cannot reference or reuse anything inside later on. It will then look for a `>` to finish the opening HTML tag,
and then for zero or more of any character, minus line breaks. The regex will then look for the beginning of a closing tag: `</` followed by the character in the first position in the regex sequence, the alphabet character found in the search [a-z]. The OR Operator `|` specifies that if the previous criteria was not found, it may also look for the following: one or more white space characters, with the `/>` ending of a closing tag. 

**Matches**
* `<html></html>`
* `<img />` <br /> <br />


## Bracket Expressions
Bracket expressions use `[]` to represent a range of characters we want to match.

**Example**
The first bracket expression `[a-z]+` says we want to find one or more of any alphabet character a-z. 

**Matches**
* `<aaaaa`
* `<img` <br />

**Example**
The second bracket expression `[^<]+` will ignore one or more opening brackets after the alphabet character(s).

**Matches**
* `<a<<<></a>` <br /> <br />


## Character Classes
Character classes define a set of characters, any one of which can occur in an input string to fulfill a match. Essentially, it gives special meaning to an otherwise literal character.

**Example**
The character class `\s` signifies a single white space character. In the case of this regex, `\s+` means to look for one or more white space characters.

**Matches**
* `<img />` <br /> <br />


## The OR Operator
The OR operator will match characters or expressions to either the left or the right of the operator. Essentially, either the left or right scenario could occur, but one of them must occur.

**Example**
This part `(.*)<\/\1>|\s+\/>)` in the last subexpression means either one of these scenarios could occur:
* 1. Any number of any characters with a closing tag that matches the type of opening tag, or
* 2. One or more white space characters with the partial closing tag `/>`

**Matches**
* `<p> This is an awesome sentence! </p>`
* `<img />` <br /> <br />


## Character Escapes
`\` escapes a character that would otherwise be interpreted literally. This can give characters special rather than literal meaning.

**Example**
`/\1` in the context of `<\/\1>` means the regex will find the beginning of a closing tag `</` followed by the same alphabet character found in the first position of the regex.

**Matches**
* `<container></container>` <br />

**Example**
The last character escape `\/>` wants the literal expression `/>` to be found at the end of the string.

**Matches**
* `<div> </div>` <br /> <br />


## Author
© Done by: Bocar Ly
[Github](https://github.com/bl-engineer)
[Portfolio](https://bl-engineer.github.io/portfolio1/)

