---
title: "MACHINE_INFO_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MACHINE_INFO_FIELDS"
helpviewer_keywords: 
  - "MACHINE_INFO_FIELDS-enumeration"
ms.assetid: 2d61d206-7d40-4df1-8c88-1b3c9c78821e
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# MACHINE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt an, welche Art von Informationen für einen bestimmten Computer abzurufen.  
  
## Syntax  
  
```cpp#  
enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
typedef DWORD MACHINE_INFO_FIELDS;  
```  
  
```c#  
public enum enum_MACHINE_INFO_FIELDS {   
   MCIF_NAME  = 0x00000001,  
   MCIF_FLAGS = 0x00000002,  
   MCIF_ALL   = 0x00000003  
};  
```  
  
## Mitglieder  
 MCIF\_NAME  
 Initialisieren Sie verwenden das\/ `bstrName` Feld in der Struktur.  
  
 MCIF\_FLAGS  
 Initialisieren Sie verwenden das\/ `Flags` Feld in der Struktur.  
  
 MIF\_ALL  
 Initialisieren Sie\/verwenden alle Felder in der Struktur.  
  
## Hinweise  
 Diese Werte werden der [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)\-Methode übergeben, um anzugeben, welche Member der [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md) Struktur initialisiert werden sollen.  
  
 Außerdem wird im `Fields`\-Member der `MACHINE_INFO` Struktur, um anzugeben, welche Felder verwendet und gültig sind.  
  
 Diese Flags werden mit bitweisen `OR`kombiniert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md)   
 [GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)