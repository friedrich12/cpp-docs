---
title: "runtime_exception Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp/Concurrency::direct3d_abort"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "runtime_exception class"
ms.assetid: 8fe3ce2c-3d4c-4b9c-95e8-e592f37adefd
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
translation.priority.ht: 
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "ru-ru"
  - "zh-cn"
  - "zh-tw"
translation.priority.mt: 
  - "cs-cz"
  - "pl-pl"
  - "pt-br"
  - "tr-tr"
---
# runtime_exception Class
The base type for exceptions in the C++ Accelerated Massive Parallelism (AMP) library.  
  
## Syntax  
  
```  
class runtime_exception : public std::exception;  
```  
  
## Members  
  
### Public Constructors  
  
|Name|Description|  
|----------|-----------------|  
|[runtime_exception::runtime_exception Constructor](#runtime_exception__ctor)|Initializes a new instance of the `runtime_exception` class.|  
|[runtime_exception::~runtime_exception Destructor](#runtime_exception__dtor)|Destroys the `runtime_exception` object.|  
  
### Public Methods  
  
|Name|Description|  
|----------|-----------------|  
|[runtime_exception::get_error_code Method](#runtime_exception__get_error_code)|Returns the error code that caused the exception.|  
  
### Public Operators  
  
|Name|Description|  
|----------|-----------------|  
|[runtime_exception::operator= Operator](#runtime_exception__operator_eq)|Copies the contents of the specified `runtime_exception` object into this one.|  
  
## Inheritance Hierarchy  
 `exception`  
  
 `runtime_exception`  
  
## Requirements  
 **Header:** amprt.h  
  
 **Namespace:** Concurrency  

## <a name="runtime_exception__ctor"></a>  runtime_exception Constructor  
## <a name="runtime_exception__dtor"></a>  ~runtime_exception Destructor  
## <a name="runtime_exception__get_error_code"></a>  get_error_code   
## <a name="runtime_exception__operator_eq"></a>  operator=   
  

  
## See Also  
 [Concurrency Namespace (C++ AMP)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)
