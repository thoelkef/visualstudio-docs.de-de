---
title: 'Iactivescriptsite:: onscriptbeenden | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.OnScriptTerminate
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnScriptTerminate
ms.assetid: 3301ddf4-5929-404c-81d3-1a720e589008
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a715b39b07df4183d4ec542a1dd82b4229d1f41e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570205"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
Benachrichtigt den Host, dass die Ausführung des Skripts abgeschlossen ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pvarResult`  
 in Adresse einer Variablen, die das Skript Ergebnis enthält, oder `NULL`, wenn das Skript kein Ergebnis erzeugt hat.  
  
 `pexcepinfo`  
 in Die Adresse einer `EXCEPINFO` Struktur, die Ausnahme Informationen enthält, die bei Beendigung des Skripts generiert wurden, oder `NULL`, wenn keine Ausnahme generiert wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück.  
  
## <a name="remarks"></a>Hinweise  
 Die Skript-Engine ruft diese Methode auf, bevor der Aufruf der [iactivescriptsite:: OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) -Methode, bei der das SCRIPTSTATE_INITIALIZED-Flag festgelegt ist, abgeschlossen ist. Diese Methode kann verwendet werden, um den Abschluss Status und die Ergebnisse an den Host zurückzugeben. Beachten Sie, dass viele Skriptsprachen, die auf Sink-Ereignissen vom Host basieren, Überlebens spannen verfügen, die vom Host definiert werden. In diesem Fall wird diese Methode möglicherweise nie aufgerufen.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)