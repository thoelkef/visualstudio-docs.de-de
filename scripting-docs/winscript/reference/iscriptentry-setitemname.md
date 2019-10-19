---
title: 'Iscriptentry:: setitemname | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetItemName
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ba226704f5b064c86b52c1b349650d509b2b549
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575372"
---
# <a name="iscriptentrysetitemname"></a>IScriptEntry::SetItemName
Legt den Elementnamen fest, der ein `IScriptEntry` Objekt identifiziert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `psz`  
 in Die Adresse eines Puffers, der den Elementnamen enthält. Der Elementname wird vom Host zum Identifizieren des Eintrags verwendet.  
  
## <a name="return-value"></a>Rückgabewert  
 Eine `HRESULT`. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Die Methode konnte nicht erfolgreich ausgeführt werden.|  
  
## <a name="remarks"></a>Hinweise  
 Bei `IScriptEntry` Objekten gibt diese Methode `S_OK` zurück.  
  
 Bei `IScriptScriptlet` Objekten (die von `IScriptEntry` abgeleitet sind) gibt diese Methode `E_FAIL` zurück. Bei `IScriptScriptlet` Objekten wird der Elementname von [iactivescriptauthor:: addscriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) festgelegt und kann nicht geändert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Iscriptentry-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)    
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)