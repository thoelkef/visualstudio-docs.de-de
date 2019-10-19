---
title: 'Ienumdebugcodekontexte:: Next | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugCodeContexts.Next
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugCodeContexts::Next
ms.assetid: 844cc353-ae0b-45e1-84a6-32b0bb67f57f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 289085265f182ec0fafca27a2cc18e8865b98091
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577176"
---
# <a name="ienumdebugcodecontextsnext"></a>IEnumDebugCodeContexts::Next
Ruft eine angegebene Anzahl von Segmenten in der enumerationssequenz ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Next(  
   ULONG                celt,  
   IDebugCodeContext**  pscc,  
   ULONG*               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 in Die Anzahl der abzurufenden Segmente.  
  
 `pscc`  
 vorgenommen Gibt ein Array von `IDebugCodeContext`-Schnittstellen zurück, die die abgerufenen Segmente darstellen.  
  
 `pceltFetched`  
 vorgenommen Die tatsächliche Anzahl der Segmente, die vom Enumerator abgerufen wurden.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ruft eine angegebene Anzahl von Segmenten in der enumerationssequenz ab.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugCodeContexts-Schnittstelle](../../winscript/reference/ienumdebugcodecontexts-interface.md)