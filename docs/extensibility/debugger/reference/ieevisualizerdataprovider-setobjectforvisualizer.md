---
title: IEEVisualizerDataProvider::SetObjectForVisualizer | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords: IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 76a901401e854611cc987ac5c0cf8eeabb8dfd53
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
Diese Methode ändert das Objekt, das die Schnellansicht darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```csharp  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pNewObject`  
 [in] Das Objekt festgelegt werden soll.  
  
 `error`  
 [out] Wenn Fehler bei der Festlegung des Objekts, enthält diese Zeichenfolge die Fehlermeldung.  
  
 `pException`  
 [out] Wenn ein Fehler aufgetreten ist, enthält dieses Objekt die Ausnahmeinformationen.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Es wird vom Implementierer um zu bestimmen, wie Fehlerinformationen zurückgegeben wird. Es ist jedoch möglich, dass einige Aufrufer möglicherweise nur suchen, um festzustellen, ob ein Exception-Objekt zurückgegeben wurde, um zu wissen, es ist ein Fehler aufgetreten, damit diese Methode immer ein Exception-Objekt zurückgeben soll, wenn ein Fehler aufgetreten. Die Fehlerzeichenfolge sollte auch angegeben werden, für den Fall, dass der Aufrufer möchte überprüfen, verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)