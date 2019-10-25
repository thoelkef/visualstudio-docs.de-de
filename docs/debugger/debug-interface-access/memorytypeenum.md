---
title: MemoryTypeEnum | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0710ec5cdfcfcb59407d18b43b885603f017fdb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738636"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
Gibt den Typ des zu zuzurufenden Speichers an.

## <a name="syntax"></a>Syntax

```C++
enum MemoryTypeEnum {
    MemTypeCode,
    MemTypeData,
    MemTypeStack,
    MemTypeAny = -1
};
```

#### <a name="parameters"></a>Parameter
`MemTypeCode` nur auf Code Arbeitsspeicher zugreift.

`MemTypeData` greift auf Daten oder den Stapel Speicher zu.

`MemTypeStack` nur auf den Stapel Speicher zugreift.

`MemTypeAny` auf eine beliebige Art von Arbeitsspeicher zugreift.

## <a name="remarks"></a>Hinweise
Die Werte in dieser Enumeration werden an die [IDiaStackWalkHelper:: Read Memory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) -Methode übermittelt, um den Zugriff auf verschiedene Arbeitsspeicher Typen einzuschränken.

## <a name="requirements"></a>Anforderungen
Header: cvconst.h

## <a name="see-also"></a>Siehe auch
- [Enumerationen und Strukturen](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
