---
title: "BPREQI_FIELDS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BPREQI_FIELDS"
helpviewer_keywords: 
  - "BPREQI_FIELDS-enumeration"
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# BPREQI_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die über einen Haltepunkt erforderlichen Informationen abgerufen werden sollen.  
  
## Syntax  
  
```cpp  
enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
typedef DWORD BPREQI_FIELDS;  
```  
  
```c#  
public enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
```  
  
## Mitglieder  
 BPREQI\_BPLOCATION  
 Initialisieren Sie das Feld\/verwenden, `bpLocation` \(Haltepunktposition\) der [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) oder [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Struktur.  
  
 BPREQI\_LANGUAGE  
 Initialisieren Sie verwenden das Feld `guidLanguage` \/oder `BP_REQUEST_INFO` der `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI\_PROGRAM  
 Initialisieren Sie verwenden das Feld `pProgram` \/oder `BP_REQUEST_INFO` der `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI\_PROGRAMNAME  
 Initialisieren Sie verwenden das Feld `bstrProgramName` \/oder `BP_REQUEST_INFO` der `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI\_THREAD  
 Initialisieren Sie verwenden das Feld `pThread` \/oder `BP_REQUEST_INFO` der `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI\_THREADNAME  
 Initialisieren Sie verwenden das Feld `bstrThreadName` \/oder `BP_REQUEST_INFO` der `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI\_PASSCOUNT  
 Initialisieren Sie verwenden das Feld `bpPassCount` \/oder `BP_REQUEST_INFO` der `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI\_CONDITION  
 Initialisieren Sie das Feld\/verwenden, `bpCondition` \(Haltepunktzustand\) der `BP_REQUEST_INFO` oder `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI\_FLAGS  
 Initialisieren Sie verwenden das Feld `dwFlags` \/oder `BP_REQUEST_INFO` der `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI\_ALLOLDFIELDS  
 Initialisieren Sie die Felder für alle\/verwenden `BP_REQUEST_INFO` Struktur.  
  
 BPREQI\_VENDOR  
 Initialisieren Sie verwenden das Feld aus `guidVendor` \/ `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI\_CONSTRAINT  
 Initialisieren Sie verwenden das Feld aus `bstrConstraint` \/ `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI\_TRACEPOINT  
 Initialisieren Sie verwenden das Feld aus `bstrTracepoint` \/ `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI\_ALLFIELDS  
 Gibt alle Felder für die `BP_REQUEST_INFO2` Struktur an.  
  
## Hinweise  
 Übergabe als Argument an den [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) und [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)\-Methoden, um anzugeben, welche Felder der [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) und [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Strukturen initialisiert werden sollen.  
  
 Diese Flags werden auch verwendet, um anzugeben, welche Felder der `BP_REQUEST_INFO` und `BP_REQUEST_INFO2` Strukturen verwendet und gültig sind, wenn jede Struktur zurückgegeben wird.  
  
 Diese Werte können mit bitweisen `OR`kombiniert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)