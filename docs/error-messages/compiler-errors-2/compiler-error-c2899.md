---
title: "Compiler Error C2899 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2899"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2899"
ms.assetid: a8942605-5bef-4d1c-b74a-41ae25423b22
caps.latest.revision: 10
author: "corob-msft"
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
# Compiler Error C2899
typename cannot be used outside a template declaration  
  
 The [typename](../../cpp/typename.md) keyword can be used only in a template definition or declaration. In a template declaration, it can be used in two ways:  
  
```  
// C2899.cpp  
// compile with: /c  
template<typename T>   
class X {};  
  
// Another way  
template<class T>   
struct XX {  
   typename T::A a;   // T::A is a type  
};  
```  
  
 The following sample generates C2899:  
  
```  
// C2899b.cpp  
// compile with: /c  
struct Y {  
   typedef int B;  
   typename Y::B b;   // C2899  
};  
  
```