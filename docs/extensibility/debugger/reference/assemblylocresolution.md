---
title: "ASSEMBLYLOCRESOLUTION | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ASSEMBLYLOCRESOLUTION"
helpviewer_keywords: 
  - "ASSEMBLYLOCRESOLUTION-enumeration"
ms.assetid: 0bcfe85c-5f37-4a9d-bf2b-141acd96ad67
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# ASSEMBLYLOCRESOLUTION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt an, wo eine Assembly isoliert ist.  
  
## Syntax  
  
```cpp#  
enum enum_ASSEMBLYLOCRESOLUTION {  
   ALR_NAME      = 0x0,  
   ALR_USERDIR   = 0x1,  
   ALR_SHAREDDIR = 0x2,  
   ALR_REMOTEDIR = 0x4,  
};  
typedef DWORD ASSEMBLYLOCRESOLUTION;  
```  
  
```c#  
public enum enum_ASSEMBLYLOCRESOLUTION {  
   ALR_NAME      = 0x0,  
   ALR_USERDIR   = 0x1,  
   ALR_SHAREDDIR = 0x2,  
   ALR_REMOTEDIR = 0x4,  
};  
```  
  
## Mitglieder  
 ALR\_NAME  
 Die Assembly befindet sich im aktuellen Namespace.  
  
 ALR\_USERDIR  
 Die Assembly befindet sich in einem Benutzerverzeichnis.  
  
 ALR\_SHAREDDIR  
 Die Assembly befindet sich im freigegebenen Verzeichnis.  
  
 ALR\_REMOTEDIR  
 Die Assembly befindet sich in einem Verzeichnis. Remote  
  
## Hinweise  
 Diese Werte werden durch die [ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md) und [GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)\-Methode zurückgegeben.  
  
 Diese Werte können mit dem `OR` Vorgang kombiniert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)   
 [GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)