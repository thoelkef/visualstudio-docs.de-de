---
title: IDebugSymbolProvider::GetAddressesFromContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7cf7599cf0fc37c16467c29c2b432f1f58b172fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719430"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
Diese Methode ordnet einen Dokumentkontext einem Array von Debugadressen zu.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetAddressesFromContext( 
   IDebugDocumentContext2* pDocContext,
   BOOL                    fStatmentOnly,
   IEnumDebugAddresses**   ppEnumBegAddresses,
   IEnumDebugAddresses**   ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromContext(
   IDebugDocumentContext2  pDocContext,
   bool                    fStatmentOnly,
   out IEnumDebugAddresses ppEnumBegAddresses,
   out IEnumDebugAddresses ppEnumEndAddresses
);
```

## <a name="parameters"></a>Parameter
`pDocContext`\
[in] Der Dokumentkontext.

`fStatmentOnly`\
[in] Wenn TRUE, beschränkt die Debugadressen auf eine einzelne Anweisung.

`ppEnumBegAddresses`\
[out] Gibt einen Enumerator für die Startdebugadressen zurück, die dieser Anweisung oder Zeile zugeordnet sind.

`ppEnumEndAddresses`\
[out] Gibt einen [IEnumDebugAddresses-Enumerator](../../../extensibility/debugger/reference/ienumdebugaddresses.md) für die endgebenden Debugadressen zurück, die dieser Anweisung oder Zeile zugeordnet sind.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein Dokumentkontext gibt in der Regel einen Bereich von Quellzeilen an. Diese Methode stellt die Start- und Enddebugadressen bereit, die diesen Zeilen zugeordnet sind. Einige Sprachen erlauben Anweisungen, die sich über mehrere Zeilen erstrecken, oder Zeilen, die mehr als eine Anweisung enthalten. Diese Methode stellt ein Flag bereit, um die Debugadressen auf eine einzelne Anweisung zu beschränken.

 Es ist möglich, dass eine einzelne Anweisung über mehrere Debugadressen verfügt, wie im Fall von Vorlagen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
