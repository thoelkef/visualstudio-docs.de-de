---
title: BP_LOCATION_DATA_STRING | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 58e1e5d4a390b24fdb1c718d3ebd4e9d2479b189
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040709"
---
# <a name="bplocationdatastring"></a>BP_LOCATION_DATA_STRING
Verwendet zum Festlegen von datenbreakpoints, die auf eine Zeichenfolge basieren, die der Benutzer aus der integrierten Entwicklungsumgebung (IDE) eingeben können.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _BP_LOCATION_DATA_STRING {   
   IDebugThread2* pThread;  
   BSTR           bstrContext;  
   BSTR           bstrDataExpr;  
   DWORD          dwNumElements;  
} BP_LOCATION_DATA_STRING;  
```  
  
## <a name="members"></a>Member  
 `pThread`  
 Die [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den Thread darstellt, an dem der Haltepunkt wird.  
  
 `bstrContext`  
 Der Kontext der der Haltepunkt im Code, in der Regel eine Methode oder Funktion Namen wie für eine Aufrufliste.  
  
 `bstrDataExpr`  
 Die Zeichenfolge gibt der Benutzer, um den Haltepunkt festzulegen.  
  
 `dwNumElements`  
 Die Anzahl der Elemente in der Datenzeichenfolge, die in der der Breakpoint auftritt.  
  
## <a name="remarks"></a>Hinweise  
 Diese Struktur ist ein Mitglied der [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Struktur als Teil einer Union.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)