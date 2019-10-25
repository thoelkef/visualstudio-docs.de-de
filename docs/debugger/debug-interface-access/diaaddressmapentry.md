---
title: DiaAddressMapEntry | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 54b326116b1e1b677a997b264cf0c168a93febb0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745261"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
Beschreibt einen Eintrag in einer Adress Zuordnung.

## <a name="syntax"></a>Syntax

```C++
struct DiaAddressMapEntry {
    DWORD rva,
    DWORD rvaTo
};
```

## <a name="elements"></a>Elements
`rva` eine relative virtuelle Adresse (RVA) in Image A.

`rvaTo` die relative virtuelle Adresse `rva` die in Image B zugeordnet ist.

## <a name="remarks"></a>Hinweise
Eine Adress Zuordnung bietet eine Übersetzung von einem Bild Layout (a) zu einem anderen (B). Ein Array von `DiaAddressMapEntry` Strukturen, sortiert nach `rva` definiert eine Adress Zuordnung.

Führen Sie die folgenden Schritte aus, um eine Adresse `addrA` in Image a in eine Adresse `addrB` in Abbildung B zu übersetzen:

1. Durchsuchen Sie die Zuordnung für den Eintrag `e`, wobei die größte `rva` kleiner oder gleich `addrA` ist.

2. Legen Sie `delta = addrA - e.rva` fest.

3. Legen Sie `addrB = e.rvaTo + delta` fest.

    Ein Array von `DiaAddressMapEntry` Strukturen wird an die [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) -Methode übermittelt.

## <a name="requirements"></a>Anforderungen
Header: dia2.h

## <a name="see-also"></a>Siehe auch
- [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
