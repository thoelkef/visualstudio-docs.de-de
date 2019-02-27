---
title: 'Idiaenumsourcefiles:: Next | Microsoft-Dokumentation'
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
ms.openlocfilehash: 29424c2b12884cae7f803a46e15f7183d9690d96
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56631782"
---
# <a name="idiaenumsourcefilesnext"></a>IDiaEnumSourceFiles::Next
Ruft eine angegebene Anzahl von Quelldateien in der Enumerationsfolge ab.

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

[in] Die Anzahl der Quelldateien im Enumerator abgerufen werden sollen.

 rgelt

[out] Ein Array, das mit gefüllt werden soll die [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) Objekte, die die gewünschten Quelldateien darstellen.

 pceltFetched

[out] Gibt die Anzahl der Quelldateien in der abgerufenen Enumerator zurück.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` , wenn keine weitere Quelldateien vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)