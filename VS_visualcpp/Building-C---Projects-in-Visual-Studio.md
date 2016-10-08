---
title: "Building C++ Projects in Visual Studio"
ms.custom: na
ms.date: 10/07/2016
ms.devlang: 
  - C++
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9e8bc1a2-bb17-4951-937a-c757ed88d2d1
caps.latest.revision: 18
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
# Building C++ Projects in Visual Studio
In the Visual Studio integrated development environment (IDE), there are several ways to build an entire solution or just one project in it. You can also modify build settings and specify custom build steps to make your development process more efficient.  
  
 To build a solution that's open in Visual Studio and selected in **Solution Explorer**, you can:  
  
-   On the menu bar, choose **Build**, **Build Solution**.  
  
-   Or, in **Solution Explorer**, open the shortcut menu for the solution and then choose **Build Solution**.  
  
-   Or, press F7. (This is the default keyboard shortcut for the C/C++ development settings.)  
  
-   Or, in the [Command Window](../Topic/Command%20Window.md) (on the menu bar, choose **View**, **Other Windows**, **Command Window**), enter `Build.BuildSolution`.  
  
-   Or, in the [Quick Launch](../Topic/Quick%20Launch,%20Environment,%20Options%20Dialog%20Box.md) box, enter `build build solution`.  
  
 To build a project that's selected in **Solution Explorer**, you can:  
  
-   On the menu bar, choose **Build**, **Build <Project Name\>**.  
  
-   Or, in **Solution Explorer**, open the shortcut menu for the project and then choose **Build**.  
  
-   Or, in the Command Window (on the menu bar, choose **View**, **Other Windows**, **Command Window**), enter `Build.BuildOnlyProject`.  
  
-   Or, in the Quick Launch box, enter `build project only build only <project name>`.  
  
 When you build a Visual C++ application in Visual Studio, you can modify many of the build's settings in the project's Property Pages dialog box. For information about how to set project properties, see [Working with Project Properties](../VS_visualcpp/Working-with-Project-Properties.md).  
  
 For an example about how to use the IDE to create, build, and debug a C++ project, see [Walkthrough: Explore the Visual Studio IDE with C++](../Topic/Getting%20Started%20with%20C++%20in%20Visual%20Studio.md). For an example about how to use the IDE to build a C++/CLR project, see [Walkthrough: Compiling a C++ Program that Targets the CLR in Visual Studio](../VS_visualcpp/Walkthrough--Compiling-a-C---Program-that-Targets-the-CLR-in-Visual-Studio.md). For an example about how to use the IDE to create a Windows Runtime app, see [Create your first Windows Runtime app using C++](http://msdn.microsoft.com/library/windows/apps/hh974580.aspx).  
  
 To read more about how to build, modify build settings, and specify custom build steps, see the following articles.  
  
## In This Section  
 [Understanding Custom Build Steps and Build Events](../VS_visualcpp/Understanding-Custom-Build-Steps-and-Build-Events.md)  
 Describes how to customize the build process in the integrated development environment.  
  
 [Common Macros for Build Commands and Properties](../VS_visualcpp/Common-Macros-for-Build-Commands-and-Properties.md)  
 Lists macros that you can use where strings are accepted.  
  
 [Building External Projects](../VS_visualcpp/Building-External-Projects.md)  
 Discusses building projects that use facilities outside the integrated development environment.  
  
 [Project Files](../VS_visualcpp/Project-Files.md)  
 Presents the XML structure of a .vcxproj file.  
  
## Related Sections  
 [VC++ Directories, Projects, Options Dialog Box](assetId:///e027448b-c811-4c3d-8531-4325ad3f6e02)  
 Discusses how to modify the search path for executable files, include files, library files, and source code files during a build  
  
 [Compiling and Building](../Topic/Compiling%20and%20Building%20in%20Visual%20Studio.md)  
 Provides information on building within Visual Studio.  
  
 [Building C/C++ Programs](../VS_visualcpp/Building-C-C---Programs.md)  
 Provides links to topics describing building your program from the command line or from the integrated development environment of Visual Studio.  
  
 [C/C++ Building Reference](../VS_visualcpp/C-C---Building-Reference.md)  
 Provides links to an overview of building programs in C++, compiler and linker options, and additional build tools.  
  
 [Upgrading Projects from Earlier Versions of Visual C++](../VS_visualcpp/Upgrading-Projects-from-Earlier-Versions-of-Visual-C--.md)  
 Provides links to topics covering issues on upgrading Visual C++ 6.0 and later projects to Visual C++ .NET.  
  
 [Porting and Upgrading Programs](assetId:///c36c44b3-5a9b-4bb4-9b7a-469aa770ed00)  
 Provides details about porting applications and discusses makefiles.  
  
## See Also  
 [Roadmap for Windows Store apps using C++](assetId:///0b71e4a4-5d8a-4a20-b2ec-e40062675ec1)