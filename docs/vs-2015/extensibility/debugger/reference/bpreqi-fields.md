---
title: BPREQI_FIELDS | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a8ad9e4b6d83ebc05c78a8b84c0c06e00d7563bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153229"
---
# <a name="bpreqi_fields"></a>BPREQI_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt die Informationen an, die über eine Breakpoint-Anforderung abgerufen werden sollen.  
  
## <a name="syntax"></a>Syntax  
  
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
  
```csharp  
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
  
## <a name="members"></a>Member  
 BPREQI_BPLOCATION  
 Initialisieren/verwenden Sie das `bpLocation` Feld (breakpointposition) der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) -oder [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Struktur.  
  
 BPREQI_LANGUAGE  
 Initialisieren/verwenden Sie das- `guidLanguage` Feld der- `BP_REQUEST_INFO` oder- `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI_PROGRAM  
 Initialisieren/verwenden Sie das- `pProgram` Feld der- `BP_REQUEST_INFO` oder- `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI_PROGRAMNAME  
 Initialisieren/verwenden Sie das- `bstrProgramName` Feld der- `BP_REQUEST_INFO` oder- `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI_THREAD  
 Initialisieren/verwenden Sie das- `pThread` Feld der- `BP_REQUEST_INFO` oder- `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI_THREADNAME  
 Initialisieren/verwenden Sie das- `bstrThreadName` Feld der- `BP_REQUEST_INFO` oder- `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI_PASSCOUNT  
 Initialisieren/verwenden Sie das- `bpPassCount` Feld der- `BP_REQUEST_INFO` oder- `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI_CONDITION  
 Initialisieren/verwenden Sie das `bpCondition` Feld (breakpointbedingung) der- `BP_REQUEST_INFO` oder- `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI_FLAGS  
 Initialisieren/verwenden Sie das- `dwFlags` Feld der- `BP_REQUEST_INFO` oder- `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI_ALLOLDFIELDS  
 Initialisieren/verwenden Sie alle Felder für den der- `BP_REQUEST_INFO` Struktur.  
  
 BPREQI_VENDOR  
 Initialisieren/verwenden Sie das `guidVendor` Feld der- `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI_CONSTRAINT  
 Initialisieren/verwenden Sie das `bstrConstraint` Feld der- `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI_TRACEPOINT  
 Initialisieren/verwenden Sie das `bstrTracepoint` Feld der- `BP_REQUEST_INFO2` Struktur.  
  
 BPREQI_ALLFIELDS  
 Gibt alle Felder für die `BP_REQUEST_INFO2` Struktur an.  
  
## <a name="remarks"></a>Bemerkungen  
 Wird als Argument an die Methoden [getrequestinfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) und [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) übermittelt, um anzugeben, welche Felder der [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) und [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Strukturen initialisiert werden sollen.  
  
 Diese Flags werden auch verwendet, um anzugeben, welche Felder der `BP_REQUEST_INFO` -und- `BP_REQUEST_INFO2` Strukturen verwendet und gültig sind, wenn jede Struktur zurückgegeben wird.  
  
 Diese Werte können mit einem bitweisen kombiniert werden `OR` .  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Getrequestinfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
