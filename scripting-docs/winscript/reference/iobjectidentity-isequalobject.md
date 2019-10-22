---
title: 'Iobjectidentity:: isequalobject | Microsoft-Dokumentation'
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
ms.openlocfilehash: 636dfa07b1fc94dfec2273220aa4101f5cd085b1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571465"
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
Bestimmt, ob ein Objekt gleich dem aktuellen Objekt ist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT IsEqualObject(  
  IUnknown*punk  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `punk`  
 in Die Adresse des-Objekts, das mit dem aktuellen-Objekt verglichen werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück. Mögliches Werte (aber nicht die Einzigen) sind die in der folgenden Tabelle.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`S_OK`|Die Objekte sind gleich.|  
|`S_FALSE`|Die Objekte sind nicht gleich.|  
  
## <a name="remarks"></a>Hinweise  
 Eine Implementierung der `IsEqualObject`-Methode sollte nur `S_OK` zurückgeben, wenn die Objekte identisch sind.  
  
## <a name="see-also"></a>Siehe auch  
 [IObjectIdentity-Schnittstelle](../../winscript/reference/iobjectidentity-interface.md)