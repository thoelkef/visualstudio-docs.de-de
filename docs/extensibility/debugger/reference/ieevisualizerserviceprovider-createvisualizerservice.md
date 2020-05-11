---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e05677122b7d4e4eb025a9382ede1509374de894
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717909"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
Diese Methode erstellt einen Visualisierungsdienst.

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

## <a name="parameters"></a>Parameter
`binder`\
[in] Das [IDebugBinder-Objekt, das](../../../extensibility/debugger/reference/idebugbinder.md) an [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)übergeben wurde.

`pSymProv`\
[in] Das [IDebugSymbolProvider-Objekt,](../../../extensibility/debugger/reference/idebugsymbolprovider.md) das an `IDebugParsedExpression::EvaluateSync`übergeben wird.

`pAddress`\
[in] Das [IDebugAddress-Objekt,](../../../extensibility/debugger/reference/idebugaddress.md) das an `IDebugParsedExression::EvaluateSync`übergeben wird.

`dataProvider`\
[in] Ein Objekt, das die [IEEVisualizerDataProvider-Schnittstelle](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) implementiert (vom Ausdrucksevaluator bereitgestellt).

`ppService`\
[out] Der erstellte Dienst.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die `binder` `pSymProv`Parameter `pAddress` , und Parameter `IDebugParsedExpression::EvaluateSync` wurden alle an die Methode übergeben. `CreateVisualizerService`ist nur `IDebugParsedExpression::EvaluateSync` als Teil der Unterstützung eines Ausdrucksevaluators für Typvisualisierer aufzusuchen.

## <a name="see-also"></a>Weitere Informationen
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
