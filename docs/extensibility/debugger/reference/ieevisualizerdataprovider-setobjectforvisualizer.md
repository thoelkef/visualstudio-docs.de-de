---
title: 'Ieevisualizerdataprovider:: setobjectforvisualizer | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab63f1e74e0cd3ac64a4d7e7687a9136075b41a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718078"
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
in Das festzulegende-Objekt.

`error`\
vorgenommen Wenn beim Festlegen des-Objekts ein Fehler aufgetreten ist, enthält diese Zeichenfolge die Fehlermeldung.

`pException`\
vorgenommen Wenn ein Fehler aufgetreten ist, enthält dieses Objekt die Ausnahme Informationen.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Es ist für den Implementierer festzulegen, wie Fehlerinformationen zurückgegeben werden. Es ist jedoch möglich, dass einige Aufrufer nur überprüfen, ob ein Ausnahme Objekt zurückgegeben wurde, um zu wissen, dass ein Fehler aufgetreten ist. Daher sollte diese Methode immer ein Ausnahme Objekt zurückgeben, wenn ein Fehler aufgetreten ist. Die Fehler Zeichenfolge sollte auch für den Fall bereitgestellt werden, dass der Aufrufer Sie verwenden möchte.

## <a name="see-also"></a>Weitere Informationen
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
