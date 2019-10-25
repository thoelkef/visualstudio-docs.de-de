---
title: UdtKind | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- UdtKind enumeration
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45ed43bf65c38890ca7ebda1a6b1719532697eae
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738448"
---
# <a name="udtkind"></a>UdtKind
Beschreibt die Vielzahl von benutzerdefinierten Typen (User-Defined Type, UDT).

## <a name="syntax"></a>Syntax

```C++
enum UdtKind {
    UdtStruct,
    UdtClass,
    UdtUnion,
    UdtInterface
};
```

## <a name="elements"></a>Elements
Udtstruct UDT ist eine Struktur.

Udtclass UDT ist eine-Klasse.

Udtunion UDT ist eine Union.

Udtinterface UDT ist eine Schnittstelle.

## <a name="remarks"></a>Hinweise
Die Werte in dieser Enumeration werden von der [idiasymmetribol:: get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md) -Methode zurückgegeben.

## <a name="requirements"></a>Anforderungen
Header: cvconst.h

## <a name="see-also"></a>Siehe auch
- [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)
