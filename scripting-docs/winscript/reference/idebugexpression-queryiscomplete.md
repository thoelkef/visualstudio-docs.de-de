---
title: IDebugExpression::QueryIsComplete | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 0b4fa4b027f0ee8d848f52c063cbfd1f7679d4a6
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087151"
---
# <a name="idebugexpressionqueryiscomplete"></a>IDebugExpression::QueryIsComplete
Bestimmt, ob der Vorgang abgeschlossen ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT QueryIsComplete();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode akzeptiert keine Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode erfolgreich war, und der Vorgang abgeschlossen ist.|  
|`S_FALSE`|Der Vorgang ist noch ausstehend.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode wird bestimmt, ob der Vorgang abgeschlossen ist.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpression-Schnittstelle](../../winscript/reference/idebugexpression-interface.md)