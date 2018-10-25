---
title: BP_LOCATION_DATA_STRING | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 92fbda278b0e0c4f4ee5a39cc13f80b5fbd2bbb7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889086"
---
# <a name="bplocationdatastring"></a>BP_LOCATION_DATA_STRING
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Verwendet zum Festlegen von datenbreakpoints, die auf eine Zeichenfolge basieren, die der Benutzer aus der integrierten Entwicklungsumgebung (IDE) eingeben können.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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

