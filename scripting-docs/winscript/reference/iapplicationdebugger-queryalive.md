---
title: IApplicationDebugger::QueryAlive | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.QueryAlive
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::QueryAlive
ms.assetid: 41181ebb-a3bf-4e41-82af-d6c7348dc706
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48571476407c29b9af949bd6f626d14ea822f2e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725320"
---
# <a name="iapplicationdebuggerqueryalive"></a>IApplicationDebugger::QueryAlive
Gibt an, ob der Debugger reagiert.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT QueryAlive();  
```  
  
#### <a name="parameters"></a>Parameter  
 Diese Methode nimmt keine Parameter.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode gibt an, ob der Debugger reagiert. Implementierungen dieser Methode sollte stets `S_OK`.  
  
 Wenn der Debuggerprozess unerwartet beendet wird, ein Fehler von COM aus dem marshalling Proxy für Aufrufe dieser Methode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IApplicationDebugger-Schnittstelle](../../winscript/reference/iapplicationdebugger-interface.md)