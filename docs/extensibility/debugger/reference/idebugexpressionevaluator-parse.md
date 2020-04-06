---
title: IDebugExpressionEvaluator::Parse | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d1af9d3f253a9849f54bb5a50d432b98eb4ad7b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729494"
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
Diese Methode konvertiert eine Ausdruckszeichenfolge in einen analysierten Ausdruck.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Parse( 
   LPCOLESTR                upstrExpression,
   PARSEFLAGS               dwFlags,
   UINT                     nRadix,
   BSTR*                    pbstrError,
   UINT*                    pichError,
   IDebugParsedExpression** ppParsedExpression
);
```

```csharp
int Parse(
   string                     upstrExpression,
   enum_PARSEFLAGS            dwFlags,
   uint                       nRadix,
   out string                 pbstrError,
   out uint                   pichError,
   out IDebugParsedExpression ppParsedExpression
);
```

## <a name="parameters"></a>Parameter
`upstrExpression`\
[in] Die zu analysierende Ausdruckszeichenfolge.

`dwFlags`\
[in] Eine Auflistung von [PARSEFLAGS-Konstanten,](../../../extensibility/debugger/reference/parseflags.md) die bestimmen, wie der Ausdruck analysiert werden soll.

`nRadix`\
[in] Radix zur Interpretation numerischer Informationen.

`pbstrError`\
[out] Gibt den Fehler als lesbaren Text zurück.

`pichError`\
[out] Gibt die Zeichenposition des Anfangs des Fehlers in der Ausdruckszeichenfolge zurück.

`ppParsedExpression`\
[out] Gibt den analysierten Ausdruck in einem [IDebugParsedExpression-Objekt](../../../extensibility/debugger/reference/idebugparsedexpression.md) zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode erzeugt einen analysierten Ausdruck und keinen tatsächlichen Wert. Ein analysierter Ausdruck kann ausgewertet werden, d. h. in einen Wert konvertiert werden.

## <a name="see-also"></a>Weitere Informationen
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)
