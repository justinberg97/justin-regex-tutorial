# Justin Berg Official Regex URL Tutorial

Introductory paragraph (replace this with your text)

## Summary

A regex is a regular expression that can be usex to match paterns in searches. For this example, we can use a regex that can extract a url from a larger sample of text so that we can properly search for what we need.  

It will look something like this: 

https?:\/\/(www\.)?[-a-zA-Z0-9@:%._\+~#=]{1,256}\.[a-zA-Z0-9()]{1,6}\b([-a-zA-Z0-9()@:%_\+.~#?&//=]*)



## Table of Contents

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

A URL search regex will have many components.  

1. The Protocal Identifier:  This will be used to identify the protocal which in turn will allow us to access the url.  It will typically be something like this: https?

2. The Separator:  This is used to separate the before mentioned protocal identifier and the rest of the regex.  It will typically look something like this: :\/\/

3. The Subdomain:  This component is optional.  It is before the domain name and will typically be some sort of "www" variation.  For example: (www\.)?

4.  The Domain Name:  This component will match a string with different characters, dots, and dashes that are found in the url.  It will look someting like this: [-a-zA-Z0-9@:%._\+~#=]{1,256}

5.  The Top-Level Domain:  This will match a string with one of six alphanumeric characters in the url.  It will look something like this typically: \.[a-zA-Z0-9()]{1,6}

6.  The Path, Query, and Fragment:  These components are optional.  The path will usually come after the domain and it can discern where the location of a resource is on a server.  The query will usually come after the path.  It includes key value pairs that can clarify more information.  The fragment wil typically follow the query and will include a reference that matches a location within a resource.  This all put together will look someting like this: \b([-a-zA-Z0-9()@:%_\+.~#?&//=]*)



### Anchors

In a regex, the anchors are special characters that can match the position of a character in a string.  They are usually either the carat or dollar sign symbol.  For example, this code snippet: ^https?
will only match expressions that start with http or https.  In the same way, this expression: \.com$
will only match with strings that have a .com at the end.  Using these together ensures that the regex will match the entire line.  

### Quantifiers

Quantifiers in a regex are characters that specify the number of times a character or group of characters appear in a string.  Usually, they are the *, +, ?, or {n,m}.  

For example: https?://www\.* will match a string with followed by zero or more www characters.  

Another example: https?://[-a-zA-Z0-9@:%._+~#=]+
This will utilize the plus symbol and match an expression with http:// and then followed by characters that are alphanuemeric.  

An example of the ? quantifier: https?://(www\.)?
this will match an http:// that is followed by zero or more "www" characters.  

Lastly, the {n,m} quantifier: https?://[-a-zA-Z0-9@:%._+~#=]{4,256}
This will match with an http:// followed by anywhere from 4 to 256 characters that are alphanuemeric. 

### OR Operator

The "|" character is the OR operator in a regex.  It allows us to match one out of multiple options and patterns.  It can match on either side of the operator.

For example, if I wanted to match the URL that use both http and https, I can use the OR as follows: 

http|https

This same concept can be used in all kinds of regex url searches, like a top-level domain:


\.com|\.org|\.edu

### Character Classes

A regex character class is an expression that is enclosed in brackets like this: []. 

### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
