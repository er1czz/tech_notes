# Regular Expressions (Regex)
- symbols representing a text pattern
- regular expression processor
- match, search, and replace text

## Engines: 
- C/C++, Python, Java, Ruby, Apache, Perl, MySQL, PHP, .NET, Unix, etc.

## Sandbox (websites)
- regexr.com, regex101.com, RegEx Pal, etc.

## Notation Conventions
- forward slashes ```/test/```
- text string  ```"text"```

## Modes
- standard:**/re/** (find first match)
- gloab:**/re/g** (find all matches)
- case insensitive: **/re/i**
- multilines: **/re/m** (default just one line)

## Grep g/re/p
- global regular expression print

## Literal Characters
- /car/ matches "car" and the first three letters of "carnival"
- case-sensitive (by default)

## Metacharacters (characters with special meaning)
- Wildcard ```.```: any single character including space except line break
- Escaping metacharacters: ```\``` **backslash**
- Quotation marks are not metacharacters, no need to escape
- Spaces
- Tabs (```\t```)
- Line returns (``` \r, \n, \r\n```)

## Greedy Expressions

## Define a character set (customize) 
- ```[``` Begin a character set 
- ```]``` End a character set
- Match only one of the characters
  - ```/gr[ea]y/``` matches "grey" and "gray"
  - ```/gr[ea]t/``` does NOT match "great"
- Order in set does not matter

## Character ranges
- ```-``` hyphen: range of characters, includes all characters between two characters
- Caution: ```[50-99]``` is the same as ```[0-9]```, a character set including 5, 0-9, and 9
- To mach a phone number ```[0-9][0-9][0-9]-[0-9][0-9][0-9]-[0-9][0-9][0-9][0-9]``` inside is character range, outside is a literal character

## Negative character set (caret)
- ```^```: not any one of several characters
- add ^ as the first character inside a character set

## Shorthand character set
- ```\d``` digit ```[0-9]```
- ```\w``` word character ```[a-zA-Z0-9_]```
  - **caution: underscore is a word character, whereas hyphen is not a word character**   
- ```\s``` whitespace ```[\t\r\n]```
- ```\D``` not digit ```[^0-9]```
- ```\W``` not word character ```[^a-zA-Z0-9_]```
- ```\S``` not whitespace ```[^\t\r\n]```
  - **caution**: ```[^\s] is equivalent to [\S]``` but ```[^\s\d] is NOT equivalent to [\S\D]```

## Repetition Metacharacters (always after a character)
- ```*``` (asterisk) Preceding item, zero or more times
- ```+``` (plus sign) Preceding item, one or more times
  - ```/.+/``` match any string of a character except a line return  
- ```?``` (question mark) Preceding item, **zero or one time**
  - ```/colo?r/``` match color or colour

### Quantified repetition ```{``` (min) and (max)```}```
- ```/d{4,8}/```: match number with four to eight digits
- ```/d{4}/```: match number with exactly four digits (min is max)
- ```/d{4,}/```: match number with four or more digits (max is infinite)
- ```/\d{0,}/```: is equals to ```/\d*/```
- ```/\d{1,}/```: is equals to ```/\d+/```
  - e.g. ```/\d{3}-\d{3}-\d{4}/``` matches US phone number

## Eager, Greedy are the nature of RE processor (default)

## Lazy Expression ```?```
- ```*?``` repeat
- ```+?``` lazy, opposed to greedy

## Grouping Metacharacters
- ```(``` start grouped expression
- ```)``` end grouped expression

## Alternation Metacharacter ```|``` (an OR operator)
- ordered: **leftmost** experession gets precedence
- multiple choices can be *daisy-chained*
- Group alternation expressions to keep them distinct
- Longer alternative first 
  - e.g. ```/(nothing/not/no)/``` will prevent result such as "**do no**thing"
  
## Efficiency
- Put simple (most efficient) expression first

## Start and End Anchors 
- reference a position, not an actual character
- Zero-width
- ```^``` start of string/line
- ```$``` end of string/line
- ```\A``` start of string, never end of line
- ```\Z``` end of string, never end of line
  - ```/^apple/ or /\Aapple/``` must be the first word

## Line breaks and multiline mode
- Python: re.search("^regex$", "string", re.MULTILINE)

## Word Boundaries
- reference a position, not an actual cahracter
- ```\b``` Word boundary (start/ end of word)
- ```\B``` Not a word boundary
- Before the first word character in the string and after the last word character in the string
- Between a word character and non-word character
- Word characters ```[A-Za-z0-9_]``` *underscore is a word character*
  - e.g. find 15-letter word including hyphenated words ```/\b[\w\-]{15}\b/gm```
    - ```\b``` word boundary
    - ```[\w\-]``` character set of words and hyphen
    - ```{15}``` repetition 15
    - ```g``` global search
    - ```m``` multiline mode
