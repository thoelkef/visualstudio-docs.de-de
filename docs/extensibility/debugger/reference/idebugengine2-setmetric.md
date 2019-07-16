---
title: IDebugEngine2::SetMetric | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 10e4662536dbe8fef8c250122d22520df1736cf8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352577"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
Diese Methode wird einen Registrierungswert, der eine Metrik genannt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetMetric(
   LPCOLESTR pszMetric,
   VARIANT   varValue
);
```

```csharp
int SetMetric(
   string pszMetric,
   object varValue
);
```

## <a name="parameters"></a>Parameter
`pszMetric`\
[in] Der metrikname.

`varValue`\
[in] Gibt den Wert der Metrik.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Eine Metrik ist ein Registrierungswert verwendet, um einer Debug-Engine-Verhalten zu ändern oder Kündigen Sie die unterstützten Funktionen. Diese Methode kann den Aufruf der geeigneten Form der Weiterleiten der [SDK-Hilfsprogramme zum Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) Funktion `SetMetric`.

## <a name="see-also"></a>Siehe auch
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [SDK-Hilfsprogramme für das Debugging](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)