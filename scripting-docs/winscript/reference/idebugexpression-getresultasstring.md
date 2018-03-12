---
title: IDebugExpression::GetResultAsString | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsString
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 557fe65859d1e3046d64884982070ad233e12559
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
Gibt das Ergebnis der Auswertung von Ausdrücken als eine Zeichenfolge und der Rückgabewert des Vorgangs zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `phrResult`  
 [out] Der Rückgabewert des Vorgangs.  
  
 `pbstrResult`  
 [out] Das Ergebnis der Auswertung von Ausdrücken.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_PENDING`|Der Vorgang ist noch ausstehend.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt das Ergebnis der Auswertung von Ausdrücken als eine Zeichenfolge und des Vorgangs `HRESULT`.  
  
 Diese Methode gibt `S_OK` und `phrResult` gibt `E_ABORT` Wenn `Abort` bricht den Vorgang ab.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpression-Schnittstelle](../../winscript/reference/idebugexpression-interface.md)