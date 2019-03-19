---
title: IActiveScriptSiteDebug::OnScriptErrorDebug | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::OnScriptErrorDebug
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50e8c7baa42d6f2f36dc71b768797dfe2a464bf3
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58160104"
---
# <a name="iactivescriptsitedebugonscripterrordebug"></a>IActiveScriptSiteDebug::OnScriptErrorDebug
Ermöglicht einen Smarthost zu bestimmen, wie zum Behandeln von Laufzeitfehlern führen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pErrorDebug`  
 [in] Die Laufzeitfehler, die aufgetreten sind  
  
 `pfEnterDebugger`  
 [out] Dieses Flag gibt an, ob der Fehler an dem Debugger an, führen Sie die JIT-Debuggen übergeben.  
  
 `pfCallOnScriptErrorWhenContinuing`  
 [out] Flag, das angibt, ob aufgerufen `IActiveScriptSite::OnScriptError` Wenn der Benutzer entscheidet, ohne das Debuggen fortzusetzen.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliche Werte enthalten, aber Sie sind nicht auf den Wert in der folgenden Tabelle beschränkt.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Ein Smarthost kann diese Methode verwenden, um zu bestimmen, wie zur Laufzeit Fehler behandelt.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSiteDebug-Schnittstelle](../../winscript/reference/iactivescriptsitedebug-interface.md)