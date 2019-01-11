---
title: IActiveScriptSiteDebug::OnScriptErrorDebug | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 5680d22ffa5ec648afaced5e98f651e35758f929
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092117"
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