---
title: 'Idiasourcefile:: Get_uniqueid | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_uniqueId method
ms.assetid: e0b8dbc0-6061-4f31-bead-2cd72be44e41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4a204e04c1c99dcbe8c6ba6d5e3457ca875dde4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832252"
---
# <a name="idiasourcefilegetuniqueid"></a>IDiaSourceFile::get_uniqueId
Ruft einen Wert des Schlüssels einfachen ganzen Zahl, der eindeutig für dieses Image ist.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_uniqueId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt einen Wert des Schlüssels einfachen ganzen Zahl, der eindeutig für dieses Image ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Vergleichen von Schlüsseln, anstatt Zeichenfolgen Line Number Verarbeitung beschleunigt werden können.

## <a name="see-also"></a>Siehe auch
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)