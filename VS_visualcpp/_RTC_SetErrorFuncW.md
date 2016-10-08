---
title: "_RTC_SetErrorFuncW"
ms.custom: na
ms.date: 10/06/2016
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
  - _RTC_SetErrorFuncW
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
apitype: DLLExport
ms.assetid: b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a
caps.latest.revision: 15
manager: ghogen
translation.priority.mt: 
  - cs-cz
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pl-pl
  - pt-br
  - ru-ru
  - tr-tr
  - zh-cn
  - zh-tw
---
# _RTC_SetErrorFuncW
Designates a function as the handler for the reporting of run-time error checks (RTCs).  
  
## Syntax  
  
```  
  
      _RTC_error_fnW _RTC_SetErrorFuncW(  
   _RTC_error_fnW function   
);  
```  
  
#### Parameters  
 `function`  
 The address of the function that will handle run-time error checks.  
  
## Return Value  
 The previously defined error function; or `NULL` if there is no previously defined function.  
  
## Remarks  
 In new code, use only `_RTC_SetErrorFuncW`. `_RTC_SetErrorFunc` is only included in the library for backward compatibility.  
  
 The `_RTC_SetErrorFuncW` callback applies only to the component that it was linked in, but not globally.  
  
 Make sure that the address that you pass to `_RTC_SetErrorFuncW` is that of a valid error handling function.  
  
 If an error has been assigned a type of –1 by using [_RTC_SetErrorType](../VS_visualcpp/_RTC_SetErrorType.md), the error handling function is not called.  
  
 Before you can call this function, you must first call one of the run-time error-check initialization functions. For more information, see [Using Run-Time Checks Without the C Run-Time Library](../Topic/Using%20Run-Time%20Checks%20Without%20the%20C%20Run-Time%20Library.md).  
  
 **_RTC_error_fnW** is defined as follows:  
  
 **typedef int (__cdecl \*_RTC_error_fnW)(int**  `errorType` **, const wchar_t \*** *filename* **, int**  *linenumber* **, const wchar_t \*** `moduleName` **, const wchar_t \*** *format* **, ...);**  
  
 where:  
  
 `errorType`  
 The type of error that's specified by [_RTC_SetErrorType](../VS_visualcpp/_RTC_SetErrorType.md).  
  
 *filename*  
 The source file where the failure occurred, or null if no debug information is available.  
  
 *linenumber*  
 The line in *filename* where the failure occurred, or 0 if no debug information is available.  
  
 `moduleName`  
 The DLL or executable name where the failure occurred.  
  
 *format*  
 printf style string to display an error message, using the remaining parameters. The first argument of the VA_ARGLIST is the RTC Error number that occurred.  
  
 For an example that shows how to use **_RTC_error_fnW**, see [Native Run-Time Checks Customization](../Topic/Native%20Run-Time%20Checks%20Customization.md).  
  
## Requirements  
  
|Routine|Required header|  
|-------------|---------------------|  
|`_RTC_SetErrorFuncW`|<rtcapi.h>|  
  
 For more information, see [Compatibility](../VS_visualcpp/Compatibility.md).  
  
## Libraries  
 All versions of the [C run-time libraries](../VS_visualcpp/CRT-Library-Features.md).  
  
## .NET Framework Equivalent  
 Not applicable. To call the standard C function, use `PInvoke`. For more information, see [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## See Also  
 [_CrtDbgReport, _CrtDbgReportW](../VS_visualcpp/_CrtDbgReport--_CrtDbgReportW.md)   
 [Run-Time Error Checking](../VS_visualcpp/Run-Time-Error-Checking.md)