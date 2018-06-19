---
title: IDebugApplication::HandleRuntimeError | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: eead4780ff061ff9c7280aeee0936c8f64741981
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725790"
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Bewirkt, dass den aktuelle Thread blockiert, und sendet eine Benachrichtigung über den Fehler an den IDE-Debugger.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 [in] Die Skript-Site des Threads.  
  
 `pbra`  
 [out] Auszuführende Aktion, wenn der Debugger die Anwendung wird fortgesetzt.  
  
 `perra`  
 [out] Auszuführende Aktion, wenn der Debugger die Anwendung wird fortgesetzt, wenn ein Fehler vorliegt.  
  
 `pfCallOnScriptError`  
 [out] Flag, das ist `TRUE` , wenn das Modul aufrufen sollte die `IActiveScriptSite::OnScriptError` Methode.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Ein Sprachmodul ruft diese Methode im Kontext eines Threads, die bewirkt, ein Laufzeitfehler dass auf. Diese Methode bewirkt, dass den aktuelle Thread blockiert und sendet eine Benachrichtigung über einen Fehler an den IDE-Debugger gesendet werden. Wenn der Debugger IDE auf die Anwendung zurückkehrt, gibt diese Methode mit der Aktion an, die ausgeführt werden.  
  
> [!NOTE]
>  Klicken Sie in den Fehler zur Laufzeit kann das Sprachmodul durch solche Aufgaben ausführen wie Stapelrahmen aufzählen oder Ausdrücke auswerten des Threads aufgerufen werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugApplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)   
 [IActiveScriptErrorDebug-Schnittstelle](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
 [BREAKRESUMEACTIONS-Enumeration](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION-Enumeration](../../winscript/reference/errorresumeaction-enumeration.md)