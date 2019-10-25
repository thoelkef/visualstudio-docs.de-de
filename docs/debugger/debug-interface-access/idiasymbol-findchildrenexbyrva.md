---
title: 'Idiasymmetribol:: findChildren-exbyrva | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByRVA
ms.assetid: cbc57c6c-7d64-4469-a114-1dd6671e5ec5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c76bcfee39deb6382199fc652ce5f3a686ac1626
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741251"
---
# <a name="idiasymbolfindchildrenexbyrva"></a>IDiaSymbol::findChildrenExByRVA
Ruft die untergeordneten Elemente des Symbols ab, die bei einer angegebenen relativen virtuellen Adresse (RVA) gültig sind.

## <a name="syntax"></a>Syntax

```C++
HRESULT findChildrenExByRVA ( 
   enum SymTagEnum   symtag,
   LPCOLESTR         name,
   DWORD             compareFlags,
   DWORD             address,
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

 `address`

in Gibt die RVA an.

 `ppResult`

vorgenommen Gibt ein [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) -Objekt zurück, das eine Liste der abgerufenen untergeordneten Symbole enthält.

## <a name="return-value"></a>Rückgabewert
 Gibt `S_OK` zurück, wenn mindestens ein untergeordnetes Element des Symbols gefunden wurde, oder gibt `S_FALSE` zurück, wenn keine untergeordneten Elemente gefunden wurden. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Zu den lokalen Symbolen, die zurückgegeben werden, gehören Informationen zum Live Bereich.

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