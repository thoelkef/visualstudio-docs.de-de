---
title: 'IDiaSession:: findinlineelinesbyrva | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7a74d5ee-0dbf-47c0-92b4-47ec03b13ce9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6cf587d9e369ac32c72df5e1fd7a9005ef417177
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742208"
---
# <a name="idiasessionfindinlineelinesbyrva"></a>IDiaSession::findInlineeLinesByRVA
Ruft eine Enumeration ab, mit der ein Client die Zeilennummerinformationen aller Funktionen durchlaufen kann, die direkt oder indirekt durch das angegebene übergeordnete Symbol Inline sind und in der angegebenen relativen virtuellen Adresse (RVA) enthalten sind.

## <a name="syntax"></a>Syntax

```C++
HRESULT findInlineeLinesByRVA ( 
   IDiaSymbol*           parent,
   DWORD                 rva,
   DWORD                 length,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parameter
 `parent`

in Ein `IDiaSymbol`-Objekt, das das übergeordnete Element darstellt.

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