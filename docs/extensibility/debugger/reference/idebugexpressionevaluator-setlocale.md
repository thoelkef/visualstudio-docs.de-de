---
title: IDebugExpressionEvaluator::SetLocale | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::SetLocale
helpviewer_keywords:
- IDebugExpressionEvaluator::SetLocale method
ms.assetid: d3d2027d-74e2-4ae6-bcc7-59d12f873b7c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 57ddee6e1796159c505b67982f25d1ba09684561
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729471"
---
# <a name="idebugexpressionevaluatorsetlocale"></a>IDebugExpressionEvaluator::SetLocale
Diese Methode legt die Sprache fest, die zum Erstellen druckbarer Ergebnisse verwendet werden soll.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetLocale( 
   WORD wLangID
);
```

```csharp
int SetLocale(
   ushort wLangID
);
```

## <a name="parameters"></a>Parameter
`wLangID`\
[in] Der Sprachbezeichner.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode kann mehrmals aufgerufen werden, während der Ausdrucksevaluator (EE) geladen wird, sodass der EE die Sprache spontan wechseln kann. Der EE verwendet dieses Gebietsschema, um Fehlermeldungen und Zeichenfolgen in der entsprechenden Sprache zurückzugeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
