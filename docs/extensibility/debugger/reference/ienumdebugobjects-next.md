---
title: IEnumDebugObjects::Next | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugObjects::Next
helpviewer_keywords:
- IEnumDebugObjects::Next method
ms.assetid: e54c3055-6030-4dc9-9f7a-5e3ce75f252f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f932b5d9d38fba94370c071c3c3714de00f92a41
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ienumdebugobjectsnext"></a>IEnumDebugObjects::Next
Diese Methode gibt den nächsten Satz von Elementen aus der Enumeration.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Next(  
   ULONG          celt,  
   IDebugObject** rgelt,  
   ULONG*         pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint           celt,  
   IDebugObject[] rgelt,  
   ref uint       pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `celt`  
 [in] Die Anzahl der abzurufenden Elemente. Außerdem gibt die maximale Größe von der `rgelt` Array.  
  
 `rgelt`  
 [in, out] Array von [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Elemente ausgefüllt werden.  
  
 `pceltFetched`  
 [out] Gibt die Anzahl der Elemente, die tatsächlich im zurückgegebenen `rgelt`.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`. Gibt `S_FALSE` Wenn weniger als die angeforderte Anzahl von Elementen zurückgegeben werden konnte; andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)