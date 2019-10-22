---
title: 'Iscriptscriptlet:: getsubitemname | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptScriptlet.GetSubItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptScriptlet::GetSubItemName
ms.assetid: 9ad963fc-9ce8-4b77-92c1-fb90d6307801
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b36f6dd98534b8122a6814f1fd154eca7882251a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571918"
---
# <a name="iscriptscriptletgetsubitemname"></a>IScriptScriptlet::GetSubItemName
Gibt den letzten Bezeichner im voll qualifizierten Namen des Objekt Hosts eines Scriptlets zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetSubItemName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstr`  
 vorgenommen Wenn der voll qualifizierte Scriptlet-Name des Hosts mehr als eine Ebene aufweist, gibt `pbstr` die Puffer Adresse des Bezeichners auf der zweiten Ebene zurück.  
  
 Wenn der voll qualifizierte Scriptlet-Name des Hosts eine Ebene aufweist, gibt `pbstr` die Puffer Adresse des Bezeichners auf der ersten Ebene zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptScriptlet-Schnittstelle](../../winscript/reference/iscriptscriptlet-interface.md)