# 2.0 - Common Programming Operators

## Contents

- [`Arithmetic`](#arithmetic)
  - [`Addition`](#addition)
  - [`Subtraction`](#subtraction)
  - [`Multiplication`](#multiplication)
  - [`Division`](#division)
  - [`Remainder (Modulus)`](#remainder-modulus)
  - [`Exponentiation`](#exponentiation)
  - [`Increment and Decrement`](#increment-and-decrement)
  - [`Unary Operators`](#unary-operators)
  - [`Bitwise Operators`](#bitwise-operators)
  - [`Bit Shifts`](#bit-shifts)
  - [`Comma Operator`](#comma-operator)
- [`Comparison`](#comparison)
  - [`Equal to`](#equal-to)
  - [`Not equal to`](#not-equal-to)
  - [`Less than`](#less-than)
  - [`Greater than`](#greater-than)
  - [`Less than or equal to`](#less-than-or-equal-to)
  - [`Greater than or equal to`](#greater-than-or-equal-to)
- [`Logical`](#logical)
  - [`AND`](#and)
  - [`OR`](#or)
  - [`NOT`](#not)
- [`Assignment`](#assignment)
  - [`Basic assignment`](#basic-assignment)
  - [`Compound assignment`](#compound-assignment)

---

## Arithmetic

### Addition
- Meaning: Adding two or more numeric values together to find their combined total.
- Role in execution: Used in arithmetic contexts like `$(( ... ))` to perform addition calculations on numbers or variables.

- Example:
```bash
sum=$(( 5 + 3 ))
echo "$sum"
# Output: 8
```

Alternatively you can do this: 

```bash
(( sum = 5 + 3 ))
echo "$sum"
# Output: 8
```


### Subtraction
- Meaning: Subtracting one numeric value from another to find the difference.
- Role in execution: Used in arithmetic contexts like `$(( ... ))` to perform subtraction calculations on numbers or variables.

- Example:
```bash
difference=$(( 10 - 4 ))
echo "$difference"
# Output: 6
```

Alternatively you can do this: 

```bash
(( difference = 10 - 4 ))
echo "$difference"
# Output: 6
```


### Multiplication
- Meaning: Multiplying two or more numeric values together to find their product.
- Role in execution: Used in arithmetic contexts like `$(( ... ))` to perform multiplication calculations on numbers or variables.

- Example:
```bash
product=$(( 4 * 5 ))
echo "$product"
# Output: 20
```

Alternatively you can do this: 

```bash
(( product = 4 * 5 ))
echo "$product"
# Output: 20
```


### Division
- Meaning: Dividing one numeric value by another to find the quotient (note that Bash discards remainders and only keeps whole numbers).
- Role in execution: Used in arithmetic contexts like `$(( ... ))` to perform division calculations on numbers or variables.

- Example:
```bash
quotient=$(( 10 / 3 ))
echo "$quotient"
# Output: 3
```

Alternatively you can do this: 

```bash
(( quotient = 10 / 3 ))
echo "$quotient"
# Output: 3
```

### Remainder (Modulus)
- Meaning: Dividing two numbers and returning only the remainder instead of the quotient using the `%` operator.
- Role in execution: Used in arithmetic contexts like `$(( ... ))` to calculate remainders, which is handy for things like checking if a number is even or odd.

- Example:
```bash
remainder=$(( 10 % 3 ))
echo "$remainder"
# Output: 1
```

Alternatively you can do this: 

```bash
(( remainder = 10 % 3 ))
echo "$remainder"
# Output: 1
```

### Exponentiation
- Meaning: Raising a number to the power of another number using the `**` operator.
- Role in execution: Used in arithmetic contexts like `$(( ... ))` to calculate exponents (such as squaring or cubing numbers).

- Example:
```bash
result=$(( 2 ** 3 ))
echo "$result"
# Output: 8
```

Alternatively you can do this: 

```bash
(( result = 2 ** 3 ))
echo "$result"
# Output: 8
```

### Increment and Decrement
- Meaning: Increasing (`++`) or decreasing (`--`) a variable's value by exactly 1.
- Role in execution: Used in arithmetic contexts like `(( ... ))` to quickly count up or down, which is heavily used in loops and tracking counters.

- Example:
```bash
count=5
(( count++ ))
echo "$count"
# Output: 6
```

Alternatively you can do this:

```bash
count=5
(( ++count ))
echo "$count"
# Output: 6
```

Decrement Example:
```bash
count=5
(( count-- ))
echo "$count"
# Output: 4
```

Alternatively you can do this:

```bash
count=5
(( --count ))
echo "$count"
# Output: 4
```

### Unary Operators
- Meaning: Operators that act on a single operand to change its sign or state (such as unary minus `-` to make a number negative, or unary plus `+`).
- Role in execution: Used in arithmetic contexts like `$(( ... ))` to negate values or explicitly set signs.

- Example:
```bash
num=5
result=$(( -num ))
echo "$result"
# Output: -5
```

Alternatively you can do this:

```bash
num=5
(( result = -num ))
echo "$result"
# Output: -5
```

### Bitwise Operators
- Meaning: Operators that perform operations on the individual binary bits of integer values (such as bitwise AND `&`, bitwise OR `|`, XOR `^`, and bitwise NOT `~`).
- Role in execution: Used in arithmetic contexts like `$(( ... ))` to manipulate flags, masks, or low-level binary data.

- Example:
```bash
# Binary: 5 is 101, 3 is 011. Bitwise AND (101 & 011) results in 001 (1)
result=$(( 5 & 3 ))
echo "$result"
# Output: 1
```

Alternatively you can do this:

```bash
(( result = 5 & 3 ))
echo "$result"
# Output: 1
```

### Bit Shifts
- Meaning: Shifting the binary bits of a number to the left (`<<`) or right (`>>`) by a specified number of positions, effectively multiplying or dividing the number by powers of 2.
- Role in execution: Used in arithmetic contexts like `$(( ... ))` for low-level bit manipulation, performance tuning, or working with binary flags.

- Example:
```bash
# 5 in binary is 101. Shifting left by 1 gives 1010, which is 10.
result=$(( 5 << 1 ))
echo "$result"
# Output: 10
```

Alternatively you can do this:

```bash
(( result = 5 << 1 ))
echo "$result"
# Output: 10
```

### Comma Operator
- Meaning: Allows multiple expressions to be evaluated sequentially from left to right, returning the value of the final expression as the overall result.
- Role in execution: Used in arithmetic contexts like `$(( ... ))` to group multiple related calculations or assignments into a single statement.

- Example:
```bash
result=$(( a = 2, b = 3, a + b ))
echo "$result"
# Output: 5
```

Alternatively you can do this:

```bash
(( a = 2, b = 3, result = a + b ))
echo "$result"
# Output: 5
```

---

## Comparison

### Equal to
- Meaning: Checking if two numeric values are equal to each other using the `==` operator.
- Role in execution: Used in conditional or arithmetic contexts like `(( ... ))` to compare numbers and control program flow.

- Example:
```bash
if (( 5 == 5 )); then
    echo "They are equal"
fi
# Output: They are equal
```

### Not equal to
- Meaning: Checking if two numeric values are not equal to each other using the `!=` operator.
- Role in execution: Used in conditional or arithmetic contexts like `(( ... ))` to compare numbers and control program flow.

- Example:
```bash
if (( 5 != 3 )); then
    echo "They are not equal"
fi
# Output: They are not equal
```

### Less than
- Meaning: Checking if one numeric value is strictly less than another using the `<` operator.
- Role in execution: Used in conditional or arithmetic contexts like `(( ... ))` to compare numbers and control program flow.

- Example:
```bash
if (( 3 < 5 )); then
    echo "3 is less than 5"
fi
# Output: 3 is less than 5
```

### Greater than
- Meaning: Checking if one numeric value is strictly greater than another using the `>` operator.
- Role in execution: Used in conditional or arithmetic contexts like `(( ... ))` to compare numbers and control program flow.

- Example:
```bash
if (( 5 > 3 )); then
    echo "5 is greater than 3"
fi
# Output: 5 is greater than 3
```

### Less than or equal to
- Meaning: Checking if one numeric value is less than or equal to another using the `<=` operator.
- Role in execution: Used in conditional or arithmetic contexts like `(( ... ))` to compare numbers and control program flow.

- Example:
```bash
if (( 3 <= 5 )); then
    echo "3 is less than or equal to 5"
fi
# Output: 3 is less than or equal to 5
```

### Greater than or equal to
- Meaning: Checking if one numeric value is greater than or equal to another using the `>=` operator.
- Role in execution: Used in conditional or arithmetic contexts like `(( ... ))` to compare numbers and control program flow.

- Example:
```bash
if (( 5 >= 3 )); then
    echo "5 is greater than or equal to 3"
fi
# Output: 5 is greater than or equal to 3
```

---

## Logical

### AND
- Meaning: Logical AND operator using `&&` to evaluate multiple conditions, returning true only if all individual conditions are true.
- Role in execution: Used in conditional or arithmetic contexts like `(( ... ))` to combine expressions and control program flow.

- Example:
```bash
if (( 5 > 3 && 10 > 8 )); then
    echo "Both conditions are true"
fi
# Output: Both conditions are true
```

### OR
- Meaning: Logical OR operator using `||` to evaluate multiple conditions, returning true if at least one individual condition is true.
- Role in execution: Used in conditional or arithmetic contexts like `(( ... ))` to combine expressions and control program flow.

- Example:
```bash
if (( 5 > 3 || 10 < 2 )); then
    echo "At least one condition is true"
fi
# Output: At least one condition is true
```

### NOT
- Meaning: Logical NOT operator using `!` to invert the truth value of a condition (turning true to false and false to true).
- Role in execution: Used in conditional or arithmetic contexts like `(( ... ))` to negate expressions and control program flow.

- Example:
```bash
if (( ! (5 < 3) )); then
    echo "The condition is false, so NOT makes it true"
fi
# Output: The condition is false, so NOT makes it true
```

---

## Assignment

### Basic assignment
- Meaning: Assigning a value to a variable using the `=` operator within an arithmetic context.
- Role in execution: Used in arithmetic contexts like `(( ... ))` to store numbers or the results of calculations into variables.

- Example:
```bash
(( x = 10 ))
echo "$x"
# Output: 10
```

### Compound assignment
- Meaning: Modifying an existing variable's value by performing an arithmetic operation and assigning the result back in a single step (using operators like `+=`, `-=`, `*=`, `/=`, and `%=`).
- Role in execution: Used in arithmetic contexts like `(( ... ))` to efficiently update variable values (such as adding to a counter or scaling a number).

- Example:
```bash
x=10
(( x += 5 ))
echo "$x"
# Output: 15
```