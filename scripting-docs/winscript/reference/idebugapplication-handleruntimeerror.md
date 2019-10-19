---
title: 'Idebugapplication:: handleruntimeerror | Microsoft-Dokumentation'
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
ms.openlocfilehash: 2fd4ba2b811cd6c4e38c10a0c68c5808f2c0870a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574331"
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Bewirkt, dass der aktuelle Thread blockiert und eine Benachrichtigung über den Fehler an die Debugger-IDE sendet.  
  
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
 in Der aufgetretene Fehler.  
  
 `pScriptSite`  
 in Die Skript Site des Threads.  
  
 `pbra`  
 vorgenommen Aktion, die durchgeführt werden soll, wenn der Debugger die Anwendung fortsetzt.  
  
 `perra`  
 vorgenommen Die auszuführende Aktion, wenn der Debugger die Anwendung fortsetzt, wenn ein Fehler auftritt.  
  
 `pfCallOnScriptError`  
 vorgenommen Flag, das `TRUE` wird, wenn die Engine die `IActiveScriptSite::OnScriptError`-Methode aufruft.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Eine Sprach-Engine ruft diese Methode im Kontext eines Threads auf, der einen Laufzeitfehler verursacht. Diese Methode bewirkt, dass der aktuelle Thread blockiert und eine Fehler Benachrichtigung sendet, die an die Debugger-IDE gesendet wird. Wenn die Debugger-IDE die Anwendung fortsetzt, gibt diese Methode mit der auszuführenden Aktion zurück.  
  
> [!NOTE]
> Während des Lauf zeitfehlers kann die Sprach-Engine vom Thread aufgerufen werden, um Aufgaben wie das Aufzählen von Stapel Rahmen oder das Auswerten von Ausdrücken auszuführen.  
  
## <a name="see-also"></a>Siehe auch  
 [Idebugapplication-Schnittstelle](../../winscript/reference/idebugapplication-interface.md)    
 [Iactivescripterrordebug-Schnittstelle](../../winscript/reference/iactivescripterrordebug-interface.md)    
 [Iactivescriptsite](../../winscript/reference/iactivescriptsite.md) -   
 [Breakresumeaction-Enumeration](../../winscript/reference/breakresumeaction-enumeration.md)    
 [ERRORRESUMEACTION-Enumeration](../../winscript/reference/errorresumeaction-enumeration.md)