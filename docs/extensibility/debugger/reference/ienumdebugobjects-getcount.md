---
title: IEnumDebugObjects::GetCount | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugObjects::GetCount
helpviewer_keywords:
- IEnumDebugObjects::GetCount method
ms.assetid: 9cbc5db4-03ae-479f-a664-13cad66ad210
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 67568b10d5b7fe33adf1d67bd9bd1f2771d058e0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53873261"
---
# <a name="ienumdebugobjectsgetcount"></a>IEnumDebugObjects::GetCount
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
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)