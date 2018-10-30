---
title: BPERESI_FIELDS | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a9530e950ddd5dbf75fb10b5391dc658bdf899fc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49869937"
---
# <a name="bperesifields"></a>BPERESI_FIELDS
Gibt die Informationen zu einer fehlerhaften Auflösung eines Haltepunkts abgerufen werden sollen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
typedef DWORD BPERESI_FIELDS;  
```  
  
```csharp  
public enum enum_BPERESI_FIELDS {   
   PERESI_BPRESLOCATION = 0x0001,  
   BPERESI_PROGRAM      = 0x0002,  
   BPERESI_THREAD       = 0x0004,  
   BPERESI_MESSAGE      = 0x0008,  
   BPERESI_TYPE         = 0x0010,  
   BPERESI_ALLFIELDS    = 0xffffffff  
};  
```  
  
## <a name="members"></a>Member  
 PERESI_BPRESLOCATION  
 Initialisieren und Verwenden der `bpResLocation` (Position des Haltepunkts Auflösung) Feld der [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) Struktur.  
  
 BPERESI_PROGRAM  
 Initialisieren und Verwenden der `pProgram` Feld der `BP_ERROR_RESOLUTION_INFO` Struktur.  
  
 BPERESI_THREAD  
 Initialisieren und Verwenden der `pThread` Feld der `BP_ERROR_RESOLUTION_INFO` Struktur.  
  
 BPERESI_MESSAGE  
 Initialisieren und Verwenden der `bstrMessage` Feld der `BP_ERROR_RESOLUTION_INFO` Struktur.  
  
 BPERESI_TYPE  
 Initialisieren und Verwenden der `dwType` (Haltepunkt) Typfeld der `BP_ERROR_RESOLUTION_INFO` Struktur.  
  
 BPERESI_ALLFIELDS  
 Alle Felder initialisiert und Verwenden der `BP_ERROR_RESOLUTION_INFO` Struktur.  
  
## <a name="remarks"></a>Hinweise  
 Übergeben als Parameter an die [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) Methode, um die Felder anzugeben der [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) sind, dass die Struktur initialisiert werden.  
  
 Diese Werte werden auch verwendet, um anzugeben, welche Felder in der `BP_ERROR_RESOLUTION_INFO` -Struktur sind gültig und verwendet, wenn dieser Struktur zurückgegeben wird.  
  
 Diese Werte können kombiniert werden, mit einer bitweisen `OR`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)