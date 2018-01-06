---
title: BP_LOCATION_DATA_STRING | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_LOCATION_DATA_STRING
helpviewer_keywords: BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 98be0e0eec66d1829569f88b38f710ddc616be85
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="bplocationdatastring"></a>BP_LOCATION_DATA_STRING
Verwendet zum Festlegen von datenbreakpoints, die auf eine Zeichenfolge, die der Benutzer die integrierte Entwicklungsumgebung (IDE) eingeben können.  
  
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
 Die [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) -Objekt, das den Thread darstellt, auf der der Breakpoint auftritt.  
  
 `bstrContext`  
 Im Rahmen der Haltepunkt im Code, in der Regel eine Methode oder Funktion Namen wie in einer Aufrufliste angezeigt.  
  
 `bstrDataExpr`  
 Zeichenfolge mit den Daten der Benutzer eingibt, um den Haltepunkt festzulegen.  
  
 `dwNumElements`  
 Die Anzahl der Elemente in der Datenzeichenfolge, die in der sich der Breakpoint auftritt.  
  
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