---
title: IEEVisualizerDataProvider::SetObjectForVisualizer | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 31bc89e248d609e8b828d4cc5b9ac41c8e15c70c
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203688"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
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

## <a name="parameters"></a>Parameter
`pNewObject`\
[in] Das Objekt festgelegt werden soll.

`error`\
[out] Wenn Fehler bei der Festlegung des Objekts, enthält diese Zeichenfolge die Fehlermeldung.

`pException`\
[out] Wenn ein Fehler aufgetreten ist, enthält dieses Objekt die Ausnahmeinformationen.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Es wird vom Implementierer getroffen, um zu bestimmen, wie Fehlerinformationen zurückgegeben wird. Allerdings ist es möglich, dass einige Aufrufer können nur suchen, um festzustellen, ob ein Exception-Objekt zurückgegeben wurde, gibt es wissen eines Fehlers wurde, damit diese Methode immer ein Exception-Objekt zurückgeben soll, wenn ein Fehler aufgetreten. Die fehlermeldungs-Zeichenfolge darf auch bereitgestellt werden, für den Fall, dass die vom Aufrufer zu verwenden.

## <a name="see-also"></a>Siehe auch
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)