---
title: IDebugSymbolProvider::GetAddressesFromContext | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 77306706c15be37a975742be917523095bec587f
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226438"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
Diese Methode ordnet einem Dokumentkontext in ein Array von Debug-Adressen.

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

 [in] Der Dokumentenkontext.

 `fStatmentOnly`\

 [in] True gibt an, beschränkt die Debug-Adressen zu einer einzigen Anweisung.

 `ppEnumBegAddresses`\

 [out] Gibt einen Enumerator für die Debug-Startadressen dieser Anweisung oder der Zeile zugeordnet.

 `ppEnumEndAddresses`\

 [out] Gibt eine [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) Enumerator für die abschließende Debug-Adressen, die dieser Anweisung oder der Zeile zugeordnet.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Ein Dokumentenkontext liegt in der Regel im Bereich von Quellzeilen. Diese Methode bietet die Start- und endadressen Debuggen, die mit diesen Zeilen verknüpft ist. Einige Sprachen ermöglichen die Anweisungen, die sich erstrecken, mehrere Zeilen oder Zeilen, die mehr als eine Anweisung enthält. Diese Methode bietet ein Flag, um die Debug-Adressen, die einer einzelnen Anweisung zu beschränken.

 Es ist möglich, dass eine einzelne Anweisung, um mehrere Debug-Adressen, wie im Fall von Vorlagen zu erhalten.

## <a name="see-also"></a>Siehe auch
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)