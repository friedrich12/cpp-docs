---
title: "Adding or Deleting a String"
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
ms.topic: article
ms.assetid: 077077b4-0f4b-4633-92d6-60b321164cab
caps.latest.revision: 10
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
# Adding or Deleting a String
You can quickly insert new entries into the string table using the String editor. New strings are placed at the end of the table and are given the next available identifier. You can then edit the ID, Value, or Caption properties in the [Properties window](../Topic/Properties%20Window.md) as needed.  
  
 The String editor makes sure you do not use an ID that's already in use. If you select an ID already in use, the String editor will notify you and then assign a generic unique ID, for example IDS_STRING58113.  
  
### To add a string table entry  
  
1.  Open the string table by double-clicking its icon in [Resource View](../VS_visualcpp/Resource-View-Window.md).  
  
    > [!NOTE]
    >  If your project doesn't already contain an .rc file, please see [Creating a New Resource Script File](../VS_visualcpp/How-to--Create-a-Resource-Script-File.md).  
  
2.  Right-click within the string table and choose **New String** from the shortcut menu.  
  
3.  In the **String** editor, select an **ID** from the ID drop-down list or type an ID directly in place.  
  
4.  Edit the **Value**, if necessary.  
  
5.  Type an entry for the **Caption**.  
  
    > [!NOTE]
    >  Null strings are not allowed in Windows string tables. If you create an entry in the string table that is a null string, you will receive a message asking you to "Please enter a string for this table entry."  
  
### To delete a string table entry  
  
1.  Select the entry you want to delete.  
  
2.  On the **Edit** menu, click **Delete**.  
  
 \- or -  
  
-   Right-click the string you want to delete and choose **Delete** from the shortcut menu.  
  
 \- or -  
  
-   Press the **DELETE** key.  
  
 For information on adding resources to managed projects (those that target the common language runtime), please see [Resources in Applications](../Topic/Resources%20in%20Desktop%20Apps.md) in the *.NET Framework Developer's Guide.* For information on manually adding resource files to managed projects, accessing resources, displaying static resources, and assigning resources strings to properties, see [Walkthrough: Localizing Windows Forms](assetId:///9a96220d-a19b-4de0-9f48-01e5d82679e5) and [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 **Requirements**  
  
 Win32  
  
## See Also  
 [String Editor](../VS_visualcpp/String-Editor.md)   
 [Strings](_win32_Strings)   
 [About Strings](_win32_About_Strings_cpp)