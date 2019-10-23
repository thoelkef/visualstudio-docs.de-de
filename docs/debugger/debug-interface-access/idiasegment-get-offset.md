---
title: 'IDiaSegment:: get_Offset | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_offset method
ms.assetid: 97415ac6-b072-4e3c-9dd3-73087ae605fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e0d6084f75b3ba903a89c3dfc4249b73887df39
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742405"
---
# <a name="idiasegmentget_offset"></a>IDiaSegment::get_offset
Ruft den Offset in Segmenten ab, in dem der Abschnitt beginnt.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_offset ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt den Offset in Segmenten zurück, in dem der Abschnitt beginnt.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)