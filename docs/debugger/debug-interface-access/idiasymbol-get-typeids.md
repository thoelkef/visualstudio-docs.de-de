---
title: 'Idiasymmetribol:: get_typeIds | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4db7c1d7e3ed19268d94b28a7f0500788f7d21f5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739073"
---
# <a name="idiasymbolget_typeids"></a>IDiaSymbol::get_typeIds
Ruft ein Array von compilerspezifischen typbezeichnerwerten für dieses Symbol ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_typeIds ( 
   DWORD  cTypeIds,
   DWORD* pcTypeIds,
   DWORD  typeIds[]
);
```

#### <a name="parameters"></a>Parameter
 `cTypeIds`

in Größe des Puffers, der die Daten enthalten soll.

 `pcTypeIds`

vorgenommen Gibt die Anzahl der geschriebenen `typeIds` oder, wenn `typeIds` `NULL` ist, die Gesamtzahl der verfügbaren Typbezeichner zurück.

 `typeIds[]`

vorgenommen Ein Array, das mit den typbezeichgern ausgefüllt werden soll.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)