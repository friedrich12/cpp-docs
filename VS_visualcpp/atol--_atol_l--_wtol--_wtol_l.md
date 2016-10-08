---
title: "atol, _atol_l, _wtol, _wtol_l"
ms.custom: na
ms.date: 10/03/2016
ms.devlang: 
  - C++
  - C
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - atol
  - _wtol_l
  - _wtol
  - _atol_l
apilocation: 
  - msvcrt.dll
  - msvcr80.dll
  - msvcr90.dll
  - msvcr100.dll
  - msvcr100_clr0400.dll
  - msvcr110.dll
  - msvcr110_clr0400.dll
  - msvcr120.dll
  - msvcr120_clr0400.dll
  - ucrtbase.dll
  - api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
ms.assetid: cedfc21c-2d64-4e9c-bd04-bdf60b12db46
caps.latest.revision: 20
manager: ghogen
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - ru-ru
  - zh-cn
  - zh-tw
translation.priority.mt: 
  - cs-cz
  - pl-pl
  - pt-br
  - tr-tr
---
# atol, _atol_l, _wtol, _wtol_l
Convert a string to a long integer.  
  
## Syntax  
  
```  
long atol(  
   const char *str   
);  
long _atol_l(  
   const char *str,  
   _locale_t locale  
);  
long _wtol(  
   const wchar_t *str   
);  
long _wtol_l(  
   const wchar_t *str,  
   _locale_t locale  
);  
```  
  
#### Parameters  
 `str`  
 String to be converted.  
  
 `locale`  
 Locale to use.  
  
## Return Value  
 Each function returns the `long` value produced by interpreting the input characters as a number. The return value is 0L for `atol` if the input cannot be converted to a value of that type.  
  
 In the case of overflow with large positive integral values, `atol` returns `LONG_MAX`; in the case of overflow with large negative integral values, `LONG_MIN` is returned. In all out-of-range cases, `errno` is set to `ERANGE`. If the parameter passed in is `NULL`, the invalid parameter handler is invoked, as described in [Parameter Validation](../VS_visualcpp/Parameter-Validation.md). If execution is allowed to continue, these functions set `errno` to `EINVAL` and return 0.  
  
## Remarks  
 These functions convert a character string to a long integer value (`atol`).  
  
 The input string is a sequence of characters that can be interpreted as a numerical value of the specified type. The function stops reading the input string at the first character that it cannot recognize as part of a number. This character may be the `NULL` character ('\0' or L'\0') terminating the string.  
  
 The `str` argument to `atol` has the following form:  
  
 [`whitespace`] [`sign`] [`digits`]]  
  
 A `whitespace` consists of space or tab characters, which are ignored; `sign` is either plus (+) or minus (–); and `digits` are one or more digits.  
  
 `_wtol` is identical to `atol` except that it takes a wide character string.  
  
 The versions of these functions with the `_l` suffix are identical except that they use the locale parameter passed in instead of the current locale. For more information, see [Locale](../VS_visualcpp/Locale.md).  
  
### Generic-Text Routine Mappings  
  
|TCHAR.H routine|_UNICODE & _MBCS not defined|_MBCS defined|_UNICODE defined|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tstol`|`atol`|`atol`|`_wtol`|  
|`_ttol`|`atol`|`atol`|`_wtol`|  
  
## Requirements  
  
|Routines|Required header|  
|--------------|---------------------|  
|`atol`|<stdlib.h>|  
|`_atol_l`, `_wtol`, `_wtol_l`|<stdlib.h> and <wchar.h>|  
  
## Example  
 This program shows how numbers stored as strings can be converted to numeric values using the `atol` function.  
  
```  
// crt_atol.c  
// This program shows how numbers stored as  
// strings can be converted to numeric values  
// using the atol functions.  
#include <stdlib.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
    char    *str = NULL;  
    long    value = 0;  
  
    // An example of the atol function  
    // with leading and trailing white spaces.  
    str = "  -2309 ";  
    value = atol( str );  
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the atol function   
    // with an arbitrary decimal point.  
    str = "314127.64";  
    value = atol( str );  
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the atol function  
    // with an overflow condition occurring.  
    str = "3336402735171707160320";  
    value = atol( str );  
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );  
    if (errno == ERANGE)  
    {  
       printf("Overflow condition occurred.\n");  
    }  
}  
```  
  
 **Function: atol( "  -2309 " ) = -2309**  
**Function: atol( "314127.64" ) = 314127**  
**Function: atol( "3336402735171707160320" ) = 2147483647**  
**Overflow condition occurred.**   
## .NET Framework Equivalent  
  
-   [System::Convert::ToInt32](https://msdn.microsoft.com/en-us/library/system.convert.toint32.aspx)  
  
-   [System::Convert::ToUInt32](https://msdn.microsoft.com/en-us/library/system.convert.touint32.aspx)  
  
## See Also  
 [Data Conversion](../VS_visualcpp/Data-Conversion.md)   
 [Floating-Point Support](../VS_visualcpp/Floating-Point-Support.md)   
 [Locale](../VS_visualcpp/Locale.md)   
 [_ecvt](../VS_visualcpp/_ecvt.md)   
 [_fcvt](../VS_visualcpp/_fcvt.md)   
 [_gcvt](../VS_visualcpp/_gcvt.md)   
 [setlocale, _wsetlocale](../VS_visualcpp/setlocale--_wsetlocale.md)   
 [_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](../VS_visualcpp/_atodbl--_atodbl_l--_atoldbl--_atoldbl_l--_atoflt--_atoflt_l.md)