---
title: 'Iactivescriptsitedebugex:: oncannotjitscripterrordebug | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7358d2b372f0801b8c45816e1fc36018b37799b2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572181"
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Benachrichtigt den Host über einen Skript Laufzeitfehler, wenn der Prozess-Debug-Manager keinen Just-in-Time-Skript Debugger findet.  
  
 Wenn Sie einen Debugger in Ihrem Host implementieren möchten, müssen Sie [iactivescriptsitedebug:: onscripterrordebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)verarbeiten. Basierend auf einer Benutzeraktion kann der Host entweder den Debugger anfügen und zurückgeben oder den Start des Debuggers im onscripterrordebug-`pfEnterDebugger` Parameter zurückgeben. Außerdem sollten Sie diese Schnittstelle implementieren, um die Benachrichtigung über den Laufzeitfehler zu erhalten, auch wenn keine externen Debugger vorhanden sind, die vom prozessdebugmanager interpretiert werden können.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pErrorDebug`  
 in Der Laufzeitfehler, der aufgetreten ist.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 vorgenommen Gibt an, ob [iactivescriptsitedebug:: onscripterrordebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) aufgerufen werden soll, wenn der Benutzer entscheidet, ohne Debuggen fortzufahren.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Außerdem sollten Sie diese Schnittstelle implementieren, um eine Benachrichtigung zu erhalten.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSiteDebugEx-Schnittstelle](../../winscript/reference/iactivescriptsitedebugex-interface.md)