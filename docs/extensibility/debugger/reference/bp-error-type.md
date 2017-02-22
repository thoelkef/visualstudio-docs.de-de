---
title: "BP_ERROR_TYPE | Microsoft Docs"
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
  - "BP_ERROR_TYPE"
helpviewer_keywords: 
  - "BP_ERROR_TYPE-enumeration"
ms.assetid: c483eaab-db29-46de-bfdb-5c2a9a9cfb68
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_ERROR_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt den Fehlertyp eines Haltepunkts an.  
  
## Syntax  
  
```cpp#  
enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
typedef DWORD BP_ERROR_TYPE;  
```  
  
```c#  
public enum enum_BP_ERROR_TYPE {   
   BPET_NONE            = 0x00000000,  
   BPET_TYPE_WARNING    = 0x00000001,  
   BPET_TYPE_ERROR      = 0x00000002,  
   BPET_SEV_HIGH        = 0x0F000000,  
   BPET_SEV_GENERAL     = 0x07000000,  
   BPET_SEV_LOW         = 0x01000000,  
   BPET_TYPE_MASK       = 0x0000ffff,  
   BPET_SEV_MASK        = 0xffff0000,  
   BPET_GENERAL_WARNING = BPET_SEV_GENERAL | BPET_TYPE_WARNING,  
   BPET_GENERAL_ERROR   = BPET_SEV_GENERAL | BPET_TYPE_ERROR,  
   BPET_ALL             = 0xffffffff  
};  
```  
  
## Mitglieder  
 BPET\_NONE  
 Gibt keinen Haltepunkt Fehler an.  
  
 BPET\_TYPE\_WARNING  
 Gibt einen Warnung Format Haltepunkt Fehler an.  
  
 BPET\_TYPE\_ERROR  
 Gibt einen Haltepunkt Format ERROR Fehler an.  
  
 BPET\_SEV\_HIGH  
 Gibt einen Haltepunkt Schweregrad HIGH Fehler an.  
  
 BPET\_SEV\_GENERAL  
 Gibt einen Haltepunkt Schweregrad MEDIUM Fehler an.  
  
 BPET\_SEV\_LOW  
 Geben einen Fehler im Zusammenhang mit niedriger Schweregrad Haltepunkt an.  
  
 BPET\_TYPE\_MASK  
 Gibt einen Haltepunkt Format Maske Fehler an.  
  
 BPET\_SEV\_MASK  
 Gibt einen Schweregrad\-Maske Format Haltepunkt Fehler an.  
  
 BPET\_GENERAL\_WARNING  
 Gibt einen Allgemein\-Warnung Format Haltepunkt Fehler an.  
  
 BPET\_GENERAL\_ERROR  
 Gibt einen Allgemein\-ERROR Format Haltepunkt Fehler an.  
  
 BPET\_ALL  
 Gibt alle Haltepunkt Fehlertypen an.  
  
## Hinweise  
 Diese Werte können mit bitweisen `OR` kombiniert werden, und für den `dwType`\-Member der [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Struktur verwendet werden.  Übergabe als Parameter an die [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)\-Methode.  
  
 Eine Haltepunkt Fehlertyp wird von einem Typ und einem Schweregrad.  Dies bedeutet, dass ein Haltepunkt niemals Fehlertyps nur einen Typ \(z. B. `BPET_TYPE_ERROR`\) oder ein Schweregrad \(z. B.`BPET_SEV_GENERAL`\) allein ist.  `BPET_GENERAL_WARNING` und `BPET_GENERAL_ERROR` stellen vordefinierte Werte für allgemeine Warnungs\- und Fehler von Haltepunkten bereit.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)