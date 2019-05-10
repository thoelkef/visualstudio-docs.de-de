---
title: IDebugObject::IsEqual | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 49d909dc0896bcc1b130ce908699c04ad9543c73
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62918504"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vergleicht ein Objekt mit diesem Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT IsEqual(   
   IDebugObject* pObject,  
   BOOL*         pfIsEqual  
);  
```  
  
```csharp  
int IsEqual(  
   IDebugObject pObject,  
   out int      pfIsEqual  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pObject`  
 [in] Ein [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekt, das das zu vergleichende Objekt darstellt.  
  
 `pfIsEqual`  
 [out] Ungleich NULL zurück (`TRUE`), wenn die Werte der Objekte gleich ist; andernfalls sind, gibt NULL zurück (`FALSE`).  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 In der Regel kann diese Methode vergleichen die Adressen der-Werte dargestellt werden, indem die `pObject` -Parameter, und dies [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt, wenn die Adressen gleich sind, und klicken Sie dann die Objekte als gleich betrachtet werden können.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
