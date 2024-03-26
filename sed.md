Use GNU sed only.
`brew install gnu-sed` on macOS

# Regular expressions
The **default** syntax is  basic regular expression ([BRE](https://www.gnu.org/software/sed/manual/html_node/BRE-syntax.html#BRE-syntax)).
The extended regular expression ([ERE](https://www.gnu.org/software/sed/manual/html_node/ERE-syntax.html#ERE-syntax)) is enabled with `-E`

The difference is in chars: `?`,`+`,`()`,`{}`,`|` (in BRE they match themselfs)

### BRE - basic regular expressions

| syntax | description |
|---|---|
| `abc` | matches "abc" |
| `a*` | 0 or more `a` |
| `.` | any char including newline |
| `^` | beginning of line |
| `$` | end of line |
| `[abc]` | matches "a", "b" or "c" |
| `[x-z]` | matches "x", "y", "z" |
| `[[:blank:]]` | matches `[:blank:]` character class |
| `a\+` | one or more "a" (**GNU extension**) |
| `\?` | zero or one "a" (**GNU extension**) |
| `\{i\}` | As `*`, but matches exactly i sequences (i is a decimal integer; for portability, keep it between 0 and 255 inclusive) |
| `\{i,j\}` | Matches between i and j, inclusive, sequences |
| `\{i,\}` | Matches more than or equal to i sequences. |
| `\(regexp\)` | Groups the inner regexp as a whole, this is used to:<br>- Apply postfix operators, like `\(abcd\)*`: this will search for zero or more whole sequences of "abcd", while abcd* would search for ‘abc’ followed by zero or more occurrences of ‘d’. Note that support for `\(abcd\)*` is required by POSIX 1003.1-2001, but many non-GNU implementations do not support it and hence it is not universally portable.<br>- Use back references (see below).
| `regexp1\|regexp2` | Matches either `regexp1` or `regexp2`. Use parentheses to use complex alternative regular expressions. The matching process tries each alternative in turn, from left to right, and the first one that succeeds is used. (**GNU extension**) |
| `regexp1regexp2` | Matches the concatenation of regexp1 and regexp2. Concatenation binds more tightly than `\|`, `^`, and `$`, but less tightly than the other regular expression operators. |
| `\digit` | Matches the digit-th `\(…\)` parenthesized subexpression in the regular expression. This is called a back reference. Subexpressions are implicitly numbered by counting occurrences of `\(` left-to-right. |
| `\n` | Matches the newline character. |
| `\char` | Matches char, where char is one of `$`, `*`, `.`, `[`, `\`, or `^`. Note that the only C-like backslash sequences that you can portably assume to be interpreted are `\n` and `\\`; in particular `\t` is not portable, and matches a "t" under most implementations of sed, rather than a tab character |

### ERE - extended regular expressions

| syntax | description |
|---|---|
| `abc` | matches "abc" |
| `a*` | 0 or more `a` |
| `.` | any char including newline |
| `^` | beginning of line |
| `$` | end of line |
| `[abc]` | matches "a", "b" or "c" |
| `[x-z]` | matches "x", "y", "z" |
| `[[:blank:]]` | matches `[:blank:]` character class |
| `a+` | one or more "a" (**GNU extension**) |
| `?` | zero or one "a" (**GNU extension**) |
| `{i}` | As `*`, but matches exactly i sequences (i is a decimal integer; for portability, keep it between 0 and 255 inclusive) |
| `{i,j}` | Matches between i and j, inclusive, sequences |
| `{i,}` | Matches more than or equal to i sequences. |
| `(regexp)` | Groups the inner regexp as a whole, this is used to:<br>- Apply postfix operators, like `(abcd)*`: this will search for zero or more whole sequences of "abcd", while abcd* would search for ‘abc’ followed by zero or more occurrences of ‘d’. Note that support for `(abcd)*` is required by POSIX 1003.1-2001, but many non-GNU implementations do not support it and hence it is not universally portable.<br>- Use back references (see below).
| <code>regexp1\|regexp2</code> | Matches either `regexp1` or `regexp2`. Use parentheses to use complex alternative regular expressions. The matching process tries each alternative in turn, from left to right, and the first one that succeeds is used. (**GNU extension**) |
| `regexp1regexp2` | Matches the concatenation of regexp1 and regexp2. Concatenation binds more tightly than `|`, `^`, and `$`, but less tightly than the other regular expression operators. |
| `\digit` | Matches the digit-th `(…)` parenthesized subexpression in the regular expression. This is called a back reference. Subexpressions are implicitly numbered by counting occurrences of `\(` left-to-right. |
| `\n` | Matches the newline character. |
| `\char` | Matches char, where char is one of `$`, `*`, `.`, `[`, `\`, or `^`. Note that the only C-like backslash sequences that you can portably assume to be interpreted are `\n` and `\\`; in particular `\t` is not portable, and matches a "t" under most implementations of sed, rather than a tab character |

### character classes

| class | description |
|---|---|
| `[:alnum:]` |  Alphanumeric characters: `[:alpha:]` and `[:digit:]`; in the C locale and ASCII character encoding, this is the same as `[0-9A-Za-z]` |
| `[:alpha:]` |  Alphabetic characters: `[:lower:]` and `[:upper:]`; in the C locale and ASCII character encoding, this is the same as `[A-Za-z]` |
| `[:blank:]` |  Blank characters: space and tab |
| `[:cntrl:]` |  Control characters. In ASCII, these characters have octal codes 000 through 037, and 177 (DEL). In other character sets, these are the equivalent characters, if any. |
| `[:digit:]` |  Digits: `0 1 2 3 4 5 6 7 8 9` |
| `[:graph:]` |  Graphical characters: `[:alnum:]` and `[:punct:]` |
| `[:lower:]` |  Lower-case letters; in the C locale and ASCII character encoding, this is `a b c d e f g h i j k l m n o p q r s t u v w x y z` |
| `[:print:]` |  Printable characters: `[:alnum:]`, `[:punct:]`, and space |
| `[:punct:]` |  Punctuation characters; in the C locale and ASCII character encoding, this is ``! " # $ % & ' ( ) * + , - . / : ; < = > ? @ [ \ ] ^ _ ` { \| } ~`` |
| `[:space:]` |  Space characters: in the C locale, this is tab, newline, vertical tab, form feed, carriage return, and space |
| `[:upper:]` |  Upper-case letters: in the C locale and ASCII character encoding, this is `A B C D E F G H I J K L M N O P Q R S T U V W X Y Z` |
