---
title: IDebugBinder3::GetEEService | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: eaaaf52a0a577d8b802540ca9b4ae11ab9aa1dbd
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2019
ms.locfileid: "65614902"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
Diese Methode gibt einen angeforderten Dienst.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetEEService(
   [in] GUID        vendor,
   [in] GUID        language,
   [in] GUID        iid,
   [out] IUnknown** ppService
);
```

```csharp
Int GetEEService(
   Guid       vendor,
   Guid       language,
   Guid       iid,
   out object ppService
);
```

## <a name="parameters"></a>Parameter
`vendor`\
[in] `GUID` eines Anbieters (ein null-Wert ist akzeptabel).

`language`\
[in] `GUID` einer Sprache (ein null-Wert ist akzeptabel).

`iid`\
[in] `IID` des Diensts zu erhalten.

`ppService`\
[out] Eine Schnittstelle zu den angeforderten Dienst.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Übergeben Sie die `IID` für die [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) Schnittstelle (`IID_IEEVisualizerServiceProvider`) um festzustellen, ob der Dienst Typschnellansicht verfügbar ist. Wenn also die ausdrucksauswertung abrufen kann die [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) Schnittstelle, um Typ-Schnellansichten unterstützen. Finden Sie unter [visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md) Details.

## <a name="see-also"></a>Siehe auch
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md)