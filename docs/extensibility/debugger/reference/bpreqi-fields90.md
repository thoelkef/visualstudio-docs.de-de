---
title: "BPREQI_FIELDS90 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "BPREQI_FIELDS90-enumeration"
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# BPREQI_FIELDS90
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Listet die gültigen Werte auf, die die zu einer Haltepunkt erforderlichen Informationen abgerufen werden sollen.  Diese Enumeration wird die [BPREQI\_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)\-Enumeration.  
  
## Syntax  
  
```cpp#  
enum enum_BPREQI_FIELDS90  
{  
   // VS 8.0 values  
   BPREQI90_BPLOCATION                = 0x0001,  
   BPREQI90_LANGUAGE                  = 0x0002,  
   BPREQI90_PROGRAM                   = 0x0004,  
   BPREQI90_PROGRAMNAME               = 0x0008,  
   BPREQI90_THREAD                    = 0x0010,  
   BPREQI90_THREADNAME                = 0x0020,  
   BPREQI90_PASSCOUNT                 = 0x0040,  
   BPREQI90_CONDITION                 = 0x0080,  
   BPREQI90_FLAGS                     = 0x0100,  
   BPREQI90_ALLOLDFIELDS              = 0x01ff,  
   BPREQI90_VENDOR                    = 0x0200,  
   BPREQI90_CONSTRAINT                = 0x0400,  
   BPREQI90_TRACEPOINT                = 0x0800,  
  
   // Values added in VS 9.0  
   BPREQI90_MACROTRACEPOINT           = 0x1000,  
  
   BPREQI90_ALLFIELDS                 = 0xffff  
};  
typedef DWORD BPREQI_FIELDS90;  
```  
  
```c#  
public enum enum_BPREQI_FIELDS90  
{  
    // VS 8.0 values  
    BPREQI90_BPLOCATION                = 0x0001,  
    BPREQI90_LANGUAGE                  = 0x0002,  
    BPREQI90_PROGRAM                   = 0x0004,  
    BPREQI90_PROGRAMNAME               = 0x0008,  
    BPREQI90_THREAD                    = 0x0010,  
    BPREQI90_THREADNAME                = 0x0020,  
    BPREQI90_PASSCOUNT                 = 0x0040,  
    BPREQI90_CONDITION                 = 0x0080,  
    BPREQI90_FLAGS                     = 0x0100,  
    BPREQI90_ALLOLDFIELDS              = 0x01ff,  
    BPREQI90_VENDOR                    = 0x0200,  
    BPREQI90_CONSTRAINT                = 0x0400,  
    BPREQI90_TRACEPOINT                = 0x0800,  
  
    // Values added in VS 9.0  
    BPREQI90_MACROTRACEPOINT           = 0x1000,  
  
    BPREQI90_ALLFIELDS                 = 0xffff  
};  
```  
  
#### Parameter  
 BPREQI90\_BPLOCATION  
 Initialisierungs\- oder verwenden Sie das Feld `bpLocation` \(Haltepunktposition\) der [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) oder [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Struktur.  
  
 BPREQI90\_LANGUAGE  
 Initialisierungs\- oder verwenden Sie die `guidLanguage` Feld der `BP_REQUEST_INFO` oder `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI90\_PROGRAM  
 Initialisierungs\- oder verwenden Sie die `pProgram` Feld der `BP_REQUEST_INFO` oder `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI90\_PROGRAMNAME  
 Initialisierungs\- oder verwenden Sie die `bstrProgramName` Feld der `BP_REQUEST_INFO` oder `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI90\_THREAD  
 Initialisierungs\- oder verwenden Sie die `pThread` Feld der `BP_REQUEST_INFO` oder `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI90\_THREADNAME  
 Initialisierungs\- oder verwenden Sie die `bstrThreadName` Feld der `BP_REQUEST_INFO` oder `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI90\_PASSCOUNT  
 Initialisierungs\- oder verwenden Sie die `bpPassCount` Feld der `BP_REQUEST_INFO` oder `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI90\_CONDITION  
 Initialisierungs\- oder verwenden Sie das Feld `bpCondition` \(Haltepunktzustand\) der `BP_REQUEST_INFO` oder `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI90\_FLAGS  
 Initialisierungs\- oder verwenden Sie die `dwFlags` Feld der `BP_REQUEST_INFO` oder `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI90\_ALLOLDFIELDS  
 Initialisierungs\- oder verwenden Sie alle Felder für die `BP_REQUEST_INFO` Struktur.  
  
 BPREQI90\_VENDOR  
 Initialisierungs\- oder verwenden Sie die `guidVendor` Feld aus `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI90\_CONSTRAINT  
 Initialisieren oder `bstrConstraint` verwenden das Feld aus `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI90\_TRACEPOINT  
 Initialisierungs\- oder verwenden Sie die `bstrTracepoint` Feld aus `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI90\_MACROTRACEPOINT  
 Initialisierungs\- oder verwenden Sie die `bstrMacroTracepoint` Feld aus `BP_REQUEST_INFO2` Struktur.  BPREQI\_ALLFIELDS umfasst keine dieses Feld ein.  
  
 BPREQI90\_ALLFIELDS  
 Gibt alle Felder für die `BP_REQUEST_INFO2` Struktur an.  
  
## Anforderungen  
 Header: Msdbg90.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)