# Mod 17 Challenge!

## Regex Tutorial
 Hello there and welcome to my Regex Tutorial! What is Regex? Let's go to the summary section below to get to know it more.

    
## Summary

In this tutorial I will explain how a specific regular expression, or regex, functions by breaking down each expression and then describe what each component does.




- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors
With anchors, they do not match any character at all. Instead, they match a position before... after... or between characters. They can be used to “anchor” the regex match at a certain position. The caret `^` matches the position before the first character in the string. Applying `^a` to abc matches `a`. `^b` does not match `abc` at all, because the `b` cannot be matched right after the start of the string, matched by `^`. Similarly, `$ `matches right after the last character in the string. `c$` matches `c` in abc, while a `$` does not match at all.

| Symbol      | Description | Example | E-mail Example
| ----------- | ----------- |-----------|-----------|
| `^`          | By default, the match must occur at the beginning of the string; in multiline mode, it must occur at the beginning of the line.       |`^a` means starts with `a` | `^([a-z0-9_\.-]+)` means starts with `([a-z0-9_\.-]+)`
| `$`          | By default, the match must occur at the end of the string or before \n at the end of the string; in multiline mode, it must occur at the end of the line or before \n at the end of the line        |`b$` means ends with `b` | `([a-z\.]{2,6})$` means ends with `([a-z\.]{2,6})`


### Quantifiers
With Quantifiers they specify how many instances of a character, group, or character class must be present in the input for a match to be found. The quantifier `?` makes the preceding token optional. In other words, it repeats the token between zero or one times. If the `*`, `+`, `?`, `{`, and `}` characters are encountered in a regular expression pattern, the regular expression engine interprets them as quantifiers or part of quantifier constructs unless they are included in a character class. To interpret these as literal characters outside a character class, you must escape them by preceding them with a backslash. For example, the string `\*` in a regular expression pattern is interpreted as a literal asterisk `("*")` character.

| Symbol      | Description | Example   |E-mail Example|
| ----------- | ----------- |-----------|-----------|
|`+`| Matches a string that has the anterior followed by one or more of the last character| `ne+` will match any set of characters that contains the string "`ne`" with at least one occurence of "`n`" and more, for example : "`nee`d", "`need`le" or "`ne`t". In the last 3 examples, "`nee`", "`nee`" and "`ne`" will be the corresponding matchings. | `[a-z0-9_\.-]+` means any characters of `[a-z0-9_\.-]` and more will be a matching record
|`\d`| Matches a single digit, is equivalent to `[0-9]`|`[\d]` in the zipcode `90210`, there will be 5 matching records|`[\da-z\.-]` would be equivalent to `[0-5a-z\.-]` meaning will find all the digits between 0 and 5, as well as any letter between `a` and `z`, dots `.` and hypens `-` . Example: needa `-`mehmud @gmail.com
|`{}`| Matches a string that has the anterior followed by how ever many the number in the brackets of the last character in the string | Here we can use  `max and min` within the curly brackets. That would simply mean that  preceding characters is matched at least "min" times and "max" times and would look something like this `{min,max}`| `\.([a-z\.]{2,6})$` means at least 2 occurences of a string `[a-z\.]` and no more than 6. Example: example@gmail`.com` and example@`gmail.com`


### OR Operator
with OR Operators in regex consist of ```|``` and ```[]```.
The ```|``` matches a string that includes both characters to the left and right of the symbol. 
Whereas, the ```[]``` will match for any characters or character classes included in the brackets. 
Additionally, the ```-``` character has special meaning inside of a ```[]``` . It provides a range construct.


### Character Classes
These  are for main character classes in regex;
The ```\d``` matches a single character that is a digit.
The ```\w``` will match a word.
The ```\s``` matches a single space.
The ```.``` is a wildcard for any character, unless preceded by a backwards slash ```\.```, then it's a required dot.

In this regular expression:
```
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/
``` 
 - ```\d``` matches a single character that is a digit. ```[\da-z\.-]``` is looking for the domain name specifically.
 - ```\w``` matches a word. ```[\/\w \.-]``` would identify any words or directories that are written post the domain.
 - ```\.``` refers to a required dot within the URL.



### Flags
Regex usually comes within a form where the search pattern is defined between two ```/``` characters. 
At the end is typically where one can specify a flag, even after the anchors we have previously discussed.
Flags help mark the expression as global ```g```, multi-line  ```m```, or insensitive ```i```.

### Grouping and Capturing
Grouping constructs delineate the subexpressions of a regular expression and capture the substrings of an input string. You can use grouping constructs to do the following:

   - Match a subexpression that is repeated in the input string.

   - Apply a quantifier to a subexpression that has multiple regular expression language elements. For more information about quantifiers, see Quantifiers.

   - Include a subexpression in the string that is returned by the Regex. Replace and Match. Result methods.

   - Retrieve individual subexpressions from the Match.Groups property and process them separately from the matched text as a whole.

| Symbol      | Description | Example   |E-mail Example
| ----------- | ----------- |-----------|-----------|
| `()`       | Grouping unifies a pattern or string so that it is matched in a complete block |`(ab)` means `a` and `b` form a group | In `([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})`, there are 3 distinct groups. Group 1: `[a-z0-9_\.-]+`  Group 2: `[\da-z\.-]+`  Group 3: `[a-z\.]{2,6}`


### Bracket Expressions
A bracket expression is either a matching list expression or a non-matching list expression. It consists of one or more expressions: ordinary characters, collating elements, collating symbols, equivalence classes, character classes, or range expressions.

| Symbol      | Description | Example   |E-mail regex example|
| ----------- | ----------- |-----------|-----------|
|`[]`   | Matching any single character within the brackets | `[C]a[tr]` means any matching strings that have `C` followed by an `a` then a `t` or a `r` like : `Car` or `Cat`|`[a-z0-9_\.-]` means any matching with `a-z0-9_\.-`
|`[-]`| Specifies any matching within the range of characters (character on the left side of the hypen `-` is the start of the range and the character on the right side of the hypen specifies the end of the range) | `[a-z]` means any matching character between letter `a` in small caps and `z` in small caps (including `a` and `z`) / `[0-9]` means any matching integer between `0` and `9` (including `0` and `9`) | `[a-z0-9_\.-]` an any matching characters between `a` and `z`, `0` and `9`.


### Greedy and Lazy Match
```*```, ```+```, ```{}```, and ```?```
**Greedy Match**
For every position in the string try to match the pattern at that position.
If there’s no match, go to the next position.

**Lazy Match**
The opposite of a greedy match, meaning it will repeat the algorithm a minimal number of times.
```?``` is a quantifier by itself, but if added after another quantifier (or even itself) it switches the matching mode from greedy to lazy

In this regular expression:
```
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/
```
 - ```([\da-z\.-]+)``` the ```+``` operator is greedy as it allows character matching from one to an infinite amount of times

### Boundaries
```\b``` represents an anchor, it is similar to ```$``` and ```^```, matching positions where one side is a word character and the other side is not a word character.



### Back-references

* If you are looking to learn, build and perform tests, please visit - https://regexr.com/ (more sprecifically https://regexr.com/39nr7)
* For more information on regular expressions, please visit - https://en.wikipedia.org/wiki/Regular_expression


## Author
HappyPanda6453

Link to the author's GitHub profile https://github.com/HappyPanda6453
