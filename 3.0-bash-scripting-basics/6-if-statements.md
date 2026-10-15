# 6 If Statements

## Comparing numbers
[[ $A -eq $B ]]  # Equal to ($A == $B)
[[ $A -ne $B ]]  # Not equal to ($A != $B)
[[ $A -gt $B ]]  # Greater than ($A > $B)
[[ $A -lt $B ]]  # Less than ($A < $B)
[[ $A -ge $B ]]  # Greater than or equal to ($A >= $B)
[[ $A -le $B ]]  # Less than or equal to ($A <= $B)

## Comparing strings
[[ "$NAME" == "Alex" ]]  # Strings are identical
[[ "$NAME" != "Alex" ]]  # Strings are NOT identical
[[ -z "$NAME" ]]         # String is empty
[[ -n "$NAME" ]]         # String is not empty



## if statement
The if statement checks if a specific condition is true. If the condition evaluates to true, the code block between then and fi (which is "if" spelled backwards) executes.

Example:
```bash
if [[ $A -gt 10 ]]; then
    echo "A is greater than 10"
fi
```



## elif
The elif (short for "else if") statement allows you to check multiple alternative conditions sequentially if the initial if condition evaluates to false. You can chain as many elif blocks as you want.

Example:
```bash
if [[ $A -gt 10 ]]; then
    echo "A is greater than 10"
elif [[ $A -eq 10 ]]; then
    echo "A is exactly 10"
fi
```



## else
The else statement serves as a catch all fallback. If all preceding if and elif conditions evaluate to false, the code inside the else block runs automatically without needing its own condition.

Example:
```bash
if [[ $A -gt 10 ]]; then
    echo "A is greater than 10"
elif [[ $A -eq 10 ]]; then
    echo "A is exactly 10"
else
    echo "A is less than 10"
fi
```

Complete Example:
```bash
#!/bin/bash

SCORE=85

if [[ $SCORE -ge 90 ]]; then
    echo "Grade: A"
elif [[ $SCORE -ge 80 ]]; then
    echo "Grade: B"
elif [[ $SCORE -ge 70 ]]; then
    echo "Grade: C"
else
    echo "Grade: F"
fi
```