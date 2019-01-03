---
title: IDebugArrayObject::GetElement | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 54ebe6e0400ba35c50f67a6fb2574df12dce276b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53821885"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
Ruft ein Element des Arrays ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetElement(   
   DWORD          dwIndex,  
   IDebugObject** ppElement  
);  
```  
  
```csharp  
int GetElement(  
   [In] uint dwIndex,   
   out IDebugObject ppElement  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwIndex`  
 [in] Der Elementindex.  
  
 `ppElement`  
 [out] Gibt eine [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Schnittstelle, die das Element darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode sieht alle Elemente eines Arrayobjekts als ein eindimensionales Array, selbst wenn das Arrayobjekt mehrdimensionale ist. Angenommen, das Array `myarray[3][2][6]` und `dwIndex` Parameter von 20, würde dieser Methode das Element aus zurückgeben `myarray[1][1][2]`, und ein `dwIndex` Parameter 21 würde das Element zurückgeben `myarray[1][1][3]`. Verwenden der [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) Methode, um zu bestimmen, die Gesamtanzahl der Elemente im Array.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)