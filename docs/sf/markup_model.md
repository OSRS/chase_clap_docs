[[_TOC_]]

# Markup language reference

In order to make standard models, we need a way to represent the vocabulary for such things.
This vocabulary will be based upon a well-defined, mostly-complete representation syntax loosely taken from [BNF](https://en.wikipedia.org/wiki/Backus%E2%80%93Naur_form)/[EBNF](https://en.wikipedia.org/wiki/Extended_Backus%E2%80%93Naur_form)/[ABNF](https://en.wikipedia.org/wiki/Augmented_Backus%E2%80%93Naur_form)

The initial standard encodings will be json, with use from Python as the prototype implementation language.
Each language is expected to have its own implementation model, which may consist of simple dictionaries/hashtables or use full-fledged classes/structs.

Since the standard models will define all properties associated with a type, both a dictionary and class based approach will work. However, it is also expected that extended properties may exist on encoded values, which an implementation should be able to deal with cleanly.

The conventions for data encodings and dealing with "extended attributes" is described in the [standardization](standardization.md) page.

## Terminal values (copied from [rfc2234](https://tools.ietf.org/html/rfc2234))

Rules resolve into a string of terminal values, sometimes called characters.  In ABNF a character is merely a non-negative integer.  In certain contexts a specific mapping (encoding) of values into a character set (such as ASCII) will be specified.

Terminals are specified by one or more numeric characters with the base interpretation of those characters indicated explicitly.  The following bases are currently defined:
```
    b   =  binary
    d   =  decimal
    x   =  hexadecimal
```
Hence, where CR is the value "13":
```
    CR  =  %d13
    CR  =  %x0D
```
## Symbols

| Usage | Notation | Description |
| ----- | ----- | ----- |
| definition | = | term = definition |
| concatenation | , | terms are combined, e.g.  "1", "2" -> "12" |
| termination | ; | ends the definition, for single line definitions this can be omitted |
| alternation | \| | a OR b (options) |
| optional | [...] | present or absent |
| repetition | {...} | repeating, {"a"} and *{"a"} means zero or more, +{"a"} means 1 or more, {"a"}5 means up to 5, 2{"a"}5 means 2,3,4 or 5 times |
| grouping | (...) | used to denote a group taken as a unit |
| terminal string | "..." | defines a "literal" string of terminal values |
| terminal string | '...'  | defines a "literal" string of terminal values (alternate notation) |
| comment | (* ... *) | inlines a comment not to be interpretted as part of the definition |
| special sequence | ?...? | |
| exception | - | used to denote an exception from the rule, as in "subtract this" |


## Simple codes
Baseline standard terminal codes exist that will be used throughout other type definitions. These codes should be simple to understand and do not represent encodings, instead conveying value intent.

For example, an integer is a numeric value of composed of an optional sign followed by digits. the notion of a digit is such as baseline code.

### Codes

#### Binary Data
>  BIT = "0" | "1"

>  NIBBLE = BIT, BIT, BIT, BIT

>  BYTE = NIBBLE, NIBBLE

#### Number representation

>  NON-ZERO-DIGIT = "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9"

>  DIGIT = "0" | NON-ZERO-DIGIT

>  NATURAL-NUMBER = NON-ZERO-DIGIT, {DIGIT}

>  INTEGER = "0" | ["-"], NATURAL-NUMBER

>  UNSIGNED-INTEGER = "0" | NATURAL-NUMBER

>  REAL = ["-"], NATURAL-NUMBER, [".", UNSIGNED-INTEGER]

>  SN = ["-"], NATURAL-NUMBER, [".", UNSIGNED-INTEGER], [ "E" | "e", INTEGER]

>  hex = digit | 'a' | 'b' | 'c' | 'd' | 'e' | 'f'

#### Well-known characters

>  BS = %x08

>  TAB = %x09

>  LF = %x0A

>  CR = %x0D

>  CRLF = CR, LF

>  SP = %x20

>  DEL = %x7F

>  WHITESPACE-CHAR = SP | LF | CR | TAB

>  WHITESPACE = +{WHITESPACE-CHAR}

>  UNSAFE-CHAR = %x00-1F - ( BS | TAB | LF | CR )


### Literal information

For well-known definitions, such as a range of values, they can be represented in our markup as follows:

>  NUMERIC = NATURAL-NUMBER | INTEGER | UNSIGNED-INTEGER | REAL | SN

>  RANGE = "R", "(" | "[", NUMERIC, "," NUMERIC, ")" | "]"

   ``` example range: R(2, 5]  meaning integers greater than 2 and less than or equal to 5 ```

>  NULL = ""; the absence of a value, may have a literal representation in encodings

>  PRIMITIVE = (* any of the primitive types, see [base types](base_types.md) for more *)

>  STRUCT = (* a non-nullable structure or any of the simple types, see [base types](base_types.md) for more *)

>  VALUE_TYPE = PRIMITIVE | STRUCT

>  REFERENCE_TYPE = (* a nullable structure *)

>  VALUE = VALUE_TYPE

>  REFERENCE = NULL | REFERENCE_TYPE

>  ANY = VALUE | REFERENCE
