---
title: 'Idiapropertystorage:: Read-OL | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d776e37bab189e61d0264f4cbda24f89cb4501ce
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742937"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
Liest `BOOL` Werte in einem Eigenschaften Satz.

## <a name="syntax"></a>Syntax

```C++
HRESULT ReadBOOL ( 
   PROPID id,
   BOOL*  pValue
);
```

#### <a name="parameters"></a>Parameter
 `id`

in Der Bezeichner der zu lesenden Eigenschaft (`PROPID` ist in Wtypes. h als `ULONG` definiert).

 `pValue`

vorgenommen Gibt den Eigenschafts Wert zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben. Gibt `E_INVALIDARG` zurück, wenn die Eigenschaft nicht vom Typ `BOOL` ist.

## <a name="remarks"></a>Hinweise
 Um konsistente Ergebnisse zu erzielen, interpretieren Sie den `BOOL` Wert, sodass Werte ungleich NULL `TRUE` und NULL `FALSE` wird.

## <a name="see-also"></a>Siehe auch
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)