---
title: IObjectIdentity::IsEqualObject | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IObjectIdentity.IsEqualObject
apilocation:
- scrobj.dll
helpviewer_keywords:
- IsEqualObject method
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c215a15a1239f07272079783366a1617c3a626e2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58156033"
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
Bestimmt, ob ein Objekt mit dem aktuellen Objekt entspricht.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT IsEqualObject(  
  IUnknown*punk  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `punk`  
 [in] Die Adresse des Objekts, mit dem aktuellen Objekt verglichen werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Objekte sind gleich.|  
|`S_FALSE`|Die Objekte sind nicht gleich.|  
  
## <a name="remarks"></a>Hinweise  
 Eine Implementierung der `IsEqualObject` Methode zurückgeben soll `S_OK` nur dann, wenn die Objekte identisch sind.  
  
## <a name="see-also"></a>Siehe auch  
 [IObjectIdentity-Schnittstelle](../../winscript/reference/iobjectidentity-interface.md)