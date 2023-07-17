# sed Cheat Sheet

`sed` (stream editor) is a powerful command-line utility used for text manipulation. It reads text from a file or standard input, performs operations (such as search, replace, and delete), and outputs the modified text. This cheat sheet provides an overview of commonly used `sed` commands and options.

## Basic Usage

COMMAND | DESCRIPTION
---|---
`sed 's/pattern/replacement/' <file>` | Search and replace a pattern with a replacement in a file
`sed 's/pattern/replacement/g' <file>` | Search and replace all occurrences of a pattern with a replacement in a file
`sed 'N,Ms/pattern/replacement/' <file>` | Search and replace a pattern in a specific range of lines in a file
`sed 'N,Ms/pattern/replacement/g' <file>` | Search and replace all occurrences of a pattern in a specific range of lines in a file
`sed 'N,Ms/pattern/replacement/I' <file>` | Search and replace a pattern with a replacement (case-insensitive) in a specific range of lines in a file

## Options

OPTION | DESCRIPTION
---|---
`-i` | Edit files in-place (save changes to the original file)
`-e 'script'` | Add script commands to be executed
`-n` | Suppress automatic printing of pattern space

## Addressing

ADDRESS | DESCRIPTION
---|---
`/pattern/` | Match lines containing a pattern
`/pattern1/,/pattern2/` | Match lines between two patterns (inclusive)
`n` | Match the nth line
`$` | Match the last line

## Commands

COMMAND | DESCRIPTION
---|---
`p` | Print the current pattern space
`d` | Delete the current pattern space
`a\text` | Append text after the current line
`i\text` | Insert text before the current line
`c\text` | Change the current line to text
`r file` | Read and insert the contents of a file
`w file` | Write the pattern space to a file
`q` | Quit (exit) the script

## Regular Expressions

REGEX | DESCRIPTION
---|---
`.` | Match any single character
`*` | Match zero or more occurrences
`^` | Match the beginning of a line
`$` | Match the end of a line
`[abc]` | Match any character from the given set
`[^abc]` | Match any character except those in the given set
`\(pattern\)` | Capture pattern for later use
`&` | Replace with the matched pattern

## Examples

EXAMPLE | DESCRIPTION
---|---
`sed 's/foo/bar/' file.txt` | Replace the first occurrence of "foo" with "bar" in file.txt
`sed 's/foo/bar/g' file.txt` | Replace all occurrences of "foo" with "bar" in file.txt
`sed '1,5d' file.txt` | Delete lines 1 to 5 in file.txt
`sed '/pattern/d' file.txt` | Delete lines containing "pattern" in file.txt
`sed -n '/pattern/p' file.txt` | Print lines containing "pattern" in file.txt

