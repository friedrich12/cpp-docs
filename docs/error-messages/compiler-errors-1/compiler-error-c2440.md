---
title: "Compiler Error C2440 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2440"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2440"
ms.assetid: 36e6676c-f04f-4715-8ba1-f096c4bf3b44
caps.latest.revision: 27
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
# Compiler Error C2440
'conversion' : cannot convert from 'type1' to 'type2'  
  
 The compiler cannot cast from '`type1`' to '`type2`'.  
  
## Example  
 C2440 can be caused if you attempt to initialize a non-const `char*` (or `wchar_t*`) by using a string literal in C++ code, when the compiler conformance option [/Zc:strictStrings](../../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md) is set. In C, the type of a string literal is array of `char`, but in C++, it is array of `const``char`. This sample generates C2440:  
  
```cpp  
// C2440s.cpp  
// Build: cl /Zc:strictStrings /W3 C2440s.cpp  
// When built, the compiler emits:  
// error C2440: 'initializing' : cannot convert from 'const char [5]'   
// to 'char *'  
//        Conversion from string literal loses const qualifier (see  
// /Zc:strictStrings)  
  
int main() {  
   char* s1 = "test"; // C2440  
   const char* s2 = "tests"; // OK  
}  
```  
  
## Example  
 C2440 can also be caused if you attempt to convert a pointer to member to void*. The next sample generates C2440:  
  
```cpp  
// C2440.cpp  
class B {  
public:  
   void  f(){;}  
  
   typedef void (B::*pf)();  
  
   void f2(pf pf) {  
       (this->*pf)();  
       void* pp = (void*)pf;   // C2440  
   }  
  
   void f3() {  
      f2(f);  
   }  
};  
```  
  
## Example  
 C2440 can also be caused if you attempt to cast from a type that is only forward declared but not defined. This sample generates C2440:  
  
```cpp  
// c2440a.cpp   
struct Base { }; // Defined  
  
struct Derived; // Forward declaration, not defined  
  
Base * func(Derived * d) {  
    return static_cast<Base *>(d); // error C2440: 'static_cast' : cannot convert from 'Derived *' to 'Base *'  
}  
  
```  
  
## Example  
 The C2440 errors on lines 15 and 16 of the next sample are qualified with the `Incompatible calling conventions for UDT return value` message. (A UDT is a user-defined type, such as a class, struct, or union.) These kinds of incompatibility errors are caused when the calling convention of a UDT specified in the return type of a forward declaration conflicts with the actual calling convention of the UDT and when a function pointer is involved.  
  
 In the example, first there are forward declarations for a struct and for a function that returns the struct; the compiler assumes that the struct uses the C++ calling convention. Next is the struct definition, which, by default, uses the C calling convention. Because the compiler does not know the calling convention of the struct until it finishes reading the entire struct, the calling convention for the struct in the return type of `get_c2` is also assumed to be C++.  
  
 The struct is followed by another function declaration that returns the struct, but at this point, the compiler knows that the struct's calling convention is C++. Similarly, the function pointer, which returns the struct, is defined after the struct definition so that the compiler knows that the struct uses the C++ calling convention.  
  
 To resolve C2440 that occurs because of incompatible calling conventions, declare functions that return a UDT after the UDT definition.  
  
```cpp  
// C2440b.cpp  
struct MyStruct;  
  
MyStruct get_c1();  
  
struct MyStruct {  
   int i;  
   static MyStruct get_C2();  
};  
  
MyStruct get_C3();  
  
typedef MyStruct (*FC)();  
  
FC fc1 = &get_c1;   // C2440, line 15  
FC fc2 = &MyStruct::get_C2;   // C2440, line 16  
FC fc3 = &get_C3;  
  
class CMyClass {  
public:  
   explicit CMyClass( int iBar)  
      throw()   {  
   }  
  
   static CMyClass get_c2();  
};  
  
int main() {  
   CMyClass myclass = 2;   // C2440  
   // try one of the following  
   // CMyClass myclass{2};  
   // CMyClass myclass(2);  
  
   int *i;  
   float j;  
   j = (float)i;   // C2440, cannot cast from pointer to int to float  
}  
```  
  
## Example  
 C2440 can also occur if you assign zero to an interior pointer:  
  
```cpp  
// C2440c.cpp  
// compile with: /clr  
int main() {  
   array<int>^ arr = gcnew array<int>(100);  
   interior_ptr<int> ipi = &arr[0];  
   ipi = 0;   // C2440  
   ipi = nullptr;   // OK  
}  
```  
  
## Example  
 C2440 can also occur for an incorrect use of a user-defined conversion. For more information about user-defined conversions, see [User-Defined Conversions (C++/CLI)](../../dotnet/user-defined-conversions-cpp-cli.md)). This sample generates C2440:  
  
```cpp  
// C2440d.cpp  
// compile with: /clr  
value struct MyDouble {  
   double d;  
   // convert MyDouble to Int32  
   static explicit operator System::Int32 ( MyDouble val ) {  
      return (int)val.d;  
   }  
};  
  
int main() {  
   MyDouble d;  
   int i;  
   i = d;   // C2440  
   // Uncomment the following line to resolve.  
   // i = static_cast<int>(d);  
}  
```  
  
## Example  
 C2440 can also occur if you try to create an instance of a Visual C++ array whose type is a <xref:System.Array>.  For more information, see [Arrays](../../windows/arrays-cpp-component-extensions.md).  The next sample generates C2440:  
  
```cpp  
// C2440e.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   array<int>^ intArray = Array::CreateInstance(__typeof(int), 1);   // C2440  
   // try the following line instead  
   // array<int>^ intArray = safe_cast<array<int> ^>(Array::CreateInstance(__typeof(int), 1));  
}  
```  
  
## Example  
 C2440 can also occur because of changes in the attributes feature.  The following sample generates C2440.  
  
```cpp  
// c2440f.cpp  
// compile with: /LD  
[ module(name="PropDemoLib", version=1.0) ];   // C2440  
// try the following line instead  
// [ module(name="PropDemoLib", version="1.0") ];  
```  
  
## Example  
 The Visual C++ compiler no longer allows the [const_cast Operator](../../cpp/const-cast-operator.md) to down cast when source code that uses **/clr** programming is compiled.  
  
 To resolve this C2440, use the correct cast operator. For more information, see [Casting Operators](../../cpp/casting-operators.md).  
  
 This sample generates C2440:  
  
```cpp  
// c2440g.cpp  
// compile with: /clr  
ref class Base {};  
ref class Derived : public Base {};  
int main() {  
   Derived ^d = gcnew Derived;  
   Base ^b = d;  
   d = const_cast<Derived^>(b);   // C2440  
   d = dynamic_cast<Derived^>(b);   // OK  
}  
```  
  
## Example  
 C2440 can also be generated by using **/clr:oldSyntax**:  
  
```cpp  
// c2440h.cpp  
// compile with: /clr:oldSyntax  
__gc class Base {};  
__gc class Derived : public Base {};  
int main() {  
   Derived *d = new Derived;  
   Base *b = d;  
   d = const_cast<Derived*>(b);   // C2440  
   d = dynamic_cast<Derived*>(b);   // OK  
}  
```