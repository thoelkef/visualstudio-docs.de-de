---
title: CV_access_e | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_access_e enumeration
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90230bd95e1dbcd3e4c186257c6c36faad6ba1f7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62555129"
---
# <a name="cvaccesse"></a>CV_access_e
Gibt den Bereich, Sichtbarkeit (Zugriffsebene) von Memberfunktionen und Variablen.

## <a name="syntax"></a>Syntax

```C++
typedef enum CV_access_e {
    CV_private   = 1,
    CV_protected = 2,
    CV_public    = 3
} CV_access_e;
```

## <a name="elements"></a>Elements
CV_private bindflags privaten Zugriff.

CV_protected Member hat Zugriff geschützt werden.

CV_public Element verfügt über öffentlichen Zugriff.

## <a name="remarks"></a>Hinweise
Die `friend` Zugriffsspezifizierer ist hier nicht enthalten, da sie in der Regel von nicht-Memberfunktionen verwendet wird, die Zugriff auf private oder geschützte Elemente der Klasse haben. Verwenden der [idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) Methode zum Suchen von Symbolen mit `SymTagFriend` Zugriff.

## <a name="requirements"></a>Anforderungen
Header: cvconst.h

## <a name="see-also"></a>Siehe auch
- [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
