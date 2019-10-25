---
title: 'IDiaEnumLineNumbers:: Next | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Next method
ms.assetid: 363d5b40-1316-4ab8-836f-63637f619e0a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 07402ef7028ecfb7bb5b2c6e33ae06bc98ffe709
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744393"
---
# <a name="idiaenumlinenumbersnext"></a>IDiaEnumLineNumbers::Next
Ruft eine angegebene Anzahl von Zeilennummern in der enumerationssequenz ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT Next ( 
   ULONG            celt,
   IDiaLineNumber** rgelt,
   ULONG*           pceltFetched
);
```

#### <a name="parameters"></a>Parameter
 celt

in Die Anzahl der Zeilennummern im Enumerator, die abgerufen werden sollen.

 rgelt

vorgenommen Gibt ein Array von [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) -Objekten zurück, die die gewünschten Zeilennummern darstellen.

 pceltFetched

vorgenommen Gibt die Anzahl der Zeilennummern im abgerufenen Enumerator zurück.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn keine Zeilennummern mehr vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)