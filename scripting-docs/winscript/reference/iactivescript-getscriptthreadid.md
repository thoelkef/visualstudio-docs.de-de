---
title: IActiveScript::GetScriptThreadID | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 8850319035b7b5e3a9cbbd4bbe4340e1eefacc96
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641610"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
Ruft einen scripting-Engine-definierten Bezeichner für den Thread, der dem angegebenen Win32-Thread zugeordnet.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwWin32ThreadID` ,  
 [in] Thread-ID eines ausgeführten Win32-Threads im aktuellen Prozess. Verwenden der [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) -Funktion zum Abrufen des Threadbezeichner des aktuell ausgeführten Threads.  
  
 `pstidThread` ,  
 [out] Die Adresse einer Variablen, die die angegebenen Win32-Thread zugeordneten Skript Threadbezeichner empfängt. Die Interpretation dieser Bezeichner obliegt dem Skriptmodul, aber es kann nur eine Kopie des Windows-Thread-ID sein. Beachten Sie, dass wenn der Win32-Thread beendet wird, wird dieser Bezeichner nicht zugewiesen wird und anschließend an einen anderen Thread zugewiesen sein.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. das Skriptmodul wurde noch kein geladen oder initialisiert) und konnte daher nicht.|  
  
## <a name="remarks"></a>Hinweise  
 Der abgerufene Bezeichner kann z. B. bei nachfolgenden Funktionsaufrufen Skript Thread Steuerelement Ausführungsmethoden verwendet werden die [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) Methode.  
  
 Diese Methode kann von nicht zur Basis Threads aufgerufen werden, ohne dass eine Legende nicht zur Basis Hostobjekte oder in der [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)