# Explicit and Implicit Type Casting

In strongly-typed programming languages like C# and Java, when a variable is declared it cannot be assigned a value of another type unless that type is implicitly convertible to the given data type. Type conversion is also called casting or type casting. 

<br/>

## Magnitude and Precision

![image](https://github.com/idanhuang/idanhuang.github.io/blob/master/image/Single-precision-and-double-precision-numbers.png)
- Magnitude <br/>
Magnitude denotes the range of a given data type. Magnitude of a given data type has no direct relevance to the number of bits it holds. For example, 'Long' has 64 bits which can represent range from -2^63 to 2^63-1. 'Float' type numbers are represented using IEEE 754 single floating point notation, even though float data type only has 32 bits, it has a valid range about from -3.4 * 10^38 to 3.4 * 10^38, which is larger range. Actually magnitude is determined by the exponent digits. 

- Precision <br/>
Precision in numbers in the total number of significant digits (有效数字). For example, Float is a single-precision data type. Its fraction part has 23 digits, which can represent minimal value 0.00000011920928955078125 (1.19 * 10 ^ -7) in decimal. Float has 7 significant digits, hence its precision is 7 digits. For another example, Double is a double-precision data type. Its fraction part has 52 digits, which can represent minimal value 2.2204460492503130808472633361816e-16 (2.22 * 10 ^ -16) in decimal. Double has 16 significant digits, hence its precision is 16 digits.Data types like int and long, they don't have fractional digits, thus their precision is 0 digit, hence they will be implicitly casted to float and long.

<br/>

## Implicit conversion

Implict type conversion (a.k.a widening type conversion) means conversion of data types without losing precision. Strict rules will be applied when implicit conversion happens. Specifically, if operands have two different data types, then operand having data type with lower precision (fewer bits) will be automatically converted to a data type with higher precision.

```C#
  int i1 = 1.2f; // compile error: Cannot implicitly convert type 'float' to 'int', since float has higher precision. 
  int i2 = 1.2;  // compile error: Cannot implicitly convert type 'double' to 'int', since long has higher precision.
  float f = 1;   // complie ok. integer 1 is implicitly converted to float, since int data type has lower precision.
```

![image](https://github.com/idanhuang/idanhuang.github.io/blob/master/image/Single-precision-and-double-precision-numbers.png)


<br/>

## References:
1. https://www.pluralsight.com/guides/explicit-implicity-type-casting-the-difference
2. https://www.reddit.com/r/javahelp/comments/4y7fsp/what_is_magnitude_precision_in_respect_to_type/
3. https://www.zhihu.com/question/26022206
4. https://en.wikipedia.org/wiki/Significant_figures
