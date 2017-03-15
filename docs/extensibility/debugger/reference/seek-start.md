---
title: "SEEK_START | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SEEK_START"
helpviewer_keywords: 
  - "SEEK_START-enumeration"
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# SEEK_START
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die Position an, aus der die Suche in einem Disassemblys datenstrom starten.  
  
## Syntax  
  
```cpp#  
enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
typedef DWORD SEEK_START;  
```  
  
```c#  
public enum enum_SEEK_START {   
   SEEK_START_BEGIN       = 0x0001,  
   SEEK_START_END         = 0x0002,  
   SEEK_START_CURRENT     = 0x0003,  
   SEEK_START_CODECONTEXT = 0x0004,  
   SEEK_START_CODELOCID   = 0x0005  
};  
```  
  
## Mitglieder  
 SEEK\_START\_BEGIN  
 Beginnt die Suche am Anfang des aktuellen Dokuments.  
  
 SEEK\_START\_END  
 Beginnt die Suche am Ende des aktuellen Dokuments.  
  
 SEEK\_START\_CURRENT  
 Startet die an der aktuellen Position des aktuellen Dokuments finden.  
  
 SEEK\_START\_CODECONTEXT  
 Startet die im angegebenen Kontext des aktuellen Dokuments Code suchen.  
  
 SEEK\_START\_CODELOCID  
 Startet die am angegebenen Speicherort des Codes Bezeichner finden.  Speicherort des Codes Bezeichner werden abgerufen, indem [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)aufruft.  
  
## Hinweise  
 Übergabe als Argument an die [Suchen](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)\-Methode.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Suchen](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)   
 [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)