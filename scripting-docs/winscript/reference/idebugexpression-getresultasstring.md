---
title: IDebugExpression::GetResultAsString | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsString
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 84255e364630245564a0cbab5d38c6dff38df0a8
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146590"
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
Gibt das Ergebnis der Auswertung des Ausdrucks als eine Zeichenfolge und der Rückgabewert des Vorgangs zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `phrResult`  
 [out] Der Rückgabewert des Vorgangs.  
  
 `pbstrResult`  
 [out] Das Ergebnis der ausdrucksauswertung.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_PENDING`|Der Vorgang ist noch ausstehend.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt das Ergebnis der Auswertung des Ausdrucks als eine Zeichenfolge und des Vorgangs zurück `HRESULT`.  
  
 Diese Methode gibt `S_OK` und `phrResult` gibt `E_ABORT` Wenn `Abort` bricht den Vorgang ab.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpression-Schnittstelle](../../winscript/reference/idebugexpression-interface.md)