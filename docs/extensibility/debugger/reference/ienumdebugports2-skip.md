---
title: IEnumDebugPorts2::Skip | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugPorts2::Skip
helpviewer_keywords:
- IEnumDebugPorts2::Skip
ms.assetid: a837383f-7b39-4e06-b336-f1715b073dbe
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3586e3aefa38b7c8a49b693df86c3241a39d194
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916103"
---
# <a name="ienumdebugports2skip"></a>IEnumDebugPorts2::Skip
Überspringt die angegebene Anzahl von Elementen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 [in] Die Anzahl der zu überspringenden Elemente.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` Wenn `celt` größer als die Anzahl der verbleibenden Elemente ist; andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Wenn `celt` gibt einen Wert größer als die Anzahl der verbleibenden Elemente am Ende die Enumeration festgelegt ist und `S_FALSE` zurückgegeben wird.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)