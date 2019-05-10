---
title: 'IActiveScript:: Setscriptstate | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.SetScriptState
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_SetScriptState
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16a13b545ddd482f8aa143d289d46447370e23ac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935530"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
Setzt das Skriptmodul in den angegebenen Zustand. Diese Methode kann von nicht-Base Threads aufgerufen werden, ohne dass eine nicht-Base-Legende Hostobjekte oder in der [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) Schnittstelle.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ss`  
 [in] Legt die Skript-Engine auf den angegebenen Zustand fest. Kann eine der in definierten Werte der [SCRIPTSTATE-Enumeration](../../winscript/reference/scriptstate-enumeration.md) Enumeration.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_FAIL`|Die Skript-Engine unterstützt nicht den Übergang zurück zum initialisierten Zustand. Der Host muss dieses Skript-Engine zu verwerfen und erstellen, initialisieren und Laden eine neue Skript-Engine, um den gleichen Effekt zu erzielen.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. die Skript-Engine wurde noch nicht wurden geladen oder initialisiert) und aus diesem Grund fehlgeschlagen ist.|  
|`OLESCRIPT_S_PENDING`|Die Methode wurde in die Warteschlange erfolgreich, jedoch der Zustand noch nicht geändert wurde. Wenn die Änderungen des Ansichtszustands des Standorts erneut aufgerufen über das [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) Methode.|  
|`S_FALSE`|Die Methode erfolgreich ausgeführt, aber das Skript wurde bereits im angegebenen Zustand.|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zur Skripterstellung für Engine-Status finden Sie im Abschnitt "Skriptmodulzustände" der [Windows Script-Engines](../../winscript/windows-script-engines.md) .  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)