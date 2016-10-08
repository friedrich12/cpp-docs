---
title: "Overview of Marshaling in C++"
ms.custom: na
ms.date: 10/03/2016
ms.devlang: 
  - C++
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: 997dd4bc-5f98-408f-b890-f35de9ce3bb8
caps.latest.revision: 16
manager: ghogen
translation.priority.ht: 
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
# Overview of Marshaling in C++
In mixed mode, you sometimes must marshal your data between native and managed types. Visual Studio 2008 introduced the marshaling library to help you marshal and convert data in a simple way.  
  
 You can use the marshaling library with or without a [marshal_context Class](../VS_visualcpp/marshal_context-Class.md). Some conversions require a context. Other conversions can be implemented using the [marshal_as](../VS_visualcpp/marshal_as.md) function. The following table lists the current conversions supported, whether they require a context, and what marshal file you have to include:  
  
|From type|To type|Marshal method|Include file|  
|---------------|-------------|--------------------|------------------|  
|System::String^|const char *|marshal_context|marshal.h|  
|const char *|System::String^|marshal_as|marshal.h|  
|char *|System::String^|marshal_as|marshal.h|  
|System::String^|const wchar_t*|marshal_context|marshal.h|  
|const wchar_t *|System::String^|marshal_as|marshal.h|  
|wchar_t *|System::String^|marshal_as|marshal.h|  
|System::IntPtr|HANDLE|marshal_as|marshal_windows.h|  
|HANDLE|System::IntPtr|marshal_as|marshal_windows.h|  
|System::String^|BSTR|marshal_context|marshal_windows.h|  
|BSTR|System::String^|marshal_as|marshal.h|  
|System::String^|bstr_t|marshal_as|marshal_windows.h|  
|bstr_t|System::String^|marshal_as|marshal_windows.h|  
|System::String^|std::string|marshal_as|marshal_cppstd.h|  
|std::string|System::String^|marshal_as|marshal_cppstd.h|  
|System::String^|std::wstring|marshal_as|marshal_cppstd.h|  
|std::wstring|System::String^|marshal_as|marshal_cppstd.h|  
|System::String^|CStringT<char\>|marshal_as|marshal_atl.h|  
|CStringT<char\>|System::String^|marshal_as|marshal_atl.h|  
|System::String^|CStringT<wchar_t>|marshal_as|marshal_atl.h|  
|CStringT<wchar_t>|System::String^|marshal_as|marshal_atl.h|  
|System::String^|CComBSTR|marshal_as|marshal_atl.h|  
|CComBSTR|System::String^|marshal_as|marshal_atl.h|  
  
 Marshaling requires a context only when you marshal from managed to native data types and the native type you are converting to does not have a destructor for automatic clean up. The marshaling context destroys the allocated native data type in its destructor. Therefore, conversions that require a context will be valid only until the context is deleted. To save any marshaled values, you must copy the values to your own variables.  
  
> [!NOTE]
>  If you have embedded `NULL`s in your string, the result of marshaling the string is not guaranteed. The embedded `NULL`s can cause the string to be truncated or they might be preserved.  
  
 The marshaling library headers are located in the include directory in the msclr subdirectory. This example shows how to include the msclr directory in an include header declaration:  
  
 `#include "msclr\marshal_cppstd.h"`  
  
 The marshaling library is extensible so that you can add your own marshaling types. For more information about extending the marshaling library, see [How to: Extend the Marshaling Library](../VS_visualcpp/How-to--Extend-the-Marshaling-Library.md).  
  
 In earlier versions, you could marshal data by using [Platform Invoke](../Topic/Consuming%20Unmanaged%20DLL%20Functions.md). For more information about `PInvoke`, see [Calling Native Functions from Managed Code](../VS_visualcpp/Calling-Native-Functions-from-Managed-Code.md).  
  
## See Also  
 [C++ Support Library](../VS_visualcpp/C---Support-Library.md)   
 [How to: Extend the Marshaling Library](../VS_visualcpp/How-to--Extend-the-Marshaling-Library.md)