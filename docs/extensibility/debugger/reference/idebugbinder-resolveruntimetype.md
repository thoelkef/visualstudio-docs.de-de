---
title: IDebugBinder::ResolveRuntimeType | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f9224314d1417f08bbf025d774c1ecc8ac706e05
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852517"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
Diese Methode bestimmt der Laufzeittyp eines Objekts.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT ResolveRuntimeType(   
   IDebugObject* pObject,  
   IDebugField** ppResolved  
);  
```  
  
```csharp  
int ResolveRuntimeType(  
   IDebugObject     pObject,   
   out IDebugField  ppResolved  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pObject`  
 [in] Die [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) aufgelöst werden.  
  
 `ppResolved`  
 [out] Gibt den Typ des Objekts als ein [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Der Laufzeittyp eines Objekts ist nicht immer zum Zeitpunkt der Kompilierung bekannt. Beispielsweise kann Polymorphismus verwendet wird, ein Argument an eine Funktion als Basisklasse, z. B. eine Button-Klasse übergeben werden. Das tatsächliche Argument möglicherweise eine abgeleitete Klasse wie z. B. eine Radio Button-Klasse.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)