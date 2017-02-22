---
title: "GETHOSTNAME_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GETHOSTNAME_TYPE"
helpviewer_keywords: 
  - "GETHOSTNAME_TYPE-enumeration"
ms.assetid: 2be92bea-8133-412b-9015-1833baf16e1b
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# GETHOSTNAME_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt den Typ des Hostnamens an.  
  
## Syntax  
  
```cpp#  
enum enum_GETHOSTNAME_TYPE {   
   GHN_FRIENDLY_NAME = 0,  
   GHN_FILE_NAME     = 1  
};  
typedef DWORD GETHOSTNAME_TYPE;  
```  
  
```c#  
public enum enum_GETHOSTNAME_TYPE {   
   GHN_FRIENDLY_NAME = 0,  
   GHN_FILE_NAME     = 1  
};  
```  
  
## Mitglieder  
 GHN\_FRIENDLY\_NAME  
 Gibt einen Anzeigenamen des Hosts an.  
  
 GHN\_FILE\_NAME  
 Gibt einen Dateinamen des Hosts an.  
  
## Hinweise  
 Diese Werte werden als Argument an die [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)\-Methode übergeben, um einen Hostnamen in verschiedenen Formaten abzurufen.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)