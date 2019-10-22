---
title: 'Iactivescriptsitedebug:: onscripterrordebug | Microsoft-Dokumentation'
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
ms.openlocfilehash: 894767b3dae9db54e8bc438a82b27195308a4342
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572204"
---
# <a name="iactivescriptsitedebugonscripterrordebug"></a>IActiveScriptSiteDebug::OnScriptErrorDebug
Ermöglicht einem Smarthost, zu bestimmen, wie Laufzeitfehler behandelt werden.  
  
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
 in Der aufgetretene Laufzeitfehler.  
  
 `pfEnterDebugger`  
 vorgenommen Flag zum angeben, ob der Fehler an den Debugger übergeben werden soll, um JIT-Debugging durchzuführen.  
  
 `pfCallOnScriptErrorWhenContinuing`  
 vorgenommen Flag zum angeben, ob `IActiveScriptSite::OnScriptError` aufgerufen werden soll, wenn der Benutzer entscheidet, ohne Debuggen fortzufahren.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliche Werte sind, sind jedoch nicht auf den Wert in der folgenden Tabelle beschränkt.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Ein intelligenter Host kann diese Methode verwenden, um zu bestimmen, wie Laufzeitfehler behandelt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [IActiveScriptSiteDebug-Schnittstelle](../../winscript/reference/iactivescriptsitedebug-interface.md)