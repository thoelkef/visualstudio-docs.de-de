---
title: 'Idiapropertystorage:: Read Long | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadLONG
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af9d65c571c5e0a281b968d922c9b5170bd1c561
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742892"
---
# <a name="idiapropertystoragereadlong"></a>IDiaPropertyStorage::ReadLONG
Liest `LONG` Werte in einem Eigenschaften Satz.

## <a name="syntax"></a>Syntax

```C++
HRESULT ReadDLONG ( 
   PROPID id,
   LONG*  pValue
);
```

#### <a name="parameters"></a>Parameter
 `id`

in Der Bezeichner der zu lesenden Eigenschaft (`PROPID` ist in Wtypes. h als `ULONG` definiert).

 `pValue`

vorgenommen Gibt den Eigenschafts Wert zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben. Gibt `E_INVALIDARG` zurück, wenn die Eigenschaft nicht vom Typ `LONG` ist.

## <a name="remarks"></a>Hinweise
 Ein `LONG` wird von Windows als eine 32-Bit-Ganzzahl mit Vorzeichen definiert.

## <a name="see-also"></a>Siehe auch
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)