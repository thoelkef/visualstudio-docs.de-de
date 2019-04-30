---
title: IActiveScriptSite::OnScriptTerminate | Microsoft-Dokumentation
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
ms.openlocfilehash: 664f974b26a2cae0d1e16d37dc3bc66e95993d6f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992652"
---
# <a name="iactivescriptsiteonscriptterminate"></a>IActiveScriptSite::OnScriptTerminate
Informiert den Host, dass das Skript die Ausführung abgeschlossen wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT OnScriptTerminate(  
    VARIANT *pvarResult,   // address of script results  
    EXCEPINFO *pexcepinfo  // address of structure with exception information  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pvarResult`  
 [in] Adresse einer Variablen, die das skriptergebnis enthält oder `NULL` Wenn das Skript kein Ergebnis erzeugt.  
  
 `pexcepinfo`  
 [in] Adresse von einem `EXCEPINFO` Struktur, die Informationen zur Ausnahme generiert, wenn das Skript beendet wird, enthält oder `NULL` , wenn keine Ausnahme ausgelöst wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück.  
  
## <a name="remarks"></a>Hinweise  
 Die Skript-Engine ruft diese Methode vor dem Aufruf der [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) Methode, mit festgelegtem Flag SCRIPTSTATE_INITIALIZED abgeschlossen ist. Diese Methode kann verwendet werden, um den Abschlussstatus und die Ergebnisse an den Host zurückzugeben. Beachten Sie, dass viele Skriptsprachen, die auf das Auffangen von Ereignissen vom Host basieren, Leben Spannen, die vom Host definiert sind. In diesem Fall kann diese Methode nie aufgerufen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)