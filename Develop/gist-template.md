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

A regex character class is an expression that is enclosed in brackets like this: [].  It can match any one character from a set.  This is used for matching one character that belongs to a specific type of characters.  

For example, if you are looking for a digit in the url, you can use something like this to return what you need: 

[0-9]

This returns any match between a single digit and the numbers 0-9.  

For searching url's, it is mostly used to match with characters that are usually found in a url.  

https?:\/\/(www\.)?[\w-@:%._+~#=]+

This will match with a http:// start and a "www" ending and will match one or more word characters, dots, dashes, and symbols inside the url. 

### Flags

Flags are added to the end of a regex.  They are charactes that modify the behavior of the regex.  

Usually, the "i" flag is used.  

In this example: https?://(www\.)?[\w-@:%._+~#=]+\.(com|org|edu)

The regex will match how I have been describing previously, but if you add the "i" flag to the end of it, will make the regex case insensitive so we can return both upper and lower case letters. 


### Grouping and Capturing

Grouping and capturing are used in regex's to group together parts of the expression and capture them for later use.  Grouping is done by enclosing the part of the regex in parantheses().  

For example: https?://(www\.)? 

This will make the "www" subdomain optional because it was grouped together by the parantheses and the ? quantifier applies to that whole group. 

Capturing is used for extraction and also utilizes parantheses.  

For example: https?:\/\/(www\.)?[-a-zA-Z0-9@:%._+~#=]+\.([a-zA-Z0-9()]{1,6})

This will capture the tdl, which can then be accessed by refering to the group number, becuase it was captured as a group.  


### Bracket Expressions

A bracket expression is a syntax that can match a range of characters.  It is created by placing anything inside of a bracket like so: [A-Z].  This will allow you to find a match to any uppercase letter from a through z.  

For url searches, you can use it to find a match to a veriety of different characters, like this example: 

https?:\/\/(www\.)?[\w-@:%._+~#=]+


This can find a match from any of the given characters.  

### Greedy and Lazy Match

Greedy and Lazy matches refer to ways that the expression engine handles repeated quantifiers, like the "*" and "+" characters.  

A greedy match is default to a regex.  

For example: .* will match with any character zero or more times, so "1234" will return a match of the entire string.  

A lazy match does the oposite. 

.*? will match only with "1" in the before mentioned string because it only matches with as little characters as possible. 

In the context of a url search, if you wanted to return the entire domain name of a url, you would use a greedy search like so: 

https?:\/\/(www\.)?([-a-zA-Z0-9@:%._+~#=]+\.)+[a-zA-Z0-9()]{1,6}

This returns the entire domain name.

https?:\/\/(www\.)?[-a-zA-Z0-9@:%._+~#=]+\.([a-zA-Z0-9()]{1,6}?)

This lazy match will only return the first match in the group, so the whole domain name will not display. 

### Boundaries

Boundries are special characters or constructs that define the start or end of a match.  It is usually either a "^" or a "$". 

The carat specifies that the match must occur at the beginning of the text.  So, 

^https will only return matches where the http is at the start of the string.  

In the same way: \.com$ wil only return a match that has .com at the end of the string.  

### Back-references

A back-reference is a construct that allows you to match a previously captured group again in the same regex.  It is created by a backslash followed by the number of the capturing group that you want to match.  

([-a-zA-Z0-9@:%._+~#=]+)\1

This will check for alphanuemeric characters, and then check to see if the next sequence of characters are the same, which will create a repeating sequence.  

You can do the same with http and .com like so: 

^(https?:\/\/(www\.)?[-a-zA-Z0-9@:%._+~#=]+\.)([-a-zA-Z0-9@:%._+~#=]+)\2$



### Look-ahead and Look-behind

These are special constructs that allow you to match patterns only if they are followed by or preceded by another specific pattern.  

For example, look-ahead is used in a url search like so: 

https(?=://)

This will only match if the https is followed by //. 

In the same way, com(?=.) will only return a match if it the com is preceded by a . because we are using look-behind. 

## Author

My name is Justin Berg.  I am planning on moving to NYC with my girlfriend Salma after our bootcamp is over.  We have a goldendoodle named Latte.  I love learning about programming and I hope that this tutorial gave you some inspiration to keep learning! 

https://github.com/justinberg97/justin-regex-tutorial


