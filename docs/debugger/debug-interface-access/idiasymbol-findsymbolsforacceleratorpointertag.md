---
title: IDiaSymbol::findSymbolsForAcceleratorPointerTag | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fb66852c-c5f7-4140-b9fe-20cb4e51a9fe
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7bf55f372b9beb0a4cb0feda0dc5869ee9eb7c5f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56613530"
---
# <a name="idiasymbolfindsymbolsforacceleratorpointertag"></a>IDiaSymbol::findSymbolsForAcceleratorPointerTag
Gibt die Anzahl der Tags von Accelerator-Zeiger in einer C++ AMP-Stub-Funktion zurück.

## <a name="syntax"></a>Syntax

```C++
HRESULT findSymbolsForAccleratorPointerTag (
   DWORD             tagValue,
   IDiaEnumSymbols** ppResult);
```

#### <a name="parameters"></a>Parameter
 `tagValue`

[in] Der Wert des Zeigers-Tag, für den die symboldatensätze Pointee gefunden werden.

 `ppResult`

[out] Ein Zeiger auf ein `IDiaEnumSymbols` Schnittstellenzeiger, der mit dem Ergebnis initialisiert wurde.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)