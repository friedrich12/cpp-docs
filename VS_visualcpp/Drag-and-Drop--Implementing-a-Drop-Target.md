---
title: "Drag and Drop: Implementing a Drop Target"
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
ms.assetid: 0689f1ec-5326-4008-b226-4b373c881358
caps.latest.revision: 8
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
# Drag and Drop: Implementing a Drop Target
This article outlines how to make your application a drop target. Implementing a drop target takes slightly more work than implementing a drop source, but it is still relatively simple. These techniques also apply to non-OLE applications.  
  
#### To implement a drop target  
  
1.  Add a member variable to each view in the application that you want to be a drop target. This member variable must be of type `COleDropTarget` or a class derived from it.  
  
2.  From your view class's function that handles the `WM_CREATE` message (typically `OnCreate`), call the new member variable's `Register` member function. `Revoke` will be called automatically for you when your view is destroyed.  
  
3.  Override the following functions. If you want the same behavior throughout your application, override these functions in your view class. If you want to modify behavior in isolated cases or want to enable dropping on non-`CView` windows, override these functions in your `COleDropTarget`-derived class.  
  
    |Override|To allow|  
    |--------------|--------------|  
    |`OnDragEnter`|Drop operations to occur in the window. Called when the cursor first enters the window.|  
    |`OnDragLeave`|Special behavior when the drag operation leaves the specified window.|  
    |`OnDragOver`|Drop operations to occur in the window. Called when the cursor is being dragged across the window.|  
    |`OnDrop`|Handling of data being dropped into the specified window.|  
    |`OnScrollBy`|Special behavior for when scrolling is necessary in the target window.|  
  
 See the MAINVIEW.CPP file that is part of the MFC OLE sample [OCLIENT](../VS_visualcpp/Visual-C---Samples.md) for an example of how these functions work together.  
  
 For more information, see:  
  
-   [Implementing a Drop Source](../VS_visualcpp/Drag-and-Drop--Implementing-a-Drop-Source.md)  
  
-   [Creating and Destroying OLE Data Objects and Data Sources](../VS_visualcpp/Data-Objects-and-Data-Sources--Creation-and-Destruction.md)  
  
-   [Manipulating OLE Data Objects and Data Sources](../VS_visualcpp/Data-Objects-and-Data-Sources--Manipulation.md)  
  
## See Also  
 [Drag and Drop (OLE)](../VS_visualcpp/Drag-and-Drop--OLE-.md)   
 [COleDropTarget Class](../VS_visualcpp/COleDropTarget-Class.md)