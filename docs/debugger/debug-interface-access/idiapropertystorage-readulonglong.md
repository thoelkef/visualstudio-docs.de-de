---
title: 'Idiapropertystorage:: locker | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadULONGLONG
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dde2f111e468b8ccf6c1d91440f06d3e7048a0f6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742849"
---
# <a name="idiapropertystoragereadulonglong"></a>IDiaPropertyStorage::ReadULONGLONG
Liest `ULONGLONG` Werte in einem Eigenschaften Satz.

## <a name="syntax"></a>Syntax

```C++
HRESULT ReadULONGLONG ( 
   PROPID     id,
   ULONGLONG* pValue
);
```

#### <a name="parameters"></a>Parameter
 `id`

in Der Bezeichner der zu lesenden Eigenschaft (`PROPID` ist in Wtypes. h als `ULONG` definiert).

 `pValue`

vorgenommen Gibt den Eigenschafts Wert zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben. Gibt `E_INVALIDARG` zurück, wenn die Eigenschaft nicht vom Typ `ULONGLONG` ist.

## <a name="remarks"></a>Hinweise
 Ein `ULONGLONG` wird von Windows als eine 64-Bit-Ganzzahl ohne Vorzeichen definiert.

## <a name="see-also"></a>Siehe auch
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)