---
title: 'Idiasymmetribol:: findinlineelinesbyrva | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ac108db1-9dbf-4dc4-bf48-159ca8d3725c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 737bc647cf3f5b64bdd8c48f7c827e8ef86a1386
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741203"
---
# <a name="idiasymbolfindinlineelinesbyrva"></a>IDiaSymbol::findInlineeLinesByRVA
Ruft eine Enumeration ab, mit der ein Client die Zeilennummern Informationen aller Funktionen, die direkt oder indirekt Inline sind, in diesem Symbol innerhalb der angegebenen relativen virtuellen Adresse (RVA) durchlaufen kann.

## <a name="syntax"></a>Syntax

```C++
HRESULT findInlineeLinesByRVA (    DWORD                 rva,   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parameter
 `rva`

in Gibt die Adresse als RVA an.

 `length`

in Gibt den Adressbereich in Byte an, der mit dieser Abfrage abgedeckt werden soll.

 `ppResult`

vorgenommen Enthält ein `IDiaEnumLineNumbers` Objekt, das die Liste der abgerufenen Zeilennummern enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)