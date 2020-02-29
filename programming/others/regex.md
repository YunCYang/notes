# Regex

## RegExp
Construct regular expression with the RegExp constructor. Pattern is written as a normal string.

`const re1 = new RegExp("abc");`

### `exec` method

Returns null when no match was found. Returns an object (array) of strings, the first element is the string that matches. The object also has a *index* property that tells us where in the string the successful match begins.

```
let match = /\d+/.exec("one two 100");
console.log(match);
// → ["100"]
console.log(match.index);
// → 8
```

When the regular expression contains subexpressions grouped with parentheses, the text that matched those groups will also show up in the array. The whole match is always the first element. The next element is the part matched by the first group (the one whose opening parenthesis comes first in the expression), then the second group, and so on.

```
let quotedText = /'([^']*)'/;
console.log(quotedText.exec("she said 'hello'"));
// → ["'hello'", "hello"]
```

When a group does not end up being matched at all (for example, when followed by a question mark), its position in the output array will hold undefined. Similarly, when a group is matched multiple times, only the last match ends up in the array.

```
console.log(/bad(ly)?/.exec("bad"));
// → ["bad", undefined]
console.log(/(\d)+/.exec("123"));
// → ["123", "3"]
```

`exec` method also has a `source` property containing the string that expression was created from, and a `lastIndex` property storing the index where the next match will start.

## Enclosing patterns in forward slash (/) characters

Since the pattern is not a string, using back slash (\) to escape characters becomes necessary. Codes like \n are preserved.

`let re2 = /abc/;`

### `test` method

`test` method will written a Boolean base on whether there's a match or not.

```
console.log(/abc/.test("abcde"));
// → true
```

### `string` method from string values

Behaves similarily to `exec` method from `RegExp`.

```
console.log("one two 100".match(/\d+/));
// → ["100"]
```

## `replace` Method

The replace method can use regex as the first argument. Normally only the first match is replaced. When a g (global) option is added, all matches will be replaced.

```
console.log("Borobudur".replace(/[ou]/, "a"));
// → Barobudur
console.log("Borobudur".replace(/[ou]/g, "a"));
// → Barabadar
```

The real power of using regular expressions with replace comes from the fact that we can refer to matched groups (parenthesized groups) in the replacement string. Can go all the way from *$1* to *$9*. The whole match can be referred to with *$&*.

```
console.log(
  "Liskov, Barbara\nMcCarthy, John"
    .replace(/(\w+), (\w+)/g, "$2 $1"));
// → Barbara Liskov
//   John McCarthy
```

A function can also be passed as the second argument to `replace`.

```
let s = "the cia and fbi";
console.log(s.replace(/\b(fbi|cia)\b/g,
            str => str.toUpperCase()));
// → the CIA and FBI
```

## Greed

The repetition operators (+, *, ?, {}) are greedy by default, meaning they match as much as they can and backtrack from there.

```
function stripComments(code) {
  return code.replace(/\/\/.*|\/\*[^]*\*\//g, "");
}
console.log(stripComments("1 + /* 2 */3"));
// → 1 + 3
console.log(stripComments("1 /* a */+/* b */ 1"));
// → 1  1 instead of 1 + 1 because of greedy operator
```

If you put a question mark after the repetition operators (+?, *?, ??, {}?), they become nongreedy and start by matching as little as possible, matching more only when the remaining pattern does not fit the smaller match.

```
function stripComments(code) {
  return code.replace(/\/\/.*|\/\*[^]*?\*\//g, "");
}
console.log(stripComments("1 /* a */+/* b */ 1"));
// → 1 + 1
```

## Rules

- `[]`: match only one character in the set of characters between the brackets.
- `[0-9]`: hyphen indicates range, ordering is determined by Unicode number.
- `\b`: word boundary. A word boundary can be the start or end of the string or any point in the string that has a word character (as in \w) on one side and a nonword character on the other.
- `[^]`: any character that is not in the empty set of characters. The difference between `[^]` and `.` is that `.` does not includes newline characters.
- `g`: global
- `i`: case insensitive
- `y`: sticky. The match will succeed only if it starts directly at `lastIndex`, whereas with *global*, it will search ahead for a position where a match can start.

## Dynamically creating RegExp object example

```
let name = "harry";
let text = "Harry is a suspicious character.";
let regexp = new RegExp("\\b(" + name + ")\\b", "gi");
console.log(text.replace(regexp, "_$1_"));
// → _Harry_ is a suspicious character.
```

```
let name = "dea+hl[]rd";
let text = "This dea+hl[]rd guy is super annoying.";
let escaped = name.replace(/[\\[.+*?(){|^$]/g, "\\$&");
let regexp = new RegExp("\\b" + escaped + "\\b", "gi");
console.log(text.replace(regexp, "_$&_"));
// → This _dea+hl[]rd_ guy is super annoying.
```

## Looping over matches example

```
let input = "A string with 3 numbers in it... 42 and 88.";
let number = /\b\d+\b/g;
let match;
while (match = number.exec(input)) {
  console.log("Found", match[0], "at", match.index);
}
// → Found 3 at 14
//   Found 42 at 33
//   Found 88 at 40
```

This makes use of the fact that the value of an assignment expression (=) is the assigned value. So by using match = number.exec(input) as the condition in the while statement, we perform the match at the start of each iteration, save its result in a binding, and stop looping when no more matches are found.

[Back](../../README.md)
