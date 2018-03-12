---
title: IActiveScript::InterruptScriptThread | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.InterruptScriptThread
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_InterruptScriptThread
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad717ee950dda4f0f0d7a14292f0f5f150ab4973
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
Unterbricht die Ausführung von einem ausgeführten Skriptthread (eine Ereignissenke, eine unmittelbare Ausführung oder einen Makroaufruf). Diese Methode kann verwendet werden, um ein Skript zu beenden, die (z. B. in einer Endlosschleife) festsitzt. Kann ohne eine Legende nicht zur Basis Hostobjekte oder in von nicht-Base-Threads aufgerufen werden der [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) Methode.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `stidThread`  
 [in] Der Bezeichner des Threads, die Interrupts oder einer der folgenden speziellen Thread-ID-Werte:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|Alle Threads. Die Unterbrechung wird für alle Skriptmethoden gleichzeitig in Verarbeitung befindlichen angewendet. Beachten Sie, dass, wenn der Aufrufer angefordert hat, dass das Skript getrennt werden, das nächste Skript Ereignis den Code erneut ausführen, durch den Aufruf bewirkt, dass die [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) Methode mit dem SCRIPTSTATE_DISCONNECTED oder SCRIPTSTATE_INITIALIZED-Flag festgelegt.|  
|SCRIPTTHREADID_BASE|Die Basis-Thread. d. h. wurde der Thread, in dem das Skript-engine-instanziiert.|  
|SCRIPTTHREADID_CURRENT|Den gerade ausgeführten Thread.|  
  
 `pexcepinfo`  
 [in] Der Adresse einer `EXCEPINFO` Struktur, enthält die Fehlerinformationen, die an der abgebrochenen Skript gemeldet werden sollte.  
  
 `dwFlags`  
 [in] Optionsflags für die Unterbrechung zugeordnet. Einer der folgenden Werte ist möglich:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|Wenn unterstützt, geben Sie das Skriptmodul-Debugger an den aktuellen Ausführungspunkt in Skript aus.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|Wenn das Skriptmodul Sprache unterstützt, können Sie das Skript, das die Ausnahme zu behandeln. Andernfalls Skriptmethode wird abgebrochen, und der Fehlercode an den Aufrufer zurückgegeben wird; d. h. Ereignis Quelle oder das Makro Invoker.|  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. das Skriptmodul wurde noch kein geladen oder initialisiert).|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)