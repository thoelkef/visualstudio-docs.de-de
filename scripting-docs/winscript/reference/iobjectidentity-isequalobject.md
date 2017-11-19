---
title: IObjectIdentity::IsEqualObject | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IObjectIdentity.IsEqualObject
apilocation: scrobj.dll
helpviewer_keywords: IsEqualObject method
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52e386055e458568f8d4076a37489b7b2397f399
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
Bestimmt, ob ein Objekt mit dem aktuellen Objekt identisch ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
|`S_FALSE`|Die Objekte sind ungleich.|  
  
## <a name="remarks"></a>Hinweise  
 Eine Implementierung der `IsEqualObject` -Methode zurückgeben sollte `S_OK` nur, wenn die Objekte identisch sind.  
  
## <a name="see-also"></a>Siehe auch  
 [IObjectIdentity-Schnittstelle](../../winscript/reference/iobjectidentity-interface.md)