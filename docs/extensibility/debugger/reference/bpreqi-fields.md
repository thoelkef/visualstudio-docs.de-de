---
title: BPREQI_FIELDS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ff66a2c23f96ad083d84a937a45c1b2b8cf3ddec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103915"
---
# <a name="bpreqifields"></a>BPREQI_FIELDS
Gibt die Informationen über einen Breakpoint-Anforderung abgerufen werden sollen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
typedef DWORD BPREQI_FIELDS;  
```  
  
```csharp  
public enum enum_BPREQI_FIELDS {   
   BPREQI_BPLOCATION   = 0x0001,  
   BPREQI_LANGUAGE     = 0x0002,  
   BPREQI_PROGRAM      = 0x0004,  
   BPREQI_PROGRAMNAME  = 0x0008,  
   BPREQI_THREAD       = 0x0010,  
   BPREQI_THREADNAME   = 0x0020,  
   BPREQI_PASSCOUNT    = 0x0040,  
   BPREQI_CONDITION    = 0x0080,  
   BPREQI_FLAGS        = 0x0100,  
   BPREQI_ALLOLDFIELDS = 0x01ff  
   BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only  
   BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only  
   BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only  
   BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only  
};  
```  
  
## <a name="members"></a>Member  
 BPREQI_BPLOCATION  
 Initialisieren/verwenden die `bpLocation` Feld (breakpointposition), der die [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) oder [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Struktur.  
  
 BPREQI_LANGUAGE  
 Die Initialisierung/verwenden die `guidLanguage` Feld der `BP_REQUEST_INFO` oder `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI_PROGRAM  
 Die Initialisierung/verwenden die `pProgram` Feld der `BP_REQUEST_INFO` oder `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI_PROGRAMNAME  
 Die Initialisierung/verwenden die `bstrProgramName` Feld der `BP_REQUEST_INFO` oder `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI_THREAD  
 Die Initialisierung/verwenden die `pThread` Feld der `BP_REQUEST_INFO` oder `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI_THREADNAME  
 Die Initialisierung/verwenden die `bstrThreadName` Feld der `BP_REQUEST_INFO` oder `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI_PASSCOUNT  
 Die Initialisierung/verwenden die `bpPassCount` Feld der `BP_REQUEST_INFO` oder `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI_CONDITION  
 Initialisieren/verwenden die `bpCondition` Feld (haltepunktbedingung), der die `BP_REQUEST_INFO` oder `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI_FLAGS  
 Die Initialisierung/verwenden die `dwFlags` Feld der `BP_REQUEST_INFO` oder `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI_ALLOLDFIELDS  
 Alle Felder für die Initialisierung/verwenden die von der `BP_REQUEST_INFO` Struktur.  
  
 BPREQI_VENDOR  
 Die Initialisierung/verwenden die `guidVendor` Feld `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI_CONSTRAINT  
 Die Initialisierung/verwenden die `bstrConstraint` Feld `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI_TRACEPOINT  
 Die Initialisierung/verwenden die `bstrTracepoint` Feld `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI_ALLFIELDS  
 Gibt an, alle Felder für die `BP_REQUEST_INFO2` Struktur.  
  
## <a name="remarks"></a>Hinweise  
 Übergeben als Argument an die [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) und [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Methoden an, welche Felder von der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) und [BP_REQUEST_INFO2 ](../../../extensibility/debugger/reference/bp-request-info2.md) Strukturen sind, initialisiert werden.  
  
 Diese Flags werden auch verwendet, um anzugeben, welche Felder von der `BP_REQUEST_INFO` und `BP_REQUEST_INFO2` Strukturen verwendet und gültig sind, wenn jede Struktur zurückgegeben wird.  
  
 Diese Werte können kombiniert werden, mit einem bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)