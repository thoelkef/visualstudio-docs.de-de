---
title: IDiaSymbol::get_isAcceleratorGroupSharedLocal | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 17a20542-5b45-478f-bb80-0d56031aadb5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ac6a7582c6fa59665390cfdb6b613fff6e36709
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62836835"
---
# <a name="idiasymbolgetisacceleratorgroupsharedlocal"></a>IDiaSymbol::get_isAcceleratorGroupSharedLocal
Ruft ein Flag, das angibt, ob das Symbol auf eine freigegebene lokale Gruppenvariable im Code für eine C++-AMP-Beschleuniger kompiliert entspricht.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_isAcceleratorGroupSharedLocal(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parameter
 `pFlag`

[out] Ein Zeiger auf eine `BOOL` , der angibt, ob eine freigegebene lokale Gruppenvariable in Code kompiliert wird, für das Symbol entspricht einem C++ Ampaccelerator. Wenn `TRUE`, `get_baseDataSlot` und `get_baseDataOffset` Methoden können verwendet werden, um die Speicherortinformationen für die Variable abzurufen.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)
- [IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)