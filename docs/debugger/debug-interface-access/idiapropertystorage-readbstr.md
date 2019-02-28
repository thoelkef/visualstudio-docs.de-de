---
title: IDiaPropertyStorage::ReadBSTR | Microsoft-Dokumentation
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
ms.openlocfilehash: f0bff81499fe8ea66ce5d4f50616adfec44d3002
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56610956"
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
Liest `BSTR` Werte in einem Eigenschaftensatz.

## <a name="syntax"></a>Syntax

```C++
HRESULT ReadBSTR ( 
   PROPID id,
   BSTR*  pValue
);
```

#### <a name="parameters"></a>Parameter
 `id`

[in] Bezeichner für die Eigenschaft gelesen werden (`PROPID` ist in WTypes.h als definiert eine `ULONG`).

 `pValue`

[out] Gibt den Wert der Eigenschaft zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls einen Fehlercode zurück. Gibt `E_INVALIDARG` ist die Eigenschaft nicht vom Typ `BSTR`.

## <a name="remarks"></a>Anmerkungen
 Ein `BSTR` wird von Windows als 0 (null) endende Breite Zeichenfolge definiert.

## <a name="see-also"></a>Siehe auch
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)