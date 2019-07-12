---
title: 'Idiasymbol:: Get_types | Microsoft-Dokumentation'
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
ms.openlocfilehash: 19642e6875e81220cb20109ce45e8dca40777a63
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/12/2019
ms.locfileid: "64786563"
---
# <a name="idiasymbolgettypes"></a>IDiaSymbol::get_types
Ruft ein Array von Compiler-spezifische Typen für dieses Symbol ab.

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

[in] Die Größe des Puffers zum Speichern der Daten.

 `pcTypes`

[out] Gibt die Anzahl der Typen, die geschrieben wird, oder, wenn Sie die `types` Parameter `NULL`, klicken Sie dann die Gesamtzahl der verfügbaren Typen.

 `types[]`

[out] Ein Array, das mit gefüllt werden soll die [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) Objekte, die alle Typen für dieses Symbol darstellen.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)