---
title: IActiveScript::GetScriptThreadID | Microsoft-Dokumentation
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
ms.openlocfilehash: 7b1c68d60b827e7540711cdf6ba34260fb8642ed
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094873"
---
# <a name="iactivescriptgetscriptthreadid"></a>IActiveScript::GetScriptThreadID
Ruft ab eine scripting-Engine-definierten Bezeichner für den Thread, der dem angegebenen Win32-Thread zugeordnet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwWin32ThreadID` ,  
 [in] Thread-ID eines ausgeführten Win32-Threads im aktuellen Prozess. Verwenden der [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) Funktion, um den Threadbezeichner des aktuell ausgeführten Thread abzurufen.  
  
 `pstidThread` ,  
 [out] Die Adresse einer Variablen, die die dem angegebenen Win32-Thread zugeordneten Skript Threadbezeichner empfängt. Die Interpretation dieser Bezeichner ist die Skript-Engine überlassen, aber es kann nur eine Kopie der Windows-Thread-Bezeichner sein. Beachten Sie, dass wenn der Win32-Thread beendet wird, wird dieser Bezeichner nicht zugewiesen wird und anschließend zu einem anderen Thread zugewiesen werden kann.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen der folgenden Werte zurück:  
  
|Rückgabewert|Bedeutung|  
|------------------|-------------|  
|`S_OK`|Erfolgreich.|  
|`E_POINTER`|Es wurde ein ungültiger Zeiger angegeben.|  
|`E_UNEXPECTED`|Der Aufruf wurde nicht erwartet (z. B. die Skript-Engine wurde noch nicht wurden geladen oder initialisiert) und aus diesem Grund fehlgeschlagen ist.|  
  
## <a name="remarks"></a>Hinweise  
 Der abgerufene Bezeichner dienen bei nachfolgenden Aufrufen von Skripts Thread Ausführungsmethoden Steuerelement wie z. B. die [IActiveScript:: Interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md) Methode.  
  
 Diese Methode kann von nicht-Base Threads aufgerufen werden, ohne dass eine nicht-Base-Legende Hostobjekte oder in der [IActiveScript:: Interruptscriptthread](../../winscript/reference/iactivescript-interruptscriptthread.md) Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScript](../../winscript/reference/iactivescript.md)