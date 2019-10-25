---
title: 'IDiaEnumSourceFiles:: Next | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Next method
ms.assetid: 83bf6317-ff39-4c5c-8987-cba34e7a6983
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 526c857acbe1283e16312355c181c56c67e19883
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744079"
---
# <a name="idiaenumsourcefilesnext"></a>IDiaEnumSourceFiles::Next
Ruft eine angegebene Anzahl von Quelldateien in der enumerationssequenz ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT Next ( 
   ULONG            celt,
   IDiaSourceFile** rgelt,
   ULONG*           pceltFetched
);
```

#### <a name="parameters"></a>Parameter
 celt

in Die Anzahl der Quelldateien im Enumerator, die abgerufen werden sollen.

 rgelt

vorgenommen Ein Array, das mit den [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) -Objekten ausgefüllt werden soll, die die gewünschten Quelldateien darstellen.

 pceltFetched

vorgenommen Gibt die Anzahl der Quelldateien im abgerufenen Enumerator zurück.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn keine weiteren Quelldateien vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)