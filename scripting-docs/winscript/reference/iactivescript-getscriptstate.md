---
title: IActiveScript::GetScriptState | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a64067679e1c56831002494c579ffdeba84a1abe
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096576"
---
# <a name="iactivescriptgetscriptstate"></a>IActiveScript::GetScriptState
Ruft den aktuellen Status des verwendeten Skriptmoduls ab. Diese Methode kann von nicht-Base Threads aufgerufen werden, ohne dass eine nicht-Base-Legende Hostobjekte oder in der [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) Schnittstelle.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pss`  
 [out] Adresse einer Variablen, die einen Wert im definierten empfängt die [SCRIPTSTATE-Enumeration](../../winscript/reference/scriptstate-enumeration.md) Enumeration. Der Wert gibt den aktuellen Zustand der Skript-Engine den aufrufenden Thread zugeordnet.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` im Erfolgsfall oder `E_POINTER` Wenn ein ungültiger Zeiger angegeben wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)