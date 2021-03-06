---
title: "Copy Constructors and Copy Assignment Operators (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "= operator, copying objects"
  - "assignment statements, copying objects"
  - "assignment operators, for copying objects"
  - "objects [C++], copying"
  - "initializing objects, by copying objects"
  - "copying objects"
  - "assigning values to copy objects"
ms.assetid: a94fe1f9-0289-4fb9-8633-77c654002c0d
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
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
# Copy Constructors and Copy Assignment Operators (C++)
> [!NOTE]
>  Starting in C++11, two kinds of assignment are supported in the language: *copy assignment* and *move assignment*. In this article "assignment" means copy assignment unless explicitly stated otherwise. For information about move assignment, see [Move Constructors and Move Assignment Operators (C++)](http://msdn.microsoft.com/en-us/1442de5f-37a5-42a1-83a6-ec9cfe0414db).  
>   
>  Both the assignment operation and the initialization operation cause objects to be copied.  
  
-   **Assignment**: When one object's value is assigned to another object, the first object is copied to the second object. Therefore,  
  
    ```cpp  
    Point a, b;  
    ...  
    a = b;  
    ```  
  
     causes the value of `b` to be copied to `a`.  
  
-   **Initialization**: Initialization occurs when a new object is declared, when arguments are passed to functions by value, or when values are returned from functions by value.  
  
 You can define the semantics of "copy" for objects of class type. For example, consider this code:  
  
```cpp  
TextFile a, b;  
a.Open( "FILE1.DAT" );  
b.Open( "FILE2.DAT" );  
b = a;  
```  
  
 The preceding code could mean "copy the contents of FILE1.DAT to FILE2.DAT" or it could mean "ignore FILE2.DAT and make `b` a second handle to FILE1.DAT." You must attach appropriate copying semantics to each class, as follows.  
  
-   By using the assignment operator `operator=` together with a reference to the class type as the return type and the parameter that is passed by `const` reference—for example `ClassName& operator=(const ClassName& x);`.  
  
-   By using the copy constructor. For more information about the copy constructor, see [Rules for Declaring Constructors](../misc/rules-for-declaring-constructors.md).  
  
 If you do not declare a copy constructor, the compiler generates a member-wise copy constructor for you.  If you do not declare a copy assignment operator, the compiler generates a member-wise copy assignment operator for you. Declaring a copy constructor does not suppress the compiler-generated copy assignment operator, nor vice versa. If you implement either one, we recommend that you also implement the other one so that the meaning of the code is clear.  
  
 Member-wise assignment is covered in more detail in [(NOTINBUILD) Memberwise Assignment and Initialization](http://msdn.microsoft.com/en-us/94048213-8b49-4416-8069-b1b7a6f271f9).  
  
 The copy constructor takes an argument of type *class-name***&**, where *class-name* is the name of the class for which the constructor is defined. For example:  
  
```cpp  
// spec1_copying_class_objects.cpp  
class Window  
{  
public:  
    Window( const Window& ); // Declare copy constructor.  
    // ...  
};  
  
int main()  
{  
}  
```  
  
> [!NOTE]
>  Make the type of the copy constructor's argument *const class-name***&** whenever possible. This prevents the copy constructor from accidentally changing the object from which it is copying. It also enables copying from **const** objects.  
  
## Compiler generated copy constructors  
 Compiler-generated copy constructors, like user-defined copy constructors, have a single argument of type "reference to *class-name*." An exception is when all base classes and member classes have copy constructors declared as taking a single argument of type **const** *class-name***&**. In such a case, the compiler-generated copy constructor's argument is also **const**.  
  
 When the argument type to the copy constructor is not **const**, initialization by copying a **const** object generates an error. The reverse is not true: If the argument is **const**, you can initialize by copying an object that is not **const**.  
  
 Compiler-generated assignment operators follow the same pattern with regard to **const.** They take a single argument of type *class-name***&** unless the assignment operators in all base and member classes take arguments of type **const** *class-name&.* In this case, the class's generated assignment operator takes a **const** argument.  
  
> [!NOTE]
>  When virtual base classes are initialized by copy constructors, compiler-generated or user-defined, they are initialized only once: at the point when they are constructed.  
  
 The implications are similar to those of the copy constructor. When the argument type is not **const**, assignment from a **const** object generates an error. The reverse is not true: If a **const** value is assigned to a value that is not **const**, the assignment succeeds.  
  
 For more information about overloaded assignment operators, see [Assignment](../cpp/assignment.md).  
  
## See Also  
 [Special Member Functions](../misc/special-member-functions-cpp.md)