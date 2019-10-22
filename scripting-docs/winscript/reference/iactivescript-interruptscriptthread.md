---
title: 'IActiveScript:: interruptscriptthread | Microsoft-Dokumentation'
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
ms.openlocfilehash: a436f973df05b945c0939f3a593640f567774277
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577270"
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
Unterbricht die Ausführung eines laufenden Skript Threads (eine Ereignis Senke, eine sofortige Ausführung oder ein Makro Aufruf). Diese Methode kann verwendet werden, um ein Skript zu beenden, das hängen bleibt (z. b. in einer Endlosschleife). Sie kann von nicht basisthreads aus aufgerufen werden, ohne dass dies zu einer nicht Basis Legenden Aufruf von Objekten oder der [iactivescriptsite](../../winscript/reference/iactivescriptsite.md) -Methode führt.  
  
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
 in Der Bezeichner des Threads, der unterbrochen werden soll, oder einer der folgenden speziellen Thread-Bezeichnerwerte:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|Alle Threads. Der Interrupt wird auf alle zurzeit ausgeführten Skript Methoden angewendet. Beachten Sie Folgendes: Wenn der Aufrufer nicht angefordert hat, dass das Skript getrennt wird, bewirkt das nächste Skript-Ereignis, dass der Skriptcode durch Aufrufen der [IActiveScript:: setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md) -Methode mit dem SCRIPTSTATE_DISCONNECTED-oder SCRIPTSTATE_INITIALIZED-Flag erneut ausgeführt wird. Set.|  
|SCRIPTTHREADID_BASE|Der Basis Thread. Das heißt, der Thread, in dem die Skript-Engine instanziiert wurde.|  
|SCRIPTTHREADID_CURRENT|Der derzeit ausgeführte Thread.|  
  
 `pexcepinfo`  
 in Adresse einer `EXCEPINFO`-Struktur, die die Fehlerinformationen enthält, die dem abgebrochenen Skript gemeldet werden sollen.  
  
 `dwFlags`  
 in Optionsflags, die mit der Unterbrechung verknüpft sind. Einer der folgenden Werte ist möglich:  
  
|Wert|Bedeutung|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|Wenn unterstützt, geben Sie den Debugger der Skript-Engine auf dem aktuellen Skript Ausführungs Punkt ein.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|Wenn Sie von der Sprache der Skript-Engine unterstützt wird, lassen Sie das Skript die Ausnahme verarbeiten. Andernfalls wird die Skript Methode abgebrochen und der Fehlercode an den Aufrufer zurückgegeben. Das heißt, die Ereignis Quelle oder der makroinvoker.|  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_INVALIDARG`|Ein Argument war ungültig.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der-Befehl wurde nicht erwartet (z. b. wurde die Skript-Engine noch nicht geladen oder initialisiert).|  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)