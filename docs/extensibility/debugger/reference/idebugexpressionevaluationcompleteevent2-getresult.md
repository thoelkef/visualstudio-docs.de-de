---
title: IDebugExpressionEvaluationCompleteEvent2::GetResult | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2::GetResult
ms.assetid: d9ad3e22-b6b2-421e-9a43-6bb8c70d12a9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8efcb487ae2d95aa54671f608d51eff78960a6de
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325737"
---
# <a name="idebugexpressionevaluationcompleteevent2getresult"></a>IDebugExpressionEvaluationCompleteEvent2::GetResult
Ruft das Ergebnis der Auswertung des Ausdrucks ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetResult( 
   IDebugProperty2** ppResult
);
```

```csharp
int GetResult( 
   out IDebugProperty2 ppResult
);
```

## <a name="parameters"></a>Parameter
`ppResult` [out] Gibt eine [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Objekt, das das Ergebnis der Auswertung des Ausdrucks darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Das zurückgegebene [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Objekt enthält den Wert des ausgewerteten Ausdrucks. Beachten Sie, dass dieser Wert kann einen komplexen Wert wie z. B. ein Array sein, aber das Endergebnis muss einen numerischen oder string-Wert, der dem Benutzer angezeigt wird.

## <a name="see-also"></a>Siehe auch
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)