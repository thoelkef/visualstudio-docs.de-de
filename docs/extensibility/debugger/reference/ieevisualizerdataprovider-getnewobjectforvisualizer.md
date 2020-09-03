---
title: 'Ieevisualizerdataprovider:: getnewobjectforvisualizer | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::GetNewObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::GetNewObjectForVisualizer method
ms.assetid: a898d549-4898-4fde-aad1-e8bb89129652
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c478ca3fc913f5ab79f37a957b05ff1d665f8aa5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718102"
---
# <a name="ieevisualizerdataprovidergetnewobjectforvisualizer"></a>IEEVisualizerDataProvider::GetNewObjectForVisualizer
Mit dieser Methode wird ein neues-Objekt für die Schnellansicht abgerufen. Diese Methode erstellt immer ein neues-Objekt aus dem vorhandenen-Objekt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetNewObjectForVisualizer(
   IDebugObject** ppObject
);
```

```csharp
int GetNewObjectForVisualizer(
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parameter
`ppObject`\
vorgenommen Das neue-Objekt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 `This method` wertet das aktuell dargestellte Objekt erneut aus und gibt das Ergebnis als neues-Objekt zurück. Das vorhandene Objekt wird als Ergebnis der Auswertung aktualisiert.

## <a name="see-also"></a>Weitere Informationen
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
