---
title: 'IDiaSegment:: get_addressSection | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment::get_addressSection method
ms.assetid: 360b61b1-69b1-4a8b-ba37-97a1d835ac53
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9114a1d97dc9c25aa9c2bfe84dc96b63051b92d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742436"
---
# <a name="idiasegmentget_addresssection"></a>IDiaSegment::get_addressSection
Ruft die Abschnitts Nummer ab, die diesem Segment zugeordnet ist.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_addressSection ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt die Abschnitts Nummer zurück, die diesem Segment zugeordnet ist.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)