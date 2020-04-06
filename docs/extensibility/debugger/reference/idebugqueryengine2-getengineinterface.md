---
title: IDebugQueryEngine2::GetEngineInterface | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2::GetEngineInterface
helpviewer_keywords:
- IDebugQueryEngine2::GetEngineInterface
ms.assetid: ed84aa98-7ec7-48f3-97ae-821090bc3664
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82f3214783a35e668bf3164c8659f60f863e9a43
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720666"
---
# <a name="idebugqueryengine2getengineinterface"></a>IDebugQueryEngine2::GetEngineInterface
Ruft eine benutzerdefinierte Debug-Engine(DE)-Schnittstelle ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetEngineInterface( 
   IUnknown** ppUnk
);
```

```csharp
int GetEngineInterface( 
   out object ppUnk
);
```

## <a name="parameters"></a>Parameter
`ppUnk`\
[out] Gibt `IUnknown` ein Objekt für das Debugmodul (DE) zurück und kann für jede andere gültige Schnittstelle abgefragt werden, die einer DE zugeordnet ist (z. B. [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) oder [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)).

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die resultierende Schnittstelle sollte mit Vorsicht verwendet werden, da das Aufrufen von Schnittstellen, die von dieser Methode abgerufen werden, die Verarbeitung des Sitzungsdebug-Managers umgeht und dazu führen kann, dass das SDM beim Debuggen in einen schlechten Zustand gerät oder Fehler generiert.

## <a name="see-also"></a>Weitere Informationen
- [IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
