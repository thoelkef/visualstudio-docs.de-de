---
title: 'Idebugexpression:: getresultasdebug-Eigenschaft | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsDebugProperty
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsDebugProperty
ms.assetid: 9075bf2f-d5bb-464e-b6c2-3fa3215e9ae0
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 104c42f02d02be386711e687f02d333425834948
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575928"
---
# <a name="idebugexpressiongetresultasdebugproperty"></a>IDebugExpression::GetResultAsDebugProperty
Gibt das Ergebnis der Ausdrucks Auswertung als Debugeigenschaft und den Rückgabewert des Vorgangs zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetResultAsDebugProperty(  
   HRESULT*          phrResult,  
   IDebugProperty**  ppdp  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `phrResult`  
 vorgenommen Der Rückgabewert des Vorgangs.  
  
 `ppdp`  
 vorgenommen Die Debug-Eigenschaft für den Ausdruck.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_PENDING`|Der Vorgang steht noch aus.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt das Ergebnis der Ausdrucks Auswertung als `IDebugProperty` und die `HRESULT` des Vorgangs zurück.  
  
 Diese Methode gibt `S_OK` zurück, und `phrResult` gibt `E_ABORT` zurück, wenn `Abort` den Vorgang abbricht.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugexpression-Schnittstelle](../../winscript/reference/idebugexpression-interface.md)    
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)