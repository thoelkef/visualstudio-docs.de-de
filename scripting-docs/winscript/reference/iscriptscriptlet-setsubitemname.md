---
title: IScriptScriptlet::SetSubItemName | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptScriptlet.SetSubItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptScriptlet::SetSubItemName
ms.assetid: 619f222f-b4c3-4c7b-9d19-e4e7037343a6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b9a4f67fb5a383666cb9f83fc2e0e38fbffb51f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786561"
---
# <a name="iscriptscriptletsetsubitemname"></a>IScriptScriptlet::SetSubItemName
Legt den letzten Bezeichner in den vollqualifizierten Namen des Hosts des Scriptlet-Objekt fest.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SetSubItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `psz`  
 Scriptlet-Name verfügt über mehr als einer Ebene, wenn der Host vollständig qualifizierte des `psz` ist die Adresse des Datenpuffers des Bezeichners auf der zweiten Ebene.  
  
 Scriptlet-Name verfügt über eine Ebene auf, wenn der Host vollständig qualifizierte des `psz` ist die Adresse des Datenpuffers des Bezeichners auf der ersten Ebene.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptScriptlet-Schnittstelle](../../winscript/reference/iscriptscriptlet-interface.md)