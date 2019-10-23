---
title: BasicType | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BasicType enumeration
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fff76abdecdd8613a462225278053ef4f6d9694
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745479"
---
# <a name="basictype"></a>BasicType
Gibt den Basistyp des Symbols an.

## <a name="syntax"></a>Syntax

```C++
enum BasicType {
    btNoType   = 0,
    btVoid     = 1,
    btChar     = 2,
    btWChar    = 3,
    btInt      = 6,
    btUInt     = 7,
    btFloat    = 8,
    btBCD      = 9,
    btBool     = 10,
    btLong     = 13,
    btULong    = 14,
    btCurrency = 25,
    btDate     = 26,
    btVariant  = 27,
    btComplex  = 28,
    btBit      = 29,
    btBSTR     = 30,
    btHresult  = 31,
    btChar16   = 32,  // char16_t
    btChar32   = 33,  // char32_t
};
```

## <a name="elements"></a>Elements
btnotype: Es wurde kein Basistyp angegeben.

der Typ "btvoid Basic" ist eine `void`.

der Typ "btchar Basic" ist eine `char`C++ (C/Typ).

der Typ "btwchar Basic" ist ein breit Zeichen (Unicode) (`WCHAR`).

der Typ "btint Basic" ist `signed int`C++ (C/Typ).

der Typ "btuint Basic" ist `unsigned int`C++ (C/Typ).

der btfloat-Basistyp ist eine Gleit Komma Zahl (`FLOAT`).

der btbcd-Basistyp ist ein Binär codiertes Dezimaltrennzeichen (`BCD`).

der Typ "btbool Basic" ist ein boolescher Wert (`BOOL`).

der Basistyp btlong ist ein `long int` (CC++ /Type).

der Typ "btulong Basic" ist ein `unsigned long int`C++ (C/Typ).

btcurrency Basic-Typ ist Currency.

der btdate-Basistyp ist "Date/Time" (`DATE`).

der btvariant-Basistyp ist eine Variablentyp Struktur (`VARIANT`).

der Typ "btcomplex Basic" ist eine komplexe Zahl.

der Typ "btbit Basic" ist ein Bit.

der btbstr-Basistyp ist eine einfache oder binäre Zeichenfolge (`BSTR`).

der Basistyp bthresult ist eine `HRESULT`.

## <a name="remarks"></a>Hinweise
Die Werte in dieser Enumeration werden von der [idiasymmetribol:: get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) -Methode zurückgegeben.

## <a name="requirements"></a>Anforderungen
Header: cvconst.h

## <a name="see-also"></a>Siehe auch
- [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
