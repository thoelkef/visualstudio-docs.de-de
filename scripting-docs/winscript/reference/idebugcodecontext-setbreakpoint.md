---
title: IDebugCodeContext::SetBreakPoint | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugCodeContext.SetBreakPoint
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugCodeContext::SetBreakPoint
ms.assetid: ecd42eae-66fa-40d3-9e47-08b826784108
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7bbfe38c1db9f7c9afff34f5a92b8c43b0f4f9ba
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974526"
---
# <a name="idebugcodecontextsetbreakpoint"></a>IDebugCodeContext::SetBreakPoint
Legt fest oder löscht einen Haltepunkt an diesem Codekontext.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SetBreakPoint(  
   BREAKPOINT_STATE  bps  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `bps`  
 [in] Gibt den Haltepunktzustand für diesen Codekontext.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode legt fest oder löscht einen Haltepunkt an diesem Codekontext.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugCodeContext-Schnittstelle](../../winscript/reference/idebugcodecontext-interface.md)   
 [BREAKPOINT_STATE-Enumeration](../../winscript/reference/breakpoint-state-enumeration.md)