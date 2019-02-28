---
title: IDiaEnumSymbolsByAddr::symbolByRVA | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsByAddr::symbolByRVA method
ms.assetid: f7828029-f2ee-4ccd-afac-785adc60a4c8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38d7b0cb8564743ab35cac20cdcb352cdbca48d3
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56632588"
---
# <a name="idiaenumsymbolsbyaddrsymbolbyrva"></a>IDiaEnumSymbolsByAddr::symbolByRVA
Positioniert den Enumerator durch eine Suche durch relative virtuelle Adresse (RVA).

## <a name="syntax"></a>Syntax

```C++
HRESULT symbolByRVA ( 
   DWORD**      relativeVirtualAddress,
   IDiaSymbol** ppsymbol
);
```

#### <a name="parameters"></a>Parameter
 relativeVirtualAddress

[in] Adresse relativ zum Anfang des Image.

 ppsymbol

[out] Gibt eine [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekt, das das Symbol gefunden darstellt.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` , wenn das Symbol nicht gefunden werden konnte. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)
- [IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)