---
title: "CONTEXT_INFO_FIELDS | Microsoft Docs"
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
  - "CONTEXT_INFO_FIELDS"
helpviewer_keywords: 
  - "CONTEXT_INFO_FIELDS-enumeration"
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# CONTEXT_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt an, welche über einen Speicher Elementkontext Informationen abzurufen.  
  
## Syntax  
  
```cpp#  
enum enum_CONTEXT_INFO_FIELDS {   
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
typedef DWORD CONTEXT_INFO_FIELDS;  
```  
  
```c#  
public enum enum_CONTEXT_INFO_FIELDS {  
   CIF_MODULEURL =       0x00000001,  
   CIF_FUNCTION =        0x00000002,  
   CIF_FUNCTIONOFFSET =  0x00000004,  
   CIF_ADDRESS =         0x00000008,  
   CIF_ADDRESSOFFSET =   0x00000010,  
   CIF_ADDRESSABSOLUTE = 0x00000020,  
   CIF_ALLFIELDS =       0x0000003f  
};  
```  
  
## Mitglieder  
 CIF\_MODULEURL  
 Initialisieren Sie `bstrModuleUrl` \/verwenden das Feld [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md) Struktur.  
  
 CIF\_FUNCTION  
 Initialisieren Sie `bstrFunction` \/verwenden das Feld `CONTEXT_INFO` Struktur.  
  
 CIF\_FUNCTIONOFFSET  
 Initialisieren Sie `posFunctionOffset` \/verwenden das Feld `CONTEXT_INFO` Struktur.  
  
 CIF\_ADDRESS  
 Initialisieren Sie `bstrAddress` \/verwenden das Feld `CONTEXT_INFO` Struktur.  
  
 CIF\_ADDRESSOFFSET  
 Initialisieren Sie `bstrAddressOffset` \/verwenden das Feld `CONTEXT_INFO` Struktur.  
  
 CIF\_ALLFIELDS  
 Initialisieren Sie `CONTEXT_INFO` \/verwenden alle Felder der Struktur.  
  
## Hinweise  
 Diese Werte werden [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) ein Parameter an die Methode übergeben, um anzugeben, welche Felder der [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md) Struktur initialisiert werden sollen.  
  
 Diese Flags werden auch verwendet, um anzugeben, welche Felder der `CONTEXT_INFO` Struktur verwendet und gültig sind, wenn die Struktur zurückgegeben wird.  
  
 Diese Werte werden mit einem bitweisen OR\-Operation kombiniert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)