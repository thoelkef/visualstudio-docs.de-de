---
title: IActiveScript::SetScriptState | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.SetScriptState
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_SetScriptState
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 146cd5e4f2b6137fc6fe6e32e8ca153c3aab8fd5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsetscriptstate"></a>IActiveScript::SetScriptState
Setzt das Skriptmodul in den angegebenen Zustand übergeht. Diese Methode kann von nicht zur Basis Threads aufgerufen werden, ohne dass eine Legende nicht zur Basis Hostobjekte oder in der [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) Schnittstelle.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ss`  
 [in] Legt das Skriptmodul in den angegebenen Zustand fest. Kann einen der Werte in definiert die [SCRIPTSTATE-Enumeration](../../winscript/reference/scriptstate-enumeration.md) Enumeration.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_FAIL`|Das Skriptmodul unterstützt nicht den Übergang zurück zum initialisierten Zustand. Der Host muss dieser Skriptmodul verwerfen und erstellen, initialisieren und Laden ein neue Skriptmodul um denselben Effekt zu erzielen.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. das Skriptmodul wurde noch kein geladen oder initialisiert) und konnte daher nicht.|  
|`OLESCRIPT_S_PENDING`|Die Methode wurde in die Warteschlange wurde erfolgreich, jedoch der Zustand noch nicht geändert wurde. Wenn die statusänderungen die Website wird zurückrufen durch die [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) Methode.|  
|`S_FALSE`|Die Methode war erfolgreich, aber das Skript wurde bereits dem angegebenen Status.|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zur Skripterstellung für Datenbankmodul-Status finden Sie im Abschnitt "Skript Datenbankmodul-Status" des [Windows Script-Module](../../winscript/windows-script-engines.md) .  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)