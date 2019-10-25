---
title: 'Idiaenumsectioncontrisb:: Next | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Next method
ms.assetid: a6bb2adb-ee6d-4f3c-ab5b-e89361c8880e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61d99b0c881abdb8974e94352911ae3234c440c1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744276"
---
# <a name="idiaenumsectioncontribsnext"></a>IDiaEnumSectionContribs::Next
Ruft eine angegebene Anzahl von Abschnitts Beiträgen in der enumerationssequenz ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT Next( 
   ULONG                celt,
   IDiaSectionContrib** rgelt,
   ULONG*               pceltFetched
);
```

#### <a name="parameters"></a>Parameter
 celt

in Die Anzahl der Abschnitts Beiträge im Enumerator, die abgerufen werden sollen.

 rgelt

vorgenommen Ein Array, das mit den [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) -Objekten gefüllt werden soll, die die gewünschten Abschnitts Beiträge darstellen.

 pceltFetched

vorgenommen Gibt die Anzahl von Abschnitts Beiträgen im Enumerator zurück, die abgerufen wurden.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn keine weiteren Abschnitts Beiträge vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)