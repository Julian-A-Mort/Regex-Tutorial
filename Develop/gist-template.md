# Password Validation Regex Tutorial

Welcome to our tutorial on one of the most mysterious and important regular expressions: Password Validation.

One of the most important uses of regex is in validating the complexity and strength of a users password. A regex pattern can enforce a mix of numbers, charachters, symbols and more. 

By the end of this tutorial you will have an understranding of how this regex works and its applications.

## Summary

In this gist we will be going through and explain the a regex pattern to enfore a sites password policies. Here is the regex pattern we will be exploring: 

```
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$
```

We will be breaking down a number of key concepts as laid out below.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
<!-- - [OR Operator](#or-operator) -->
- [Character Classes](#character-classes)
<!-- - [Flags](#flags) -->
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors
In a regex we use the characters `^` and `$` as anchors donating the beginning and end of the pattern/password.

The `^` anchor is the start=of-string achor, denoting that the string starts with the following exact charachter.

For example in the following the start of the pattern is `(`.

```
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}
```
The `$` anchor meanwhile is the end-of-string achor, denoting the end of the pattern/password. In this case the `}` charachter is the end of the pattern.
```
(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$
```

The use of anchors is vital for password validation as it determines if validation rules have been applied correctly to the entrie password, not just part of it.

### Quantifiers

### OR Operator

### Character Classes

### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
