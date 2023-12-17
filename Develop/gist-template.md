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
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
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

### Grouping and Capturing
Grouping in regex is done using `()`. When part of a pattern are grouped the regex engine will treat the enclosed sequence as a single unit. This approach is  useful for applying quantifiers / conditions to an entire sequence rather than individual characters.

Using parentheses will also create a capturing group. This stores the part of the string that matches the group for use later in the regex or the larger application.

For our password validation we use `Non-Captruing Groups`, in which the pattern part is grouped without being captured. This is denoted as `(?:...)`.

```
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$
```

In our pattern the look-ahead assertions, for example `(?=.*[a-z])`, are examples of non-capturing groups. This allows us to impose multiple independent conditions on the string, such as containing a minimum of one letter or one upperclase etc.

This is important as we want to check the presence of certain character types, ensuring the different conditions can operate indepedndently without clashing with each other.

### Bracket Expressions
Bracket expressions are used to specify a character set that can match, together in a single position. This is done by using square brackets `[]`.

Bracket expressions are used throughout our regex:
```
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$
```

Here bracket expressions are used in two ways:

* Character Ranges: Here `[a-z]` and `[A-Z]` are character ranges. They match any charachter from `a` to `z`and `A` to `Z` respectively. 
* Combining Character Classes: In `[A-Za-z\d@$!%*?&]` we have combined multiple character classes/ranges. `A-Z`, `a-z`, `\d`and `@$!%*?&`.

Within brackets special characters `@$!%*?&` lose their special maning and are treated as their literal character. This allows them to be included directly without the need for escape characters.

### Greedy and Lazy Match
In a regular expression greedy and lazy (non-greedy) natching dictates how much of a string is matched when a quanitifer is involved.

Quantifiers in regex are greedy by default, meaning they match as many occurrences of a pattern as possible, capturing the longest possible string that satisfies the pattern.

In relation to our Password Validation regex:
```
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$
```

Here, the quantifier `{8,}` is greedy. It selects the longest possible sequence of characters from the set `[A-Za-z\d@$!%*?&]`, with a requirement of at least 8 characters. This ensures the entire string is evaluated during password validation, which is crucial for checking the minimum length requirement.

In contrast, lazy matching is achieved by placing a `?` after the quantifier. This approach matches the shortest possible string that satisfies the pattern.

While lazy matching provides a minimal match, it's not typically used in password validation scenarios like ours. In password validation, we generally prefer greedy matching to ensure the entire password (string) is thoroughly evaluated against all specified criteria.

### Back-references

### Look-ahead and Look-behind
Look-ahead and look-behind assertions in regular expressions allow for conditional matching based on the patterns that either follow or precede a given point in the string. This capability is crucial when the validity of a match depends on its surrounding context, but without including that context in the match itself.

Look-ahead Assertions
1. Positive Look-ahead: `(?=...)`
    * The specified pattern must follow.
    * Example: `X(?=Y)` wherein `X` matches only if `X` is followed by `Y`.
2. Negative Look-ahead: `(?!...)`
    * The specified pattern must not follow.
    * Example: `X(?!Y)` wherein `X` matches only if `X` is not followed by `Y`.

Look-behind Assertions
1. Positive Look-behind: `(?<=...)`
    * The specified pattern must precede.
    * Example: `(?<=Y)X` wherein matches `X` only if `X` is preceded by `Y`.
2. Negative Look-behind: `(?<!...)`
    * The specified pattern must not preced.
    * Eample: `(?<!Y)X` wherein matched `X` only if `X` is not preceded by `Y`.

Lets return to our Password Validation regex: 
```
^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$
```

Here we are using look-ahead assertions:

* `(?=.*[a-z])`: A positive a look-ahead assertion checking for the presence of at least one lowercase letter within the string. The `.*` allows for any characters (including none) between the start of the string and the lowercase letter.
* Similarly `(?=.*[A-Z])`, `(?=.*\d)` and `(?=.*[@$!%*?&])` ensure the presence of uppercase letters, digits, and special characters, respectively.

These look-ahead assertions are key in password validation as they ensure the password contains a variety of character types. They check conditions without consuming characters, meaning they do not affect the overall matching but ensure that each condition is met somewhere within the string.

Look-behind assertions, while not used in this password validation example, offer similar conditional checking for patterns preceding a given point in the string.

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
