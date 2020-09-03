---
title: 'Idebugsymbolprovider:: getnextaddress | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetNextAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNextAddress method
ms.assetid: 704eeb94-cb13-49d1-82b6-7d83ed0f19c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9b314ab7006d6bbe65136451aeee6c5200cf7980
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719195"
---
# <a name="idebugsymbolprovidergetnextaddress"></a>IDebugSymbolProvider::GetNextAddress
Ruft die debugadresse ab, die einer bestimmten debugadresse in einer Methode folgt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetNextAddress( 
   IDebugAddress*  pAddress,
   BOOL            fStatementOnly,
   IDebugAddress** ppAddress
);
```

```csharp
int GetNextAddress( 
   IDebugAddress     pAddress,
   bool              fStatementOnly,
   out IDebugAddress ppAddress
);
```

## <a name="parameters"></a>Parameter
`pAddress`\
in Die angegebene debugadresse.

`fStatementOnly`\
in Wenn true, werden die debugadressen auf eine einzige Anweisung beschränkt.

`ppAddress`\
vorgenommen Gibt die nächste debugadresse zurück.

## <a name="return-value"></a>Rückgabewert
 Gibt einen gültigen zurück `HRESULT` , in der Regel S_OK.

## <a name="see-also"></a>Weitere Informationen
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
