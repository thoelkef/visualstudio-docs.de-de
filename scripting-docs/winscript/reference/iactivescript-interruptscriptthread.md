---
title: 'IActiveScript:: Interruptscriptthread | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.InterruptScriptThread
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_InterruptScriptThread
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa46bc95087b3defaf739cc3473c58e29a93071c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155929"
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
Unterbricht die Ausführung einen ausgeführten Skriptthread (eine Ereignissenke, eine unmittelbare Ausführung oder einem Makroaufruf). Diese Methode kann verwendet werden, um ein Skript zu beenden, die (z. B. in einer Endlosschleife) gebunden ist. Kann ohne eine Legende nicht zur Basis, auf dem Host-Objekte oder von nicht-Base Threads aufgerufen werden die [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) Methode.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `stidThread`  
 [in] Die ID des Threads, um den Interrupt oder eine der folgenden speziellen Thread-ID-Werte:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|Alle Threads. Die Unterbrechung wird auf alle Skriptmethoden gerade angewendet. Beachten Sie, dass, wenn der Aufrufer angefordert hat, dass das Skript getrennt werden, das nächste Skript Ereignis Serverskript-Code erneut ausführen durch den Aufruf bewirkt, dass die [IActiveScript:: Setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md) -Methode mit dem SCRIPTSTATE_DISCONNECTED oder SCRIPTSTATE_INITIALIZED-Flag festlegen.|  
|SCRIPTTHREADID_BASE|Die Basis-Thread. instanziiert wurde, also die in dem der Skript-Engine-Threads.|  
|SCRIPTTHREADID_CURRENT|Der aktuell ausgeführten Thread.|  
  
 `pexcepinfo`  
 [in] Adresse von einem `EXCEPINFO` Struktur, die mit den Fehlerinformationen, die an das Skript abgebrochenen gemeldet werden sollen.  
  
 `dwFlags`  
 [in] Flags, die über diese Unterbrechung-Option. Einer der folgenden Werte ist möglich:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|Wenn unterstützt, geben Sie die Skript-Engine-Debugger am aktuellen Ausführungspunkt Skript aus.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|Wenn von der Skript-Engine-Sprache unterstützt wird, können Sie das Skript die Ausnahme zu behandeln. Andernfalls die Skriptmethode wird abgebrochen, und der Fehlercode an den Aufrufer zurückgegeben wird; d. h. die Ereignis Quelle oder das Makro aufrufende Instanz.|  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. die Skript-Engine wurde noch nicht wurden geladen oder initialisiert).|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)