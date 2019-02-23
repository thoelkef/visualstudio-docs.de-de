---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 23c11e386b6c100839ae299e56e6a4d771012b38
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56688793"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
Diese Methode erstellt einen schnellansichtsdienst.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateVisualizerService(
   IDebugBinder*              binder,
   IDebugSymbolProvider*      pSymProv,
   IDebugAddress*             pAddress,
   IEEVisualizerDataProvider* dataProvider,
   IEEVisualizerService**     ppService
);
```

```csharp
int CreateVisualizerService(
   IDebugBinder binder,
   IDebugSymbolProvider      pSymProv,
   IDebugAddress             pAddress,
   IEEVisualizerDataProvider dataProvider,
   out IEEVisualizerService  ppService
);
```

#### <a name="parameters"></a>Parameter
 `binder`

 [in] Die [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) -Objekt übergeben, um [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).

 `pSymProv`

 [in] Die [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) -Objekt übergeben, um `IDebugParsedExpression::EvaluateSync`.

 `pAddress`

 [in] Die [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) -Objekt übergeben, um `IDebugParsedExression::EvaluateSync`.

 `dataProvider`

 [in] Ein Objekt, das die [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) Schnittstelle (bereitgestellt von der ausdrucksauswertung).

 `ppService`

 [out] Der erstellte Dienst.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Die `binder`, `pSymProv`, und `pAddress` Parameter wurden zum Übergeben der `IDebugParsedExpression::EvaluateSync` Methode. `CreateVisualizerService` nur aus aufgerufen werden soll `IDebugParsedExpression::EvaluateSync` als Teil einer ausdrucksauswertung-Unterstützung für Typ-Schnellansichten.

## <a name="see-also"></a>Siehe auch
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)