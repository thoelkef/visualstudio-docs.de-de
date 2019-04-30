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
ms.openlocfilehash: 03e82a8c17b33aa085b4ed64b9ba609bee183e1d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829731"
---
# <a name="basictype"></a>BasicType
Gibt an, die grundlegende Symboltyp.

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
BtNoType kein Basistyp angegeben ist.

BtVoid Basistyp ist eine `void`.

BtChar Basistyp ist eine `char` (C /C++ Typ).

BtWChar Basistyp ist ein Breitzeichen (Unicode) ist (`WCHAR`).

BtInt Basistyp ist `signed int` (C /C++ Typ).

BtUInt Basistyp ist `unsigned int` (C /C++ Typ).

BtFloat Basistyp ist eine Gleitkommazahl (`FLOAT`).

BtBCD Basistyp ist eine Dezimalzahl Binär codierte (`BCD`).

BtBool Basistyp ist ein boolescher Wert (`BOOL`).

BtLong Basistyp ist eine `long int` (C /C++ Typ).

BtULong Basistyp ist ein `unsigned long int` (C /C++ Typ).

BtCurrency Basistyp ist die Währung.

BtDate Basistyp ist die Datum/Uhrzeit (`DATE`).

BtVariant Basistyp ist eine Variable vom Typ-Struktur (`VARIANT`).

BtComplex Basistyp ist die komplexe Zahl.

BtBit Basistyp ist ein wenig.

BtBSTR Basistyp ist eine grundlegende oder binäre Zeichenfolge (`BSTR`).

BtHresult Basistyp ist ein `HRESULT`.

## <a name="remarks"></a>Hinweise
Die Werte in dieser Enumeration werden zurückgegeben, durch die [idiasymbol:: Get_basetype](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) Methode.

## <a name="requirements"></a>Anforderungen
Header: cvconst.h

## <a name="see-also"></a>Siehe auch
- [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)
- [IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)
