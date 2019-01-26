---
title: BP_RESOLUTION_DATA | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03a269dad8b282707bf4087b8f97fb570a8959cd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54960229"
---
# <a name="bpresolutiondata"></a>BP_RESOLUTION_DATA
Beschreibt das Ergebnis der Bindung eines Haltepunkts für Daten.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _BP_RESOLUTION_DATA {   
   BSTR              bstrDataExpr;  
   BSTR              bstrFunc;  
   BSTR              bstrImage;  
   BP_RES_DATA_FLAGS dwFlags;  
} BP_RESOLUTION_DATA;  
```  
  
```csharp  
public struct BP_RESOLUTION_DATA {   
   public string bstrDataExpr;  
   public string bstrFunc;  
   public string bstrImage;  
   public uint   dwFlags;  
};  
```  
  
## <a name="members"></a>Member  
 `bstrDataExpr`  
 Die Datenausdruck, der gebunden wurde.  
  
 `bstrFunc`  
 Der Name der Funktion hat der Datenhaltepunkt in (sofern vorhanden) gebunden.  
  
 `bstrImage`  
 Der Name des Moduls (z. B. MyModule.dll), das in der Datenhaltepunkt gebunden ist.  
  
 `dwFlags`  
 Ein Wert aus der [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) Enumeration, die beschreibt, wie der Datenhaltepunkt implementiert wird.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur ist ein Mitglied der [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) -Struktur, die in ein Mitglied zu aktivieren ist die [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) vom zurückgegebene Struktur der [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)Methode.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)