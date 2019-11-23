---
title: 'IActiveScript:: setscriptstate | Microsoft-Dokumentation'
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
ms.openlocfilehash: ea947e00ffd5a3498261f4a3a8acd4791e8ace60
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577991"
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
Versetzt die Skript-Engine in den angegebenen Zustand. Diese Methode kann von nicht basisthreads aus aufgerufen werden, ohne dass ein Aufruf von Objekten oder die [iactivescriptsite](../../winscript/reference/iactivescriptsite.md) -Schnittstelle durchgeführt werden soll.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ss`  
 in Legt die Skript-Engine auf den angegebenen Zustand fest. Kann einer der Werte sein, die in der [ScriptState](../../winscript/reference/scriptstate-enumeration.md) -enumerationsenumeration definiert sind.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_FAIL`|Die Skript-Engine unterstützt den Übergang nicht in den initialisierten Zustand. Der Host muss diese Skript-Engine verwerfen und eine neue Skript-Engine erstellen, initialisieren und laden, um denselben Effekt zu erzielen.|  
|`E_UNEXPECTED`|Der-Befehl wurde nicht erwartet (z. b. wurde die Skript-Engine noch nicht geladen oder initialisiert) und ist daher fehlgeschlagen.|  
|`OLESCRIPT_S_PENDING`|Die Methode wurde erfolgreich in die Warteschlange eingereiht, aber der Zustand wurde noch nicht geändert. Wenn sich der Status ändert, wird die Website über die [iactivescriptsite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) -Methode zurückgerufen.|  
|`S_FALSE`|Die Methode war erfolgreich, das Skript war jedoch bereits im angegebenen Zustand.|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu den Status der Skript-Engine finden Sie im Abschnitt Skript-Engine-Zustände von [Windows Script Engines](../../winscript/windows-script-engines.md) .  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)