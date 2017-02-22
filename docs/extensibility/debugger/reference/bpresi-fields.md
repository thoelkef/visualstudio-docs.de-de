---
title: "BPRESI_FIELDS | Microsoft Docs"
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
  - "BPRESI_FIELDS"
helpviewer_keywords: 
  - "BPRESI_FIELDS-enumeration"
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# BPRESI_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die über die erfolgreiche Behebung eines Haltepunkts Informationen abgerufen werden sollen.  
  
## Syntax  
  
```cpp#  
enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
typedef DWORD BPRESI_FIELDS;  
```  
  
```c#  
public enum enum_BPRESI_FIELDS {   
   BPRESI_BPRESLOCATION = 0x0001,  
   BPRESI_PROGRAM       = 0x0002,  
   BPRESI_THREAD        = 0x0004,  
   BPRESI_ALLFIELDS     = 0xffffffff  
};  
```  
  
## Mitglieder  
 BPRESI\_BPRESLOCATION  
 Initialisieren Sie das Feld\/verwenden, `bpResLocation` \(Haltepunkt auflösungs\) der Speicherort [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Struktur.  
  
 BPRESI\_PROGRAM  
 Initialisieren Sie `pProgram` \/verwenden das Feld `BP_RESOLUTION_INFO` Struktur.  
  
 BPRESI\_THREAD  
 Initialisieren Sie `pThread` \/verwenden das Feld `BP_RESOLUTION_INFO` Struktur.  
  
 BPRESI\_ALLFIELDS  
 Gibt alle Felder angezeigt.  
  
## Hinweise  
 So [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) die Methode übergeben, um anzugeben, welche Felder der [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Struktur initialisiert werden sollen.  
  
 Diese Flags werden auch verwendet, um anzugeben, welche Felder der `BP_RESOLUTION_INFO` Struktur verwendet und gültig sind, wenn diese Struktur zurückgegeben wird.  
  
 Diese Werte können mit bitweisen `OR`kombiniert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)