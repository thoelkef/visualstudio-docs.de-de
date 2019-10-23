---
title: 'Idiasymmetribol:: findsymbolsbyrvaforacceleratorpointertag | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f0d05946db816e6bd209e364e11d5091163941a4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741153"
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
Wenn ein entsprechender Tagwert angegeben ist, gibt diese Methode eine Enumeration von Symbolen zurück, die in dieser stubfunktion an einer angegebenen relativen virtuellen Adresse enthalten sind.

## <a name="syntax"></a>Syntax

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag (
   DWORD             tagValue,
   DWORD             rva,
   IDiaEnumSymbols** ppResult);
```

#### <a name="parameters"></a>Parameter
 `tagValue`

in Der zeigertag Wert, für den die pointee-Symbol Datensätze gefunden werden.

 `rva`

in Die RVA, mit der die Symbole gefiltert werden, die der pointee-Variablen mit dem angegebenen Tagwert entsprechen.

 `ppResult`

vorgenommen Ein Zeiger auf einen `IDiaEnumSymbols` Schnittstellen Zeiger, der mit dem Ergebnis initialisiert wird.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode wird nur für eine `IDiaSymbol`-Schnittstelle aufgerufen, die einer Zugriffstasten-Stub-Funktion entspricht.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)