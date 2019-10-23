---
title: 'Idiasymmetribol:: get_isAcceleratorPointerTagLiveRange | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d195aec4-6d3c-42e0-88a5-3d463539f0b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd5a24a136bb9c04366449a91d825ddbecff2957
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740320"
---
# <a name="idiasymbolget_isacceleratorpointertagliverange"></a>IDiaSymbol::get_isAcceleratorPointerTagLiveRange
Ruft ein Flag ab, das angibt, ob das Symbol dem *Definitions Bereichs Symbol* für die Tagkomponente einer Zeiger Variablen in Code entspricht, der für C++ einen amp-Accelerator kompiliert wurde. Das Symbol für den Definitionsbereich ist der Speicherort einer Variablen für eine Adress Spanne.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_isAcceleratorPointerTagLiveRange(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parameter
 `pFlag`

vorgenommen Ein Zeiger auf einen `BOOL` der angibt, ob das Symbol dem Definitions Bereichs Symbol entspricht.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)