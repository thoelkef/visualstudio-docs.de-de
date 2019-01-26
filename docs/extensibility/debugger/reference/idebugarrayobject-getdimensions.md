---
title: IDebugArrayObject::GetDimensions | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b33df4ab74b0446b18f2c2a1693ffc8f711bb2fa
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54955894"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
Ruft die Dimensionen des Arrays ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```csharp  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwCount`  
 [in] Die Anzahl der Dimensionen, die abgerufen werden.  
  
 `dwDimensions`  
 [in, out] Ein Array, das mit der Größe der einzelnen Dimensionen gefüllt ist. `dwCount` Gibt an, die maximale Größe der `dwDimensions` Array.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein mehrdimensionales Array kann es sich um andere Größen für jede Dimension sein. Angenommen, das dreidimensionale Array `myarray[3][2][6]`, würde diese Methode zurückgeben, 3, 2 und 6 in der `dwDimensions` Parameter in dieser Reihenfolge.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)