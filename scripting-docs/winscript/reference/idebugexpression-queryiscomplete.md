---
title: 'Idebugexpression:: queryiscomplete | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.QueryIsComplete
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::QueryIsComplete
ms.assetid: 510d62e5-a316-46fb-b23f-d3ba902b295c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c260ac5c02052f11f70e479588d65b71b4971267
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571974"
---
# <a name="idebugexpressionqueryiscomplete"></a>IDebugExpression::QueryIsComplete
Bestimmt, ob der Vorgang beendet ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT QueryIsComplete();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode nimmt keine Parameter an.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode wurde erfolgreich ausgeführt, und der Vorgang ist abgeschlossen.|  
|`S_FALSE`|Der Vorgang steht noch aus.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode bestimmt, ob der Vorgang beendet ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpression-Schnittstelle](../../winscript/reference/idebugexpression-interface.md)