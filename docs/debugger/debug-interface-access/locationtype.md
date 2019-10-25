---
title: LocationType | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- LocationType enumeration
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc40cc6cc8e821db7c28a4647e36e7bad241b29f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738648"
---
# <a name="locationtype"></a>LocationType
Gibt die Art der Speicherort Informationen an, die in einem Symbol enthalten sind.

## <a name="syntax"></a>Syntax

```C++
enum LocationType {
    LocIsNull,
    LocIsStatic,
    LocIsTLS,
    LocIsRegRel,
    LocIsThisRel,
    LocIsEnregistered,
    LocIsBitField,
    LocIsSlot,
    LocIsIlRel,
    LocInMetaData,
    LocIsConstant,
    LocTypeMax
};
```

## <a name="elements"></a>Elements
`LocIsNull` Speicherort Informationen sind nicht verfügbar.

`LocIsStatic` Speicherort ist statisch.

`LocIsTLS` Speicherort befindet sich im lokalen Thread Speicher.

`LocIsRegRel` Speicherort ist Register-relative.

`LocIsThisRel` Speicherort ist `this`-relative.

`LocIsEnregistered` Speicherort befindet sich in einem Register.

`LocIsBitField` Speicherort befindet sich in einem Bitfeld.

`LocIsSlot` Speicherort ist ein MSIL-Slot (Microsoft Intermediate Language).

`LocIsIlRel` Speicherort ist MSIL-relative.

`LocInMetaData` Speicherort ist in den Metadaten.

`LocIsConstant` Speicherort ist ein konstanter Wert.

`LocTypeMax` die Anzahl der Speicherort Typen in dieser Enumeration.

## <a name="remarks"></a>Hinweise
Die Eigenschaften, die für die [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Schnittstelle verfügbar sind, hängen von der Position des Symbols in der Bilddatei ab. Weitere Informationen finden Sie unter [Symbol Speicherorte](../../debugger/debug-interface-access/symbol-locations.md).

Die Werte in dieser Enumeration werden von einem Rückruf der [idiasymmetribol:: get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) -Methode zurückgegeben.

## <a name="requirements"></a>Anforderungen
Header: cvconst.h

## <a name="see-also"></a>Siehe auch
- [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [Symbolspeicherorte](../../debugger/debug-interface-access/symbol-locations.md)
