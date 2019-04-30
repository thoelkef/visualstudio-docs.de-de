---
title: IPerPropertyBrowsing2::SetPredefinedValue | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.SetPredefinedValue
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::SetPredefinedValue
ms.assetid: 3aff5300-c5a4-4d9b-9d47-a75b64014ac4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d35e087cc057608666e104681d65fa8009f8167
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944824"
---
# <a name="iperpropertybrowsing2setpredefinedvalue"></a>IPerPropertyBrowsing2::SetPredefinedValue
Legt den Wert der durch die angegebene Eigenschaft `dispID`. Der vordefinierte Wert wird durch das Token identifiziert. `dwCookie.`  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT SetPredefinedValue(  
   DISPID  dispid,  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dispid`  
 [in] Dispatch-ID der Eigenschaft für die ein vordefinierter Wert festgelegt wird.  
  
 `dwCookie`  
 [in] Token, das den festzulegenden Wert identifiziert.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt einen gültigen `HRESULT`, in der Regel `S_OK`.  
  
## <a name="see-also"></a>Siehe auch  
 [IPerPropertyBrowsing2-Schnittstelle 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)