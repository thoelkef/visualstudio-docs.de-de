---
title: 'IDiaImageData:: get_relativeVirtualAddress | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_relativeVirtualAddress method
ms.assetid: e6d6deee-dc12-4b38-af15-f917b2d4368e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bfc7a808da6bb11907fc239f4b320e4dd93a2d19
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743429"
---
# <a name="idiaimagedataget_relativevirtualaddress"></a>IDiaImageData::get_relativeVirtualAddress
Ruft den Speicherort im virtuellen Arbeitsspeicher des Moduls relativ zur Anwendung ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_relativeVirtualAddress ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt den relativen virtuellen Speicher Offset des Moduls zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)