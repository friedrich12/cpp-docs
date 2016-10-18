---
title: "_get_dstbias"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "article"
apiname: 
  - "_get_dstbias"
  - "__dstbias"
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
  - "api-ms-win-crt-time-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__dstbias"
  - "_get_dstbias"
  - "get_dstbias"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "__dstbias"
  - "daylight saving time offset"
  - "get_dstbias function"
  - "_get_dstbias function"
ms.assetid: e751358c-1ecc-411b-ae2c-81b2ec54ea45
caps.latest.revision: 18
ms.author: "corob"
manager: "ghogen"
translation.priority.ht: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# _get_dstbias
Retrieves the daylight saving time offset in seconds.  
  
## Syntax  
  
```  
  
      error_t _get_dstbias(   
    int* seconds  
);  
```  
  
#### Parameters  
 `seconds`  
 The offset in seconds of daylight saving time.  
  
## Return Value  
 Zero if successful or an `errno` value if an error occurs.  
  
## Remarks  
 The `_get_dstbias` function retrieves the number of seconds in daylight saving time as an integer. If daylight saving time is in effect, the default offset is 3600 seconds, which is the number of seconds in one hour (though a few regions do observe a two-hour offset).  
  
 If `seconds` is `NULL`, the invalid parameter handler is invoked as described in [Parameter Validation](../crt/parameter-validation.md). If execution is allowed to continue, this function sets `errno` to `EINVAL` and returns `EINVAL`.  
  
 We recommend you use this function instead of the macro `_dstbias` or the deprecated function `__dstbias`.  
  
## .NET Framework Equivalent  
 Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Requirements  
  
|Routine|Required header|  
|-------------|---------------------|  
|`_get_dstbias`|\<time.h>|  
  
 For more information, see [Compatibility](../crt/compatibility.md).  
  
## See Also  
 [Time Management](../crt/time-management.md)   
 [errno, _doserrno, _sys_errlist, and _sys_nerr](../crt/errno--_doserrno--_sys_errlist--and-_sys_nerr.md)   
 [_get_daylight](../crt/_get_daylight.md)   
 [_get_timezone](../crt/_get_timezone.md)   
 [_get_tzname](../crt/_get_tzname.md)