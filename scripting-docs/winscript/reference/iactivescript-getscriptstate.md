---
title: 'IActiveScript:: getscriptstate | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptState
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d266e713879aafe1c5ca271d46b3030f3275460f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575726"
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
Ruft den aktuellen Zustand der Skript-Engine ab. Diese Methode kann von nicht basisthreads aus aufgerufen werden, ohne dass ein Aufruf von Objekten oder die [iactivescriptsite](../../winscript/reference/iactivescriptsite.md) -Schnittstelle durchgeführt werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pss`  
 vorgenommen Adresse einer Variablen, die einen Wert empfängt, der in der [ScriptState-Enumeration](../../winscript/reference/scriptstate-enumeration.md) -Enumeration definiert ist. Der Wert gibt den aktuellen Zustand der Skript-Engine an, die dem aufrufenden Thread zugeordnet ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` zurück, wenn erfolgreich, oder `E_POINTER`, wenn ein ungültiger Zeiger angegeben wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)