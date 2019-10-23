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
ms.openlocfilehash: bbe338ba9d3aa6cbc795606c3fa285526afdfd36
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745359"
---
# <a name="cv_access_e"></a>CV_access_e
Gibt den Bereich der Sichtbarkeit (Zugriffsebene) von Element Funktionen und Variablen an.

## <a name="syntax"></a>Syntax

```C++
typedef enum CV_access_e {
    CV_private   = 1,
    CV_protected = 2,
    CV_public    = 3
} CV_access_e;
```

## <a name="elements"></a>Elements
CV_private Member hat privaten Zugriff.

CV_protected Member hat geschützten Zugriff.

CV_public Member hat öffentlichen Zugriff.

## <a name="remarks"></a>Hinweise
Der `friend` Zugriffsspezifizierer ist hier nicht enthalten, da er in der Regel von nicht-Member-Funktionen verwendet wird, die Zugriff auf private und geschützte Elemente der Klasse haben. Verwenden Sie die [idiasymmetribol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) -Methode, um Symbole mit `SymTagFriend` Access zu suchen.

## <a name="requirements"></a>Anforderungen
Header: cvconst.h

## <a name="see-also"></a>Siehe auch
- [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
