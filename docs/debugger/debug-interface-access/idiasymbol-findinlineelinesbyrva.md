---
title: IDiaSymbol::findInlineeLinesByRVA | Microsoft-Dokumentation
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
ms.openlocfilehash: bdcb85db51a3fcfca434af9d39bc88587a0e5cdc
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "62831756"
---
# <a name="idiasymbolfindinlineelinesbyrva"></a>IDiaSymbol::findInlineeLinesByRVA
Ruft eine Enumeration, die ermöglicht einem Client die Zeilennummerninformationen aller Funktionen durchlaufen, die inline erweitert wird, direkt oder indirekt in dieses Symbols in die angegebene relative virtuelle Adresse (RVA) ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT findInlineeLinesByRVA (    DWORD                 rva,   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parameter
 `rva`

[in] Gibt die Adresse als eine RVA an.

 `length`

[in] Gibt den Adressbereich in Anzahl von Bytes, die mit dieser Abfrage abzudecken.

 `ppResult`

[out] Enthält eine `IDiaEnumLineNumbers` Objekt, das die Liste der Zeilennummern enthält, die abgerufen werden.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)