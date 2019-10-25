---
title: 'Idiasymmetribol:: get_isAcceleratorGroupSharedLocal | Microsoft-Dokumentation'
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
ms.openlocfilehash: 1d6cf755121f851e652cce251ace2105e6773822
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740332"
---
# <a name="idiasymbolget_isacceleratorgroupsharedlocal"></a>IDiaSymbol::get_isAcceleratorGroupSharedLocal
Ruft ein Flag ab, das angibt, ob das Symbol einer freigegebenen lokalen Variablen einer Gruppe in Code entspricht C++ , der für einen amp-Accelerator kompiliert wurde.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_isAcceleratorGroupSharedLocal(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parameter
 `pFlag`

vorgenommen Ein Zeiger auf einen `BOOL` der angibt, ob das Symbol einer lokalen Gruppen Variablen in Code entspricht, der für einen C++ amp-Accelerator kompiliert wurde. Wenn `TRUE`, können die `get_baseDataSlot`-und `get_baseDataOffset`-Methoden verwendet werden, um die Speicherort Informationen für die Variable zu erhalten.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)
- [IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)