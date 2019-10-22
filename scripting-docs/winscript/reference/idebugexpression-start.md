---
title: 'Idebugexpression:: Start | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.Start
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::Start
ms.assetid: a7af3470-62b5-40f0-987d-63b6b22538b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1c8c3666adfc83f3ad60b942cd3f7fe9eedfccba
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576431"
---
# <a name="idebugexpressionstart"></a>IDebugExpression::Start
Beginnt die Auswertung des Ausdrucks.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdecb`  
 in Rückruf, der angibt, wann die Ausdrucks Auswertung beendet ist. Wenn dieser Parameter `NULL` ist, werden keine Ereignisse ausgelöst, und der Client muss den Ausdrucks Zustand mithilfe `QueryIsComplete` Abfragen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode beginnt mit der Auswertung des Ausdrucks.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugexpression:: Abort](../../winscript/reference/idebugexpression-abort.md)    
 [IDebugExpression-Schnittstelle](../../winscript/reference/idebugexpression-interface.md)