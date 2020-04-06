---
title: IDebugBinder3::GetEEService | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7c08d7df4a6b05be489f6b9ab06569c085f3b1f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735824"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
Diese Methode gibt einen angeforderten Dienst zurück.

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
[in] `GUID` eines Kreditors (ein Nullwert ist akzeptabel).

`language`\
[in] `GUID` einer Sprache (ein Nullwert ist akzeptabel).

`iid`\
[in] `IID` des zu erhaltenden Dienstes.

`ppService`\
[out] Eine Schnittstelle zum angeforderten Dienst.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Übergeben `IID` Sie die für die [IEEVisualizerServiceProvider-Schnittstelle](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) (`IID_IEEVisualizerServiceProvider`), um zu sehen, ob der Typvisualisierungsdienst verfügbar ist. Wenn dies der Zutun ist, kann der Ausdrucksauswertungsgeber die [IEEVisualizerService-Schnittstelle](../../../extensibility/debugger/reference/ieevisualizerservice.md) abrufen, um Typvisualisierungen zu unterstützen. Weitere Informationen finden Sie [unter Visualisieren und Anzeigen von Daten.](../../../extensibility/debugger/visualizing-and-viewing-data.md)

## <a name="see-also"></a>Weitere Informationen
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md)
