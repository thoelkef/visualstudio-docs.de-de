---
title: 'IDiaEnumSegments:: Next | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Next method
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34062b654cbaccec053c5ac50bfb041d37a0f4e6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744192"
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
Ruft eine angegebene Anzahl von Segmenten in der enumerationssequenz ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT Next ( 
   ULONG         celt,
   IDiaSegment** rgelt,
   ULONG*        pceltFetched
);
```

#### <a name="parameters"></a>Parameter
 celt

in Die Anzahl der Segmente im Enumerator, die abgerufen werden sollen.

 rgelt

vorgenommen Ein Array, das mit den gewünschten [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) -Objekten ausgefüllt werden soll, die die Segmente darstellen.

 pceltFetched

vorgenommen Gibt die Anzahl der Segmente im abgerufenen Enumerator zurück.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn keine weiteren Segmente vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)