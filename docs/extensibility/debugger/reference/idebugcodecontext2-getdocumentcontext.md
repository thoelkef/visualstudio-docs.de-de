---
title: IDebugCodeContext2::GetDocumentContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 46510ce794ea30fdd365a77007b962a1eafd5d31
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734344"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
Ruft den Dokumentkontext ab, der diesem Codekontext entspricht. Der Dokumentkontext stellt eine Position in der Quelldatei dar, die dem Quellcode entspricht, der diese Anweisung generiert hat.

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
[out] Gibt das [IDebugDocumentContext2-Objekt](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) zurück, das dem Codekontext entspricht. Wenn `S_OK` zurückgegeben wird, sollte ths nicht-`null`sein.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Ein Debugmodul sollte einen Fehlercode zurückgeben, z. `E_FAIL` B. wenn der `out` Parameter z. B. wenn dem Codekontext keine Quellposition zugeordnet ist. `null`

## <a name="remarks"></a>Bemerkungen
 Im Allgemeinen kann der Dokumentkontext als Position in einer Quelldatei betrachtet werden, während der Codekontext eine Position einer Codeanweisung in einem Ausführungsstream ist.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
