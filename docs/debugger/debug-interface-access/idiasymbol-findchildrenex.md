---
title: 'Idiasymmetribol:: findChildren-Ex | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenEx
ms.assetid: 6e045045-da8c-4338-9423-81a1ca20c405
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26fdced012baada390cdd0a112856b592d3c923e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741267"
---
# <a name="idiasymbolfindchildrenex"></a>IDiaSymbol::findChildrenEx
Ruft die untergeordneten Elemente des Symbols ab. Zu den lokalen Symbolen, die zurückgegeben werden, gehören Live Bereichs Informationen, wenn das Programm mit der Optimierung von kompiliert wird.

## <a name="syntax"></a>Syntax

```C++
HRESULT findChildrenEx ( 
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

in Gibt die Vergleichs Optionen an, die auf die namens Übereinstimmung angewendet werden. Werte aus der Enumeration-Enumeration von [NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) können allein oder in Kombination verwendet werden.

 `ppResult`

vorgenommen Gibt ein [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) -Objekt zurück, das eine Liste der abgerufenen untergeordneten Symbole enthält.

## <a name="return-value"></a>Rückgabewert
 Gibt `S_OK` zurück, wenn mindestens ein untergeordnetes Element des Symbols gefunden wurde, oder gibt `S_FALSE` zurück, wenn keine untergeordneten Elemente gefunden wurden. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode ist die erweiterte Version von [idiasymmetribol:: findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md).

## <a name="requirements"></a>Anforderungen
 Header: Dia2.h

 Bibliothek: diaguids. lib

 DLL: msdia100.dll

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [NameSearchOptions-Enumeration](../../debugger/debug-interface-access/namesearchoptions.md)