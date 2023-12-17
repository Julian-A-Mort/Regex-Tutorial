# Password Validation Regex Tutorial

Welcome to our tutorial on one of the most mysterious and important regular expressions: Password Validation.

One of the most important uses of regex is in validating the complexity and strength of a users password. A regex pattern can enforce a mix of numbers, characters, symbols and more. 

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
In regular expressions quantifiers are used to dictate how many times a charachter, class or group need to occur for the password to be valid. This is expressed in the `{min,max}` format. In which `min` referes to the minimum number of times the defined element must occur, where as `max` refers to the maximum number of times.

So in the following code the relevent characters are `[A-Za-z\d@$!%*?&]` and `{8,}`.

```
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$
```

In this password pattern `{8,}` denotes that the characters from our primary charachter set `[A-Za-z\d@$!%*?&]` must appear 8 times.

* `8`: The password must contain a minimym of 8 characters
* `,`: This indicates there is no upper limit on charachter usage

In the following code we have denoted both an upper and lower limit.

```
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,12}$
```

* `8`: Here again the password must contain a minimum of 8 characters
* `12`: This indicates the maximum number of times the charachter set can appear

### Character Classes
Charachter classes are used to define the charachter set to be used the password. Only characters that have been defined here will be accepted as valid.

In the following code the relevant section is `[A-Za-z\d@$!%*?&]`.

```
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$
```

In this code a number of different character classes are used:

* `[a-z]`: Matches any lowercase letter from `a` to `z`.
* `[A-Z]`: Matches any uppercase letter from `A` to `Z`.
* `[\d]`: A shorthand way of refrencing any digit, from `0` to `9`. 
* `[@$!%*?&]`: Specifies a set of special characters that can be used.

These different classes are combined within a set of `[]` brackets. 

Other potential character class refrences are:

* `\w`: Shorthand for any alphanumeric character, both upper and lower case, as well as the underscore (`_`). 
* `\W`: Shorthand for any non-word character outside the alphanumeric range, including most symbols and whitespaces.
* `\s`: For any whitespace character, rarely used in passwords.
* `\S`: Any chrachter that is not a whitespace. More likely to be used to ensure whitespace characters are not used.
* `\D`: Any charahcter that is not a digit.
* `[A-Fa-f0-9]`: For any hexadecimal digit.
* `[aeiou]`: Custom charachter sets can also be used. In this example we are matching to any lowercase vowel.

### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
