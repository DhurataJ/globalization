---
title: Number formatting in .NET Framework
description: The *NumberFormatInfo* class defines how currency, decimal separators, and other numeric symbols are formatted and displayed based on culture.
ms.assetid: 81bc7141-92f0-432a-a241-eebfda454fd2
ms.date: 03/16/2016
---

# Number Formatting in .NET Framework

The *NumberFormatInfo* class defines how currency, decimal separators, and other numeric symbols are formatted and displayed based on culture.
For example, the decimal number 10000.50 is formatted as 10,000.50 for the culture "en-US" and 10.000,50 for the culture "de-DE."
An instance of *NumberFormatInfo* can be created for a specific culture or the invariant culture, but not for a neutral culture.
A neutral culture does not provide enough information to display the correct numeric format.
Table 4-10 lists the standard format characters for each standard formatting pattern and the associated *NumberFormatInfo* property that can be set to modify this pattern.

| Format character | Description | Associated properties (if any) |
| --- | --- | -- |
| c, C | Currency format. | CurrencyNegativePattern, CurrencyPositivePattern, CurrencySymbol, CurrencyGroupSizes, CurrencyGroupSeperator, CurrencyDecimalDigits, CurrencyDecimalSeperator |
| d, D | Decimal format | - |
| e, E | Scientific (exponential) format | - |
| f, F | Fixed point format | - |
| g, G | General format | - |
| n, N | Number format | NumberNegativePattern, NumberGroupSizes, NumberGroupSeperator, NumberDecimalDigits, NumberDecimalSeperator |
| r, R | Roundtrip format, which ensures that numbers converted to strings will have the same value when they are converted back to numbers. | - |
| x, X | Hexadecimal format | - |

**Table 1:** Standard format characters for basic formatting patterns and the associated NumberFormatInfo property used to modify these patterns.

The following code example displays an integer using the NumberFormatInfo standard currency format ("c") for the specified CurrentCulture.

```csharp
using System.Globalization;

public class CurrencyFormatSample
{
  public static void Main()
  {
    int i = 100;

    // Create a CultureInfo object for English in Belize.
    CultureInfo bz = new CultureInfo("en-BZ");
    // Display i formatted as currency for bz.
    Console.WriteLine(i.ToString("c", bz));

    // Create a CultureInfo object for English in the U.S.
    CultureInfo us = new CultureInfo("en-US");
    // Display i formatted as currency for us.
    Console.WriteLine(i.ToString("c", us));

    // Create a CultureInfo object for Danish in Denmark.
    CultureInfo dk = new CultureInfo("da-DK");
    // Display i formatted as currency for dk.
    Console.WriteLine(i.ToString("c", dk));
  }
}
```

This code produces the following output:

```console
$100.00
$100.00
100,00 kr.
```

As when dealing with numbers, formatting conventions for addresses vary widely from one country to another.
There are also discrepancies in the actual terms used when representing addresses that you will need to handle.
