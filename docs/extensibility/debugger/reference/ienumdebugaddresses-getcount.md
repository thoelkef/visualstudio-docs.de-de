---
title: IEnumDebugAddresses::GetCount | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugAddresses::GetCount
helpviewer_keywords:
- IEnumDebugAddresses::GetCount method
ms.assetid: f2ca8ff8-539f-457c-83f8-9bbf97618065
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e8696e42459058e0f55f5d9a8de57b74eb2fcd48
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836386"
---
# <a name="ienumdebugaddressesgetcount"></a>IEnumDebugAddresses::GetCount
Diese Methode gibt die Anzahl der Elemente in der Enumeration.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetCount(  
   [out] ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pcelt`  
 [out] Gibt die Anzahl der Elemente in der Enumeration zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ist nicht Teil der übliche COM-Enumerationsschnittstelle gibt an, dass nur weiter, Klonen, überspringen und Zurücksetzen der implementiert werden müssen.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)