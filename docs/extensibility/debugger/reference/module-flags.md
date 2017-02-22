---
title: "MODULE_FLAGS | Microsoft Docs"
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
  - "MODULE_FLAGS"
helpviewer_keywords: 
  - "MODULE_FLAGS-enumeration"
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# MODULE_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Wird verwendet, um ein Modul zu beschreiben.  
  
## Syntax  
  
```cpp#  
enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
typedef DWORD MODULE_FLAGS;  
```  
  
```c#  
public enum enum_MODULE_FLAGS {   
   MODULE_FLAG_NONE        = 0x0000,  
   MODULE_FLAG_SYSTEM      = 0x0001,  
   MODULE_FLAG_SYMBOLS     = 0x0002,  
   MODULE_FLAG_64BIT       = 0x0004,  
   MODULE_FLAG_OPTIMIZED   = 0x0008,  
   MODULE_FLAG_UNOPTIMIZED = 0x0010  
};  
```  
  
## Mitglieder  
 MODULE\_FLAG\_NONE  
 Gibt kein Modul an.  
  
 MODULE\_FLAG\_SYSTEM  
 Gibt ein Modul System an.  
  
 MODULE\_FLAG\_SYMBOLS  
 Gibt ein Symbol Modul an.  
  
 MODULE\_FLAG\_64BIT  
 Gibt ein 64\-Bit\-Modul an.  
  
 MODULE\_FLAG\_OPTIMIZED  
 Gibt das Modul optimiert ist.  Dieser Zustand wird im **Module** Fenster reflektiert.  
  
 MODULE\_FLAG\_UNOPTIMIZED  
 Gibt das Modul ist nicht optimiert wurde.  Dieser Zustand wird im **Module** Fenster reflektiert.  Dies ist der Standardzustand.  
  
## Hinweise  
 Wird für den `m_dwModuleFlags`\-Member der [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) Struktur.  
  
 Diese Flags werden mit bitweisen `OR`kombiniert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)