---
title: IDebugExpressionContext2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::GetName
helpviewer_keywords:
- IDebugExpressionContext2::GetName
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 500d5c1788e837a27b4affada50ecc59db122e8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729667"
---
# <a name="idebugexpressioncontext2getname"></a>IDebugExpressionContext2::GetName
Ruft den Namen des Auswertungskontexts ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetName( 
   BSTR* pbstrName
);
```

```csharp
int GetName( 
   out string pbstrName
);
```

## <a name="parameters"></a>Parameter
`pbstrName`\
[out] Gibt den Namen des Auswertungskontexts zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Der Name ist die Beschreibung dieses Evaluierungskontexts. Es ist in der Regel etwas, das von einem Ausdrucksevaluator analysiert werden kann, die auf diesen genauen Auswertungskontext verweist. In C++ lautet der Name beispielsweise wie folgt:

```
"{ function-name, source-file-name, module-file-name }"
```

## <a name="see-also"></a>Weitere Informationen
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
