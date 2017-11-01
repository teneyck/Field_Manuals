# Yara

### Description
 > YARA is a tool aimed at (but not limited to) helping malware researchers to identify and classify malware samples. With YARA you can create descriptions of malware families (or whatever you want to describe) based on textual or binary patterns. Each description, a.k.a rule, consists of a set of strings and a boolean expression which determine its logic. Let's see an example:

### Example

```
rule silent_banker : banker
{
    meta:
        description = "This is just an example"
        thread_level = 3
        in_the_wild = true

    strings:
        $a = {6A 40 68 00 30 00 00 6A 14 8D 91}
        $b = /md5: [0-9a-fA-F]{32}/
        $c = "UVODFRYSIHLNWPEJXQZAKCBGMT"

    condition:
        $a or $b or $c
}
```

The above rule is telling YARA that any file containing one of the three strings must be reported as silent_banker. This is just a simple example, more complex and powerful rules can be created by using wild-cards, case-insensitive strings, regular expressions, special operators and many other features that you’ll find explained in this documentation.

### Keywords
| | | |YARA keywords| | | |
|-|-|-|-|-|-|-|
|all|and|any|ascii|at|condition|contains|
|entrypoint|false|filesize|fullword|for|global|in|
|import|include|int8|int16|int32|int8be|int16be|
|int32be|matches|meta|nocase|not|or|of|
|private|rule|strings|them|true|uint8|uint16|
|uint32|uint8be|uint16be|uint32be|wide| | |


### Required Fields

#### Strings

Each string has an identifier consisting of a $ character followed by a sequence of alphanumeric characters and underscores, these identifiers can be used in the condition section to refer to the corresponding string. Strings can be defined in text or hexadecimal form, as shown in the following example:

```
strings:
    $a = {6A 40 68 00 30 00 00 6A 14 8D 91}
    $b = /md5: [0-9a-fA-F]{32}/
    $c = "UVODFRYSIHLNWPEJXQZAKCBGMT"
```

Text strings are enclosed in double quotes just like in the C language. Hex strings are enclosed by curly brackets, and they are composed by a sequence of hexadecimal numbers that can appear contiguously or separated by spaces. Decimal numbers are not allowed in hex strings.

#### Conditions

The condition section is where the logic of the rule resides. This section must contain a boolean expression telling under which circumstances a file or process satisfies the rule or not. Generally, the condition will refer to previously defined strings by using their identifiers. In this context the string identifier acts as a boolean variable which evaluate to true if the string was found in the file or process memory, or false if otherwise.

```
condition:
    $a or $b or $c
```


### Optional

#### Meta

Besides the string definition and condition sections, rules can also have a metadata section where you can put additional information about your rule. The metadata section is defined with the keyword meta and contains identifier/value pairs like in the following example:

```
meta:
        my_identifier_1 = "Some string data"
        my_identifier_2 = 24
        my_identifier_3 = true
```

#### Comments

You can add comments to your YARA rules just as if it was a C source file, both single-line and multi-line C-style comments are supported.

```
/*
    This is a multi-line comment ...
*/

rule CommentExample   // ... and this is single-line comment
```

[Documentation](http://yara.readthedocs.io/en/v3.6.0/writingrules.html)
