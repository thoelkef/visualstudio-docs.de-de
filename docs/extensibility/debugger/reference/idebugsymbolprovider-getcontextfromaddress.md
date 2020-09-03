---
title: 'Idebugsymbolprovider:: getcontextfromaddress | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetContextFromAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetContextFromAddress method
ms.assetid: 7a27d56f-20d4-4e5c-af7b-7307d3aff0a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca6c3fa5d657100ecce55de31117ea2c2532374d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719250"
---
# <a name="idebugsymbolprovidergetcontextfromaddress"></a>IDebugSymbolProvider::GetContextFromAddress
Diese Methode ordnet eine debugadresse einem Dokument Kontext zu.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetContextFromAddress( 
   IDebugAddress*           pAddress,
   IDebugDocumentContext2** ppDocContext
);
```

```csharp
int GetContextFromAddress(
   IDebugAddress              pAddress,
   out IDebugDocumentContext2 ppDocContext
);
```

## <a name="parameters"></a>Parameter
`pAddress`\
in Die debugadresse, wie von einer [idebugaddress](../../../extensibility/debugger/reference/idebugaddress.md) -Schnittstelle dargestellt.

`ppDocContext`\
vorgenommen Gibt einen Dokument Kontext zurück, der durch eine [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) -Schnittstelle dargestellt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
