---
title: IDebugApplication::HandleRuntimeError | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleRuntimeError
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleRuntimeError
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a457ba0dcc6fb7f8a95a982b6dabd93f9d0207e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150100"
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Bewirkt, dass den aktuelle Thread blockiert, und sendet eine Benachrichtigung über den Fehler an den Debugger-IDE.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT HandleRuntimeError(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   IActiveScriptSite*        pScriptSite,  
   BREAKRESUMEACTION*        pbra,  
   ERRORRESUMEACTION*        perra,  
   BOOL*                     pfCallOnScriptError  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pErrorDebug`  
 [in] Der Fehler, der aufgetreten sind.  
  
 `pScriptSite`  
 [in] Die skriptwebsite des Threads.  
  
 `pbra`  
 [out] Auszuführende Aktion, wenn der Debugger die Anwendung fortgesetzt wird.  
  
 `perra`  
 [out] Auszuführende Aktion, wenn der Debugger die Anwendung fortgesetzt wird, wenn ein Fehler auftritt.  
  
 `pfCallOnScriptError`  
 [out] Flag, das ist `TRUE` , wenn die Engine aufrufen soll die `IActiveScriptSite::OnScriptError` Methode.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Eine Sprach-Engine ruft diese Methode im Kontext eines Threads, der einen Laufzeitfehler auslöst. Diese Methode bewirkt, dass den aktuelle Thread blockiert und sendet eine Fehlermeldung angezeigt, die an der Debugger-IDE gesendet werden. Wenn der Debugger-IDE mit der Anwendung fortgesetzt wird, gibt diese Methode, mit der Aktion an, die ausgeführt werden.  
  
> [!NOTE]
>  In den Fehler zur Laufzeit kann die Sprach-Engine aufgerufen werden, durch den Thread aus, um solche Aufgaben wie Stapelrahmen aufzählen oder Ausdrücke auswerten.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)   
 [IActiveScriptErrorDebug-Schnittstelle](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
 [BREAKRESUMEACTION-Enumeration](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION-Enumeration](../../winscript/reference/errorresumeaction-enumeration.md)