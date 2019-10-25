---
title: 'Idiapropertystorage:: Read BSTR | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBSTR
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef0b5bac11a1bf3da7e8081f7ae24b6a7a6f1a71
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742915"
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
Liest `BSTR` Werte in einem Eigenschaften Satz.

## <a name="syntax"></a>Syntax

```C++
HRESULT ReadBSTR ( 
   PROPID id,
   BSTR*  pValue
);
```

#### <a name="parameters"></a>Parameter
 `id`

in Der Bezeichner der zu lesenden Eigenschaft (`PROPID` ist in Wtypes. h als `ULONG` definiert).

 `pValue`

vorgenommen Gibt den Eigenschafts Wert zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben. Gibt `E_INVALIDARG` zurück, wenn die Eigenschaft nicht vom Typ `BSTR` ist.

## <a name="remarks"></a>Hinweise
 Ein `BSTR` wird von Windows als eine NULL terminierte Zeichenfolge mit breit Zeichen definiert.

## <a name="see-also"></a>Siehe auch
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)