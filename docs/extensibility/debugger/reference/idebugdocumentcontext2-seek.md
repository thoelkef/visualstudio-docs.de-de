---
title: IDebugDocumentContext2::Seek | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::Seek
helpviewer_keywords:
- IDebugDocumentContext2::Seek
ms.assetid: 71501356-8a82-4d36-b354-6625bdd2baa0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 413b1416adcd4b20231666e25f6a8044e632198b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325429"
---
# <a name="idebugdocumentcontext2seek"></a>IDebugDocumentContext2::Seek
Verschiebt den Dokumentenkontext durch eine angegebene Anzahl von Anweisungen oder Zeilen an.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Seek( 
   int                      nCount,
   IDebugDocumentContext2** ppDocContext
);
```

```cpp
int Seek( 
   int                        nCount,
   out IDebugDocumentContext2 ppDocContext
);
```

## <a name="parameters"></a>Parameter
`nCount`\
[in] Die Anzahl der Anweisungen oder Zeilen, je nach Dokumentenkontext verschieben.

`ppDocContext`\
[out] Gibt eine neue [idebugdocumentcontext2 angegeben](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Objekt mit der die neue Position.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)