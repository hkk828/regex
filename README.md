# Regular Expression (Regex)

### Cheat Sheet for regex symbols
```
.       - Any Character Except New Line  
\d      - Digit (0-9)  
\D      - Not a Digit (0-9)  
\w      - Word Character (a-z, A-Z, 0-9, _)  
\W      - Not a Word Character  
\s      - Whitespace (space, tab, newline)  
\S      - Not Whitespace (space, tab, newline)  

\b      - Word Boundary (blank in front of the word)   
\B      - Not a Word Boundary (starts in the middle of words)  
^       - Beginning of a String  
$       - End of a String  

[]      - Matches Characters in brackets  
[^ ]    - Matches Characters NOT in brackets  
|       - Either Or  
( )     - Group  

Quantifiers:  
*       - 0 or More  
+       - 1 or More  
?       - 0 or One  
{3}     - Exact Number  
{3,4}   - Range of Numbers (Minimum, Maximum)  


#### Sample Regexs ####
Email address-like pattern
[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+
```

### regex in Python
Regular expression can be handled with ```re``` module

```python
import re
pattern = re.compile(r'\d{3}-\d{3}-\d{4}')  # finds an expression like 011-3210-5043

pattern.finditer(sentence_to_find_pattern)  # returns an iterator of matched expressions (with position and expression)
pattern.findall(sentence_to_find_pattern)   # returns a list of matched expression (if there is a group, then it returns a group list and if there are more than two groups, it returns a tupled group list)
pattern.sub(sub_expr, sentence_to_be_substituted)  # substitues "sentence_to_be_substituted" with "sub_expr" (using pattern)
```


```python
import re

sentence_to_find_pattern='''
Phone Numbers
321-555-4321
123.555.1234
123*555*1234
800-555-1234
900-555-1234
End
'''

pattern = re.compile(r'\d{3}-\d{3}-\d{4}')
matches = pattern.finditer(sentence_to_find_pattern)

for match in matches:
  print(match)
```

```
Results
<re.Match object; span=(15, 27), match='321-555-4321'>
<re.Match object; span=(54, 66), match='800-555-1234'>
<re.Match object; span=(67, 79), match='900-555-1234'>
```


Reference: [Corey Schafer](https://www.youtube.com/watch?v=K8L6KVGG-7o&t=617s&ab_channel=CoreySchafer)

