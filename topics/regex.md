# Regular Expressions

Regular Expressions are mostly used for validation to target certain characters. According to MDN regular expressions are patterns used to match character combinations in strings. In JavaScript, regular expressions are also objects. These patterns are used with the exec and test methods of RegExp, and with the match, replace, search, and split methods of String.

## Using regular expressions

Regular Expressions can be built by enclosing a pattern in slashes.

```js
// Regular expression
let regExpr = /abc/
```
## Testing for matches

Regular expressions objects have many different methods, one of the easiest to understand is `test`. Test() will return a boolean.

```js
let regExpr = /abc/

// check for match
if(regExpr.test("test this")){
console.log("That did not match.")
}
else if(regExpr.test("abc")){
console.log("Thats a match!")
}
```

## Testing groups of characters

Groups of characters can be tested by using square brackets and the test method. `[0123456789]` is the same as `[0-9]`.

```js
// check for groups of characters
let numbers = /[0-9]/

if(numbers.test("Numbers are 545984 ")){
console.log(" Yes they are!")
}
```
Just remember this checks for a digit not for a exact match.

## Testing for a valid email

Testing for a valid email can be tricky; the simplest way is to add a regular expression. In this example, we will use a pre-generated literal from [Email Address Regular Expression That 99.99% Works](http://emailregex.com/) to validate an email.

```js
// email validation
let email = trythis@youremail.com
let regexEmail = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/

if(regexEmail.test(email)){
console.log("This is a real email")
}else{
console.log("This is not a valid email")
}
```
## Domain Validation

Domain validation works the same way as email validation. This example uses a domain regular expression literal created just for domains.

```js
// domain validation
let domain = google.com
let regexDomain = ^(?:(?:(?:[a-zA-z\-]+)\:\/{1,3})?(?:[a-zA-Z0-9])(?:[a-zA-Z0-9-\.]){1,61}[a-zA-Z0-9](?:\.[a-zA-Z]{2,})+|\[(?:(?:(?:[a-fA-F0-9]){1,4})(?::(?:[a-fA-F0-9]){1,4}){7}|::1|::)\]|(?:(?:[0-9]{1,3})(?:\.[0-9]{1,3}){3}))(?:\:[0-9]{1,5})?$


if(regexDomain.test(domain)){
console.log("This is a real domain")
}else{
console.log("This is not a valid domain")
}
```

## Additional Resources and Reading

- [Regular Expressions - Javascript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions)
- [Regular Expressions | Eloquent Javascript](http://eloquentjavascript.net/09_regexp.html)
- [Email Address Regular Expression That 99.99% Works](http://emailregex.com/)
