---
title: IEEVisualizerService::GetCustomViewerList | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f3808ad6fb511270ee3825601c476f10a8b77124
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718020"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
Diese Methode gibt eine Liste der Typvisualisierungen zurück, die diesem Dienst bekannt sind.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetCustomViewerList(
   ULONG                celtSkip,
   ULONG                celtRequested,
   DEBUG_CUSTOM_VIEWER* rgViewers,
   ULONG*               pceltFetched
);
```

```csharp
int GetCustomViewerList(
   uint                  celtSkip,
   uint                  celtRequested,
   DEBUG_CUSTOM_VIEWER[] rgViewers,
   out uint              pceltFetched
);
```

## <a name="parameters"></a>Parameter
`celtSkip`\
[in] Anzahl der zu überspringenden Visualisierungen.

`celRequested`\
[in] Anzahl der abzurufenden Visualisierungen (gibt `rgViewers` auch die Größe des Arrays an).

`rgViewers`\
[in, out] Array von [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Strukturen auszufüllen.

`pceltFetched`\
[out] Anzahl der tatsächlich abgerufenen Visualizer.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) übergibt die Anforderung an diese Methode als Teil ihrer Unterstützung für Typvisualisierer. Wenn der Ausdrucksauswertungsor auch benutzerdefinierte Viewer für denselben Typ bereitstellt, kann er entsprechend ausgefüllte [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) Strukturen für diese benutzerdefinierten Viewer an die Liste anhängen. Stellen Sie sicher, dass [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) diese zusätzlichen Viewer widerspiegelt.

 Weitere Informationen zu den Unterschieden zwischen Visualizern und Betrachtern finden Sie unter [Typvisualisierung und benutzerdefinierter Viewer.](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

## <a name="see-also"></a>Weitere Informationen
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)
- [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)
- [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)
- [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
