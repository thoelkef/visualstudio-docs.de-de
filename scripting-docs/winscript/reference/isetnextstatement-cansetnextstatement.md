---
title: 'Isetnextstatement:: cansetnextstatement | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 56cf0b2e4afd7a86a087b37be4b23758a5b59720
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571845"
---
# <a name="isetnextstatementcansetnextstatement"></a>ISetNextStatement::CanSetNextStatement
Diese Methode bestimmt, ob der Ausführungs Punkt, der die nächste auszuführende Code Anweisung bestimmt, auf den angegebenen Speicherort festgelegt werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT CanSetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### <a name="parameters"></a>Parameter  
 `pStackFrame`  
 in Zeiger auf ein Stapel Rahmen Objekt.  
  
 `pCodeContext`  
 in Zeiger auf ein Code Kontext Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die nächste Anweisung kann auf den angegebenen Code Kontext aktualisiert werden.|  
|`S_FALSE`|Die nächste Anweisung kann nicht in den angegebenen Code Kontext aktualisiert werden.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [ISetNextStatement-Schnittstelle](../../winscript/reference/isetnextstatement-interface.md)