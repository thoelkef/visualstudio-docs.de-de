---
title: IEEVisualizerDataProvider::SetObjectForVisualizer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fdbd6ec439fc46b0ecab7621d4f793c1b3e33450
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893480"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Es wird vom Implementierer getroffen, um zu bestimmen, wie Fehlerinformationen zurückgegeben wird. Allerdings ist es möglich, dass einige Aufrufer können nur suchen, um festzustellen, ob ein Exception-Objekt zurückgegeben wurde, gibt es wissen eines Fehlers wurde, damit diese Methode immer ein Exception-Objekt zurückgeben soll, wenn ein Fehler aufgetreten. Die fehlermeldungs-Zeichenfolge darf auch bereitgestellt werden, für den Fall, dass die vom Aufrufer zu verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

