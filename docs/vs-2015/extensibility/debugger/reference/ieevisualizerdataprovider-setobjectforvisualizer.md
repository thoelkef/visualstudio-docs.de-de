---
title: 'Ieevisualizerdataprovider:: setobjectforvisualizer | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d20164e31f8c42b7099f99ff34ac120319a2def1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62540278"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode ändert das Objekt, das die Schnellansicht darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```csharp  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pNewObject`  
 in Das festzulegende-Objekt.  
  
 `error`  
 vorgenommen Wenn beim Festlegen des-Objekts ein Fehler aufgetreten ist, enthält diese Zeichenfolge die Fehlermeldung.  
  
 `pException`  
 vorgenommen Wenn ein Fehler aufgetreten ist, enthält dieses Objekt die Ausnahme Informationen.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Es ist für den Implementierer festzulegen, wie Fehlerinformationen zurückgegeben werden. Es ist jedoch möglich, dass einige Aufrufer nur überprüfen, ob ein Ausnahme Objekt zurückgegeben wurde, um zu wissen, dass ein Fehler aufgetreten ist. Daher sollte diese Methode immer ein Ausnahme Objekt zurückgeben, wenn ein Fehler aufgetreten ist. Die Fehler Zeichenfolge sollte auch für den Fall bereitgestellt werden, dass der Aufrufer Sie verwenden möchte.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ieevisualizerdataprovider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
