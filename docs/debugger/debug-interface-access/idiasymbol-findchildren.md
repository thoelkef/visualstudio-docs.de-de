---
title: 'Idiasymmetribol:: findChildren | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildren method
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3c62271f6324e50a68de393cfa668c69ba4a935
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741299"
---
# <a name="idiasymbolfindchildren"></a>IDiaSymbol::findChildren
Ruft die untergeordneten Elemente des Symbols ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT findChildren ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parameter
 `symtag`

in Gibt die Symbol Tags der untergeordneten Elemente an, die abgerufen werden sollen, wie in der [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)definiert. Legen Sie auf `SymTagNull` fest, damit alle untergeordneten Elemente abgerufen werden.

 `name`

in Gibt den Namen der untergeordneten Elemente an, die abgerufen werden sollen. Legen Sie auf `NULL` fest, damit alle untergeordneten Elemente abgerufen werden.

 `compareFlags`

in Gibt die auf die namens Übereinstimmung angewendeten Vergleichs Optionen an Werte aus der Enumeration-Enumeration von [NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) können allein oder in Kombination verwendet werden.

 `ppResult`

vorgenommen Gibt ein [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) -Objekt zurück, das eine Liste der abgerufenen untergeordneten Symbole enthält.

## <a name="return-value"></a>Rückgabewert
 Gibt `S_OK` zurück, wenn mindestens ein untergeordnetes Element des Symbols gefunden wurde, oder gibt `S_FALSE` zurück, wenn keine untergeordneten Elemente gefunden wurden. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode ist identisch mit dem Aufruf der [IDiaSession:: findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md) -Methode mit diesem Symbol als ersten Parameter.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [NameSearchOptions-Enumeration](../../debugger/debug-interface-access/namesearchoptions.md)