---
title: IDebugObject::IsEqual | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject::IsEqual
helpviewer_keywords: IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2af7ef11a142442b97dbb5d6a4d0545bf118da39
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Vergleicht ein Objekt mit diesem Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
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
 [in] Ein [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekt, das zu vergleichende Objekt darstellt.  
  
 `pfIsEqual`  
 [out] Ungleich 0 (null) zurückgibt (`TRUE`) gibt 0 zurück, wenn die Werte der Objekte gleich; andernfalls sind, (`FALSE`).  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 In der Regel kann diese Methode die Adressen der Werte, dargestellt durch Vergleichen der `pObject` -Parameter und diese [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekt; Wenn die Adressen gleich sind, und klicken Sie dann die Objekte als gleich betrachtet werden können.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)