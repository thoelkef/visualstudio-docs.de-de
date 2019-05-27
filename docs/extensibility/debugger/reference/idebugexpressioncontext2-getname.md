---
title: IDebugExpressionContext2::GetName | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionContext2::GetName
helpviewer_keywords:
- IDebugExpressionContext2::GetName
ms.assetid: c2b70d22-17af-4986-a7e3-930910367216
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1961ac778dab2d17a87748cae8e1210f6b13422d
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66201063"
---
# <a name="idebugexpressioncontext2getname"></a>IDebugExpressionContext2::GetName
Ruft den Namen des dem Auswertungskontext ab.

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
[out] Gibt den Namen des dem Auswertungskontext zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Der Name ist die Beschreibung dieses Kontexts für die Auswertung. Es ist in der Regel etwas, das von einer ausdrucksauswertung analysiert werden können, die auf diese genaue Evaluierungskontext verweist. Beispielsweise ist in C++ der Name wie folgt:

```
"{ function-name, source-file-name, module-file-name }"
```

## <a name="see-also"></a>Siehe auch
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)