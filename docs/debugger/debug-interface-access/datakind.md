---
title: DataKind | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DataKind enumeration
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31be0615fd7d1da279ecf414260af21cb8239dc8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745285"
---
# <a name="datakind"></a>DataKind
Gibt den bestimmten Bereich eines Daten Werts an.

## <a name="syntax"></a>Syntax

```C++
enum DataKind {
    DataIsUnknown,
    DataIsLocal,
    DataIsStaticLocal,
    DataIsParam,
    DataIsObjectPtr,
    DataIsFileStatic,
    DataIsGlobal,
    DataIsMember,
    DataIsStaticMember,
    DataIsConstant
};
```

## <a name="elements"></a>Elements
Das Daten Symbol ' dataisunknown ' kann nicht bestimmt werden.

Das dataislocal-Datenelement ist eine lokale Variable.

Das dataisstaticlocal-Datenelement ist eine statische lokale Variable.

Dataisparam-Datenelement ist ein formaler Parameter.

Dataisobjectptr-Datenelement ist ein Objekt Zeiger (`this`).

Das dataisfilestatic-Datenelement ist eine Datei bezogene Variable.

Das dataisglobal-Datenelement ist eine globale Variable.

Dataismember-Datenelement ist eine Objektmember-Variable.

Das dataisstaticmember-Datenelement ist eine statische Klassen Variable.

Dataisconstant-Datenelement ist ein konstanter Wert.

## <a name="remarks"></a>Hinweise
Die Werte in dieser Enumeration werden von der [idiasymmetribol:: get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) -Methode zurückgegeben.

## <a name="requirements"></a>Anforderungen
Header: cvconst.h

## <a name="see-also"></a>Siehe auch
- [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)
