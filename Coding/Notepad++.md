
|   |   |   |
|---|---|---|
|**RegEx**|**Effect**|**Example**|
|**a**|Find character ‘a’||
|**abc**|Find string **abc**||
|**[…]**|Find any of ‘…’|**[abc]** finds characters ‘a’, ‘b’, or ‘c’|
|**[a-z]**|Find any in the range from ‘a’ to ‘z’|**[a-f]** finds any of the lowercase letters ‘a’ to ‘f’|
|**[^x]**|Find anything that is not ‘x’|**[^aeiou]** Finds all characters that are not vowels, including punctuation, digits and whitespace|
|**?**|The previous element is optional, it does not have to occur|[1-9][0-9]? Finds numbers from **1** to **9** and **10** to **99**|
|**.**|Find any character except **newline**, **linefeed**, **carriage return**||
|**+**|Find the previous element 1 to many times|**r+** finds ‘r’, **rr**, **rrr**, **rrrr**, etc.|
|*****|Find the previous element 0 to many times|**[a-zA-Z]*ed** finds strings ending in **ed**|
|**{x,y}**|Repeat the previous element x to y times|**[0-9]{5,7}** Finds any sequence of 5 to 7 digits.|
|**(…)**|Save anything inside the parentheses for use in replacement|**(store this)** finds and stores the string **store this**|
|**\1 \2 \3**|Restore the string saved by the parentheses, for use in replacement|**\1ing** adds **ing** to the saved string|
|**\w**|Shortcut for word characters (letters, digits and underscores)|**\w*** finds **cat**, **dog**, **login_name**, **cutie17**, etc.|
|**\d**|Shortcut for digits, same as **[1-9]**||
|**\b**|Marks the beginning or end of a word||
|**\**|Escape the operator following ‘\’|**\[\w*\]** finds a word in brackets|