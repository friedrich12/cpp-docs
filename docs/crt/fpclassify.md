---
title: "fpclassify"
ms.custom: na
ms.date: "10/14/2016"
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: "article"
apiname: 
  - "fpclassify"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "HeaderDef"
f1_keywords: 
  - "fpclassify"
  - "math/fpclassify"
helpviewer_keywords: 
  - "fpclassify macro"
  - "fpclassify function"
ms.assetid: bf549499-7ff9-4a58-8692-f2d1cb6bab81
caps.latest.revision: 3
ms.author: "corob"
manager: "ghogen"
translation.priority.mt: 
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "ru-ru"
  - "zh-cn"
  - "zh-tw"
---
# fpclassify
Returns the floating-point classification of the argument.  
  
## Syntax  
  
```  
int fpclassify(   
   /* floating-point */ x   
);  
  
int fpclassify(   
   float x   
); // C++ only  
  
int fpclassify(   
   double x   
); // C++ only  
  
int fpclassify(   
   long double x   
); // C++ only  
  
```  
  
#### Parameters  
 `x`  
 The floating-point value to test.  
  
## Return Value  
 `fpclassify` returns an integer value that indicates the floating-point class of the argument `x`. This table shows the possible values returned by `fpclassify`, defined in \<math.h>.  
  
|Value|Description|  
|-----------|-----------------|  
|`FP_NAN`|A quiet, signaling, or indeterminate NaN|  
|`FP_INFINITE`|A positive or negative infinity|  
|`FP_NORMAL`|A positive or negative normalized non-zero value|  
|`FP_SUBNORMAL`|A positive or negative denormalized value|  
|`FP_ZERO`|A positive or negative zero value|  
  
## Remarks  
 In C, `fpclassify` is a macro; in C++, `fpclassify` is a function overloaded using argument types of `float`, `double`, or `long double`. In either case, the value returned depends on the effective type of the argument expression, and not on any intermediate representation. For example, a normal `double` or `long double` value can become an infinity, denormal, or zero value when converted to a `float`.  
  
## Requirements  
  
|Function/Macro|Required header (C)|Required header (C++)|  
|---------------------|---------------------------|-------------------------------|  
|`fpclassify`|\<math.h>|\<math.h> or \<cmath>|  
  
 The `fpclassify` macro and `fpclassify` functions conform to the C99 and C++11 specifications. For more compatibility information, see [Compatibility](../crt/compatibility.md).  
  
## See Also  
 [Floating-Point Support](../crt/floating-point-support.md)   
 [isnan, _isnan, _isnanf](../crt/isnan--_isnan--_isnanf.md)