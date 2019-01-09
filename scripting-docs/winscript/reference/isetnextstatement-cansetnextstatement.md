---
title: ISetNextStatement::CanSetNextStatement | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISetNextStatement.CanSetNextStatement
apilocation:
- scrobj.dll
ms.assetid: e2a54634-31ec-4d16-84e8-2b123845d876
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5288b0cffc3b8bfca0e995e67d4b3e4bf3a6b2e2
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090128"
---
# <a name="isetnextstatementcansetnextstatement"></a>ISetNextStatement::CanSetNextStatement
Diese Methode bestimmt, ob es sich bei der Ausführungspunkt an, der bestimmt, die nächste Anweisung des Codes ausgeführt werden, auf der angegebenen Position festgelegt werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT CanSetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### <a name="parameters"></a>Parameter  
 `pStackFrame`  
 [in] Zeiger auf ein.  
  
 `pCodeContext`  
 [in] Zeiger auf ein Code-Context-Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die nächste Anweisung kann auf den angegebenen Kontext aktualisiert werden.|  
|`S_FALSE`|Die nächste Anweisung kann nicht auf den angegebenen Kontext aktualisiert werden.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [ISetNextStatement-Schnittstelle](../../winscript/reference/isetnextstatement-interface.md)