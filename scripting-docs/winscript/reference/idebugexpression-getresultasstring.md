---
title: 'Idebugexpression:: getresultasstring | Microsoft-Dokumentation'
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
ms.openlocfilehash: 56b8f637744227763f55b7c024745d7ae4448b40
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573524"
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
Gibt das Ergebnis der Ausdrucks Auswertung als Zeichenfolge und den Rückgabewert des Vorgangs zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `phrResult`  
 vorgenommen Der Rückgabewert des Vorgangs.  
  
 `pbstrResult`  
 vorgenommen Das Ergebnis der Ausdrucks Auswertung.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_PENDING`|Der Vorgang steht noch aus.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt das Ergebnis der Ausdrucks Auswertung als Zeichenfolge und den `HRESULT` des Vorgangs zurück.  
  
 Diese Methode gibt `S_OK` zurück, und `phrResult` gibt `E_ABORT` zurück, wenn `Abort` den Vorgang abbricht.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpression-Schnittstelle](../../winscript/reference/idebugexpression-interface.md)