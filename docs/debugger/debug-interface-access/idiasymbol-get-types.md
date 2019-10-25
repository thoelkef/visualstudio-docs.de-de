---
title: 'Idiasymmetribol:: get_types | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_types method
ms.assetid: 5f056e0c-e15b-4e00-8f78-aadc8574f7ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d23ea3c4d885b3f7575c998999814d0808d03bc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739060"
---
# <a name="idiasymbolget_types"></a>IDiaSymbol::get_types
Ruft ein Array von compilerspezifischen Typen für dieses Symbol ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_types ( 
   DWORD       cTypes,
   DWORD*      pcTypes,
   IDiaSymbol* types[]
);
```

#### <a name="parameters"></a>Parameter
 `cTypes`

in Größe des Puffers, der die Daten enthalten soll.

 `pcTypes`

vorgenommen Gibt die Anzahl der geschriebenen Typen zurück, oder, wenn der `types` Parameter `NULL` ist, die Gesamtzahl der verfügbaren Typen.

 `types[]`

vorgenommen Ein Array, das mit den [idiasymmetribol](../../debugger/debug-interface-access/idiasymbol.md) -Objekten ausgefüllt werden soll, die alle Typen für dieses Symbol darstellen.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)