---
title: 'Ienumentbugstackframes:: Skip | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Skip
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Skip
ms.assetid: d893d6e9-e119-4f14-99d0-bf23dbd2d625
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29e5864d1304aeb4c916e93da8b151336596d979
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575539"
---
# <a name="ienumdebugstackframesskip"></a>IEnumDebugStackFrames::Skip
Überspringt eine angegebene Anzahl von Segmenten in einer enumerationssequenz.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 in Anzahl der zu über springenden Segmente in der enumerationssequenz.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode überspringt eine angegebene Anzahl von Segmenten in einer enumerationssequenz.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugStackFrames-Schnittstelle](../../winscript/reference/ienumdebugstackframes-interface.md)