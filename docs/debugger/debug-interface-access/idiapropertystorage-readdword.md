---
title: 'Idiapropertystorage:: Read-Word | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadDWORD
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1764ec83a69dcc5daff267767594473bf690b341
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742907"
---
# <a name="idiapropertystoragereaddword"></a>IDiaPropertyStorage::ReadDWORD
Liest `DWORD` Werte in einem Eigenschaften Satz.

## <a name="syntax"></a>Syntax

```C++
HRESULT ReadDWORD ( 
   PROPID id,
   DWORD* pValue
);
```

#### <a name="parameters"></a>Parameter
 `id`

in Der Bezeichner der zu lesenden Eigenschaft (`PROPID` ist in Wtypes. h als `ULONG` definiert).

 `pValue`

vorgenommen Gibt den Eigenschafts Wert zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben. Gibt `E_INVALIDARG` zurück, wenn die Eigenschaft nicht vom Typ `DWORD` ist.

## <a name="remarks"></a>Hinweise
 Ein `DWORD` wird von Windows als eine 32-Bit-Ganzzahl ohne Vorzeichen definiert.

## <a name="see-also"></a>Siehe auch
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)