---
title: IDebugExpression::Start | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 2c0d7b809f18407bfeb3de59c9cbb6e6e26911ad
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093339"
---
# <a name="idebugexpressionstart"></a>IDebugExpression::Start
Beginnt die Auswertung des Ausdrucks an.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdecb`  
 [in] Rückruf für den, der angibt, wenn die Auswertung des Ausdrucks abgeschlossen ist. Wenn dieser Parameter ist `NULL`, werden keine Ereignisse ausgelöst, und der Client muss den Zustand des Abfrageausdrucks mithilfe von Abfragen `QueryIsComplete`.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode beginnt die Auswertung des Ausdrucks.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)   
 [IDebugExpression-Schnittstelle](../../winscript/reference/idebugexpression-interface.md)