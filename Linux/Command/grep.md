# Grep Cheat Sheet

Grep is a command-line utility used for searching and matching patterns in text files. It provides powerful pattern matching capabilities for filtering and extracting data. This cheat sheet provides an overview of the most commonly used `grep` commands and options.

## Basic Usage

COMMAND | DESCRIPTION
---|---
`grep "pattern" <file>` | Search for lines containing a specific pattern in a file
`grep -r "pattern" <directory>` | Recursively search for a pattern in all files within a directory
`grep -i "pattern" <file>` | Perform a case-insensitive search for a pattern in a file
`grep -v "pattern" <file>` | Invert the search and display lines not matching the pattern

## Regular Expressions

COMMAND | DESCRIPTION
---|---
`grep -E "pattern" <file>` | Enable extended regular expressions for pattern matching
`grep -w "pattern" <file>` | Match whole words only (exact word match)
`grep -o "pattern" <file>` | Display only the matching part of the line

## Output Control

COMMAND | DESCRIPTION
---|---
`grep -n "pattern" <file>` | Display line numbers along with matching lines
`grep -c "pattern" <file>` | Count the number of lines matching a pattern
`grep -l "pattern" <file>` | Display only the filenames of files containing a pattern
`grep -L "pattern" <file>` | Display only the filenames of files not containing a pattern

## Context Control

COMMAND | DESCRIPTION
---|---
`grep -B <num> "pattern" <file>` | Display `<num>` lines of leading context before matching lines
`grep -A <num> "pattern" <file>` | Display `<num>` lines of trailing context after matching lines
`grep -C <num> "pattern" <file>` | Display `<num>` lines of context before and after matching lines

## File Type Filtering

COMMAND | DESCRIPTION
---|---
`grep "pattern" *.<ext>` | Search for a pattern in files with a specific extension
`grep "pattern" <file_pattern>` | Search for a pattern in files matching a specific pattern

## Other Useful Options

COMMAND | DESCRIPTION
---|---
`grep -q "pattern" <file>` | Quiet mode - suppress output, useful for script execution
`grep --exclude-dir=<dir_pattern>` | Exclude directories matching a specific pattern from the search

