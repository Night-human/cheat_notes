# SED (Stream Editor)

Command in unix that can perform functions like searching, finding, replacing, insertion or deletion on files.

## Syntax

> sed OPTIONS... [SCRIPT] [INPUT FILE]

### Substitution

File: text.txt  
Content: The sun is brightness, the sun is life.

> sed 's/sun/moon/' text.txt

**output:** The moon is brightness, the sun is life.

Definitions:

**s:** specifies the substitution  
**sun:** is the search pattern  
**moon:** is the replacement string  
**/:** is the delimiter  

The above command only replaces the first match. You can choose which word you want to replace by placing a number at the end of the delimiter. **g** for replace all occurrences. number and **g** can be mixed.

Replacing starting from a line number:

> sed '3 s/sun/moon/' text.txt

To replace on a range of lines: **1,3**. **$** to the last line.

### Duplication

> sed -n 's/sun/moon/p' text.txt

**p:** duplicates the replaced line on the file.
**-n:** prints the replaced line instead

### Deleting a line

> sed 'nd' text.txt

**n:** is the number of line to delete. **n,nd** for ranges.

### Delete a pattern line

> sed '/sun/d' text.txt
