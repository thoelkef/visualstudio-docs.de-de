---
title: 'Iscriptentry:: GetItemName | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetItemName
ms.assetid: 8f2562f1-8231-4a39-ad79-074f9ec3d403
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dcd1b83fa6d22fafc2123645f1f252fa1325f7f1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575453"
---
# <a name="iscriptentrygetitemname"></a>IScriptEntry::GetItemName
Gibt den Elementnamen zurück, der ein `IScriptEntry` Objekt identifiziert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetItemName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pbstr`  
 vorgenommen Die Adresse eines Puffers, der den Elementnamen enthält. Der Elementname wird vom Host zum Identifizieren des Eintrags verwendet.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## <a name="remarks"></a>Hinweise  
 Bei `IScriptScriptlet` Objekten legen Sie den Elementnamen mithilfe von [iactivescriptauthor:: addscriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)fest. Für andere Schnittstellen legen Sie den Elementnamen mithilfe von [iscriptentry:: setitemname](../../winscript/reference/iscriptentry-setitemname.md)fest.  
  
## <a name="see-also"></a>Siehe auch  
 [IScriptEntry-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)