---
title: IDebugExpressionEvaluator2::GetService | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5428606ad54c7938037c3ffecf04f1cfe41787c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729349"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Ruft ein Dienstobjekt mit seinem eindeutigen Bezeichner ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetService (
   GUID        uid,
   IUnknown ** ppService
);
```

```csharp
int GetService (
   Guid       uid,
   out object ppService
);
```

## <a name="parameters"></a>Parameter
`uid`\
[in] Eindeutiger Bezeichner des abzurufenden Dienstes.

`ppService`\
[out] Gibt ein Objekt zurück, das den Dienst darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Dies kann von einem Ausdrucksevaluator eines Drittanbieters verwendet werden, um Dienste von einem anderen Ausdrucksbewerter zu erhalten. Diese Methode kann beispielsweise verwendet werden, um die Schnittstelle für den Visualisierungsdienst vom Standardausdrucksauswertungsdienst abzusondern. Ausdrucksauswertungen von Drittanbietern müssen diese Schnittstelle wahrscheinlich nicht implementieren.

## <a name="see-also"></a>Weitere Informationen
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
