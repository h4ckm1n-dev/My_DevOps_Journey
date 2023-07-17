# AWK Cheat Sheet

AWK is a powerful text processing tool that allows you to manipulate and analyze structured text data. This cheat sheet provides an overview of the most commonly used AWK commands and options.

## Basic Usage

COMMAND | DESCRIPTION
---|---
`awk '{print $0}' <file>` | Print each line of a file
`awk '/pattern/' <file>` | Print lines matching a pattern
`awk '{print $1, $2}' <file>` | Print specific fields of each line
`awk '{print NR, $0}' <file>` | Print line number and content
`awk 'BEGIN{print "Header"} {print $0} END{print "Footer"}' <file>` | Add header and footer to output
`awk 'NR==1, NR==5 {print $0}' <file>` | Print lines from a specific range

## Field and Record Separators

COMMAND | DESCRIPTION
---|---
`awk -F',' '{print $1}' <file>` | Set the field separator to comma (`,`)
`awk -v FS=':' '{print $2}' <file>` | Set the field separator using a variable
`awk 'BEGIN{OFS=","} {print $1, $2}' <file>` | Set the output field separator to comma (`,`)
`awk 'BEGIN{ORS=","} {print $0} END{print "\n"}' <file>` | Set the output record separator to comma (`,`)
`awk -v RS='pattern' '{print $0}' <file>` | Set the record separator using a pattern

## Conditions and Expressions

COMMAND | DESCRIPTION
---|---
`awk '/pattern/{print $0}' <file>` | Apply actions to lines matching a pattern
`awk '$3 > 10 {print $0}' <file>` | Apply actions to lines where the third field is greater than 10
`awk '{if ($1 > $2) print "True"; else print "False"}' <file>` | Use if-else conditional statements
`awk '{total += $1} END{print total}' <file>` | Calculate and print the sum of a field

## Variables and Arrays

COMMAND | DESCRIPTION
---|---
`awk -v var=value '{print var}' <file>` | Use variables in AWK commands
`awk '{arr[$1] += $2} END{for (i in arr) print i, arr[i]}' <file>` | Use arrays to store and manipulate data

## Functions

COMMAND | DESCRIPTION
---|---
`awk '{print length($0)}' <file>` | Print the length of each line
`awk 'BEGIN{print toupper("hello")}'` | Convert a string to uppercase
`awk 'BEGIN{srand(); print int(rand()*10)}'` | Generate a random number

## Regular Expressions

COMMAND | DESCRIPTION
---|---
`awk '/[0-9]+/{print $0}' <file>` | Match lines containing one or more digits
`awk '/pattern1/ && /pattern2/{print $0}' <file>` | Match lines matching multiple patterns

