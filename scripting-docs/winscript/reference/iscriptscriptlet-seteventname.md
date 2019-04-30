---
title: IScriptScriptlet::SetEventName | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptScriptlet.SetEventName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptScriptlet::SetEventName
ms.assetid: 8787d58b-7deb-415b-b0e9-d2f0eb72dcf7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6bfa0bd69673ec8bbfc65f7f171dfbb933c7a68
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786723"
---
# <a name="iscriptscriptletseteventname"></a>IScriptScriptlet::SetEventName
Legt den Namen des Ereignisses, das das Scriptlet zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SetEventName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `psz`  
 [in] Einen Puffer, den Ereignisnamen, der zugeordnet wird, enthält, die `IScriptScriptlet` Objekt.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptScriptlet-Schnittstelle](../../winscript/reference/iscriptscriptlet-interface.md)