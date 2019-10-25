---
title: 'Idiapropertystorage:: Read PropertyNames | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f554485ae56a9d5f190c749879545165d299531c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742873"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
Ruft entsprechende Zeichen folgen Namen für angegebene Eigenschaften Bezeichner ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT ReadPropertyNames (
   ULONG         cpropid,
   PROPID const* rgpropid,
   BSTR*         rglpwstrName
);
```

#### <a name="parameters"></a>Parameter
 `cpropid`

in Anzahl der Eigenschaften-IDs in `rgpropid`.

 `rgpropid`

in Ein Array von Eigenschaften-IDs, für die die Namen abzurufen sind (`PROPID` ist in Wtypes. h als `ULONG` definiert).

 `rglpwstrName`

[in, out] Array von Eigenschaften Namen für die angegebenen Eigenschaften-IDs. Das Array muss vorab zugeordnet werden, um die angeforderte Anzahl von Eigenschaftsnamen zu speichern, und muss mindestens `cpropid``BSTR` Zeichen folgen enthalten können.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Die zurückgegebenen Eigenschaftsnamen müssen freigegeben werden (durch Aufrufen der `SysFreeString`-Funktion), wenn Sie nicht mehr benötigt werden.

## <a name="see-also"></a>Siehe auch
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)