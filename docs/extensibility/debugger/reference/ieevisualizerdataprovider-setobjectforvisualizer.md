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
ms.openlocfilehash: cd7bd4bfd113da8cfd311d1022967d8c99f915b5
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65223936"
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