---
title: IDebugCodeContext2::GetDocumentContext | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a12838db0687fd7ebe20a5c576db0e06ece49107
ms.sourcegitcommit: 34807a6b6105ae7839adde8ff994c85182ad3aff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2019
ms.locfileid: "67342400"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Ruft ab, der Dokumentenkontext, der an diesen Codekontext entspricht. Den Dokumentenkontext darstellt, eine Position in der Quelldatei, die auf den Quellcode entspricht, die diese Anweisung generiert wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetDocumentContext( 
   IDebugDocumentContext2** ppSrcCxt
);
```

```csharp
int GetDocumentContext( 
   out IDebugDocumentContext2 ppSrcCxt
);
```

## <a name="parameters"></a>Parameter
`ppSrcCxt`\
[out] Gibt die [idebugdocumentcontext2 angegeben](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Objekt, das den Codekontext entspricht. Wenn `S_OK` zurückgegeben wird, diesen muss nicht`null`.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Eine Debug-Engine sollte einen Fehlercode zurück, wie z. B. `E_FAIL` bei der `out` Parameter `null` z. B. wenn der Codekontext keine Position der zugehörigen Datenquelle hat.

## <a name="remarks"></a>Hinweise
 Im Allgemeinen kann der Dokumentenkontext betrachtet werden als eine Position in einer Quelldatei während der Codekontext eine Position ein Code-Anweisung in einen Stream für die Ausführung ist.

## <a name="see-also"></a>Siehe auch
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
