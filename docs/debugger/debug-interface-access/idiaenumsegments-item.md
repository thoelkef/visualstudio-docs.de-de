---
title: 'IDiaEnumSegments:: Item | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Item method
ms.assetid: ee44dd55-39a0-4b7b-97ff-2e1226eeb2bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 101821e3c00d3aeac9b131ee5a11ab9a01e090a9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744181"
---
# <a name="idiaenumsegmentsitem"></a>IDiaEnumSegments::Item
Ruft ein Segment mithilfe eines Indexes ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT Item ( 
   DWORD         index,
   IDiaSegment** segment
);
```

#### <a name="parameters"></a>Parameter
 Index

in Der Index des [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) -Objekts, das abgerufen werden soll. Der Index liegt im Bereich von 0 bis `count`-1, wobei `count` von der [IDiaEnumSegments:: get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md) -Methode zurückgegeben wird.

 segment

vorgenommen Gibt ein [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) -Objekt zurück, das das gewünschte Segment darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)