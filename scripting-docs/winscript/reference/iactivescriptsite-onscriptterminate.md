---
title: IActiveScriptSite::OnScriptTerminate | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: eef8bd2a3f2e2a4eb4fd4b5f0e35fcd9acfe5bc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724800"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
Benachrichtigt den Host aus, dass das Skript die Ausführung abgeschlossen wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pvarResult`  
 [in] Adresse einer Variablen, die das skriptergebnis enthält oder `NULL` , wenn das Skript kein Ergebnis erzeugt.  
  
 `pexcepinfo`  
 [in] Adresse der ein `EXCEPINFO` -Struktur, die Informationen zur Ausnahme generiert, wenn das Skript beendet wird, enthält oder `NULL` , wenn keine Ausnahme ausgelöst wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück.  
  
## <a name="remarks"></a>Hinweise  
 Das Skriptmodul ruft diese Methode vor dem Aufruf der [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) Methode, die SCRIPTSTATE_INITIALIZED Flag festgelegt ist, abgeschlossen ist. Diese Methode kann verwendet werden, um Abschlussstatus sowie die Ergebnisse an den Host zurückzugeben. Beachten Sie, dass viele Skriptsprachen, die auf Auffangen von Ereignissen vom Host basieren, Lebensdauer haben, die vom Host definiert sind. In diesem Fall wird diese Methode kann nie aufgerufen.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)