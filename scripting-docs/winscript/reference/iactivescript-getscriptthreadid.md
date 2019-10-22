---
title: 'IActiveScript:: getscriptthreadid | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptThreadID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptThreadID
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a0fb1eebfcb6ed100056289fab6bce662f86a7b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575703"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
Ruft einen von der Skript-Engine definierten Bezeichner für den Thread ab, der dem angegebenen Win32-Thread zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwWin32ThreadID` ,  
 in Thread Bezeichner eines laufenden Win32-Threads im aktuellen Prozess. Verwenden Sie die [IActiveScript:: getcurrentscriptthreadid](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) -Funktion, um den Thread Bezeichner des aktuell ausgeführten Threads abzurufen.  
  
 `pstidThread` ,  
 vorgenommen Adresse einer Variablen, die den dem angegebenen Win32-Thread zugeordneten Skript Thread Bezeichner empfängt. Die Interpretation dieses Bezeichners wird der Skript-Engine überlassen, aber es kann sich lediglich um eine Kopie der Windows-Thread Kennung handeln. Beachten Sie, dass dieser Bezeichner, wenn der Win32-Thread beendet wird, nicht zugewiesen und anschließend einem anderen Thread zugewiesen werden kann.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der-Befehl wurde nicht erwartet (z. b. wurde die Skript-Engine noch nicht geladen oder initialisiert) und ist daher fehlgeschlagen.|  
  
## <a name="remarks"></a>Hinweise  
 Der abgerufene Bezeichner kann in nachfolgenden Aufrufen von Skript Ausführungs Steuerungsmethoden wie z. b. der [IActiveScript:: interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md) -Methode verwendet werden.  
  
 Diese Methode kann von nicht basisthreads aus aufgerufen werden, ohne dass eine nicht-Basis Legende zum Hosten von Objekten oder zur [IActiveScript:: interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md) -Schnittstelle verwendet wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)