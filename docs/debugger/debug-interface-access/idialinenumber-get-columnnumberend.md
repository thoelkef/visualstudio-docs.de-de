---
title: 'Idialinenumber:: Get_columnnumberend | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumberEnd method
ms.assetid: 02fa56c1-87b6-405a-adee-3bb6bc62de2d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 567df436093b53432e44e21fb96f0d092b71c81d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839848"
---
# <a name="idialinenumbergetcolumnnumberend"></a>IDiaLineNumber::get_columnNumberEnd
Ruft die Nummer der Spalte 1-basierte Quelle, in den Ausdruck oder Anweisung endet.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_columnNumberEnd ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt die Nummer der Spalte zurück, beendet den Ausdruck oder Anweisung ist. Wenn der Wert 0 (null) ist, ist die End-Spalteninformationen nicht vorhanden.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Der Spaltenwert, der von dieser Methode zurückgegebene ist ein Byteoffset in der Zeile, der die Position hinter dem letzten Zeichen der Anweisung in der Zeile.

## <a name="see-also"></a>Siehe auch
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)