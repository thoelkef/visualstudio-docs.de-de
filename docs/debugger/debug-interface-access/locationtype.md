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
ms.openlocfilehash: faff61833cb130902efbd64d60a16f74c507a3e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62834128"
---
# <a name="locationtype"></a>LocationType
Gibt die Art der Standortinformationen in ein Symbol an.

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
`LocIsNull` Informationen zum Speicherort ist nicht verfügbar.

`LocIsStatic` Speicherort ist statisch.

`LocIsTLS` Speicherort ist im lokalen Threadspeicher.

`LocIsRegRel` Speicherort ist relativ registrieren.

`LocIsThisRel` Speicherort ist `this`-relative.

`LocIsEnregistered` Speicherort ist in einem Register.

`LocIsBitField` Speicherort ist in einem Bitfeld.

`LocIsSlot` Speicherort ist ein Microsoft Intermediate Language (MSIL)-Slot.

`LocIsIlRel` Der Speicherort ist relativ MSIL.

`LocInMetaData` Speicherort ist in den Metadaten.

`LocIsConstant` Speicherort ist in einem konstanten Wert.

`LocTypeMax` Die Anzahl der Typen in dieser Enumeration.

## <a name="remarks"></a>Hinweise
Die Eigenschaften für die [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Schnittstelle hängen Speicherort des Symbols, in der Imagedatei. Weitere Informationen finden Sie unter [Orte für Symboldateien](../../debugger/debug-interface-access/symbol-locations.md).

Die Werte in dieser Enumeration werden zurückgegeben, durch einen Aufruf der [idiasymbol:: Get_locationtype](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) Methode.

## <a name="requirements"></a>Anforderungen
Header: cvconst.h

## <a name="see-also"></a>Siehe auch
- [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)
- [Symbolspeicherorte](../../debugger/debug-interface-access/symbol-locations.md)
