---
title: IDebugSymbolProvider::GetLanguage | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetLanguage
helpviewer_keywords:
- IDebugSymbolProvider::GetLanguage method
ms.assetid: e4142183-3d8b-418f-907f-4ee4c753d8ce
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dfa11a1df6460c08431d7b23fabe5d94674baad2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347601"
---
# <a name="idebugsymbolprovidergetlanguage"></a>IDebugSymbolProvider::GetLanguage
Diese Methode ruft die Sprache, die zum Kompilieren des Codes an der debugadresse verwendet wurde.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetLanguage( 
   IDebugAddress* pAddress,
   GUID*          pguidLanguage,
   GUID*          pguidLanguageVendor
);
```

```csharp
int GetLanguage(
   IDebugAddress pAddress,
   out Guid      pguidLanguage,
   out Guid      pguidLanguageVendor
);
```

## <a name="parameters"></a>Parameter
`pAddress`\
[in] Durch dargestellt wird ein Adressobjekt ein [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Schnittstelle.

`pguidLanguage`\
[out] Gibt eine `GUID` , der die Sprache angibt.

`pguidLanguageVendor`\
[out] Gibt eine `GUID` , die den Compilerhersteller angibt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Die Debug-Engine ruft diese Methode zum Abrufen der Informationen, die Auswahl die richtigen ausdrucksauswertung erforderlich.

## <a name="see-also"></a>Siehe auch
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)