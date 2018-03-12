---
title: IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e428f12b3d199603ac341a5e069fcc5ce5d36f93
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Informiert, dass der Host über ein Skript zur Laufzeit Fehler beim Debuggen des Prozesses Manager einen JIT-Skriptdebugger nicht finden kann.  
  
 Um einen Debugger in Ihrem Host zu implementieren, sollten Sie behandeln [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md). Basierend auf eine Benutzeraktion kann der Host kann entweder den Debugger Anfügen und, oder zurückgeben das Starten des Debuggers in der OnScriptErrorDebug `pfEnterDebugger` Parameter. Sie sollten auch implementieren diese Schnittstelle, um die Benachrichtigung über den Fehler zur Laufzeit zu erhalten, selbst wenn es sind keine externen Debugger, die von der Debug-Prozess-Manager interpretiert werden können.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pErrorDebug`  
 [in] Die Laufzeitfehler, die aufgetreten sind.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 [out] Ob Aufrufen [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) , wenn der Benutzer entscheidet, ohne Debuggen zu fortfahren.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Sie sollten auch diese Schnittstelle, um eine Benachrichtigung erhalten implementieren.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSiteDebugEx-Schnittstelle](../../winscript/reference/iactivescriptsitedebugex-interface.md)