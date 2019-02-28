---
title: 'Idiaenumlinenumbers:: Clone | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Clone method
ms.assetid: fcd2479a-8ff7-4aba-a737-06123c280d54
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd9dd34bd75199f2af3e14a96a12af663b2ba1f9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616429"
---
# <a name="idiaenumlinenumbersclone"></a>IDiaEnumLineNumbers::Clone
Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.

## <a name="syntax"></a>Syntax

```C++
HRESULT Clone ( 
   IDiaEnumLineNumbers** ppenum
);
```

#### <a name="parameters"></a>Parameter
 `ppenum`

[out] Gibt eine [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) Objekt, das ein Duplikat des Enumerators enthält. Die Zeile, die Zahlen sind dupliziert, nur den Enumerator...

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)