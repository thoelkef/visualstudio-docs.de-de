---
title: IDispatchEx::GetNameSpaceParent | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNameSpaceParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNameSpaceParent method
ms.assetid: 0b077d39-2fd6-4390-8cd5-128d9b8dc90c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1abe2a880e12d6a4a3c1dfda32d30722525858f5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000823"
---
# <a name="idispatchexgetnamespaceparent"></a>IDispatchEx::GetNameSpaceParent
Ruft die Schnittstelle für den übergeordneten Namespace eines Objekts ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
HRESULT GetNameSpaceParent(  
   IUnknown **ppunk  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppunk`  
 Adresse von einem `IUnknown` Schnittstellenzeiger, der den Namespace des übergeordneten Schnittstelle empfängt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt `S_OK` bei Erfolg oder ein OLE definierter Fehlercode andernfalls.  
  
## <a name="see-also"></a>Siehe auch  
 [IDispatchEx-Schnittstelle](../../winscript/reference/idispatchex-interface.md)