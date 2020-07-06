# Dictionary Vs Hashtable

### Dictionary 
1. Dictionary is a generic collection. We must specify date type of key and value.
2. Dictionary stores key/value pairs of same type.
3. Performance is better than Hashtable due to no boxing/unboxing.
4. Dictionary will give error when you try to access a key that doesn't present in the Dictionary.
5. Dictionary maintains the order of stored values.
```C#
public class Dictionary<TKey, TValue> 
```

### Hashtable
1. Hashtable is a non-generic collection. We don't specify data type of key and value.
2. Hashtable stores key/value pairs of same or different type.
2. Performance is worse than Dictionary due to boxing/unboxing.
3. Hashtable will give null value when you try to access a key that doesn't present in the Hashtable.
4. Hashtable doesn't maintain the order of stored values.
```C#
public class Hashtable
```

### Dictionary properties
1. **Count**: Get the number of key/value pairs contained in the Dictionary.
2. **Item[]**: Get or set the value associated with the specified key.
3. **Keys**: Get a collection containing all the keys in the Dictionary.
4. **Values**: Get a collection containning all the values in the Dictionary.
5. **Comparer**

```C#
using System;
using System.Collections.Generic;
public class Solution
{
    static void Main(string[] args)
    {
        Dictionary<int, string> dic = new Dictionary<int, string>();
        dic.Add(1, "one");
        dic.Add(2, "two");
        dic.Add(3, "three");
        Console.WriteLine(dic.Count); // 3
        Console.WriteLine(dic[1]);    // One
        Console.WriteLine(dic.Keys.Count);   // 3
        Console.WriteLine(dic.Values.Count); // 3
    }
}
```
### Dictionary Methods
1. **Add**: Add the specified key/value to the Dictionary.<br/>
   If Count is less than capacity, this method is O(1) operation. If the capacity must be increased to accommodate the new element, this mehtod becomes a O(n) operation, where n is Count.
2. **Clear**: Remove all the key/value pairs from the Dictionary.<br/>
   It is a O(n) method
3. **ContainsKey**: Determine whether the Dictionary contains a specfied key. <br/>
   It is a O(1) operation.
4. **ContainsValue**: Determine whether the Dictionary contains a specfied value. <br/>
   It is a O(n) operation.
5. **Remove**: Remove the value with the specified key from the Dictionary. <br/>
   It is a O(1) operation.

### Reference
1. https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic?view=dotnet-plat-ext-3.1
2. https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/types/boxing-and-unboxing
3. https://www.geeksforgeeks.org/difference-between-hashtable-and-dictionary-in-c-sharp/
