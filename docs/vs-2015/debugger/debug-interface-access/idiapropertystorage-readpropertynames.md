---
title: IDiaPropertyStorage::ReadPropertyNames | Microsoft-Dokumentation
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
ms.openlocfilehash: f3f6d3ac520a396b5207767a3fec0913c801c287
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62537354"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
Ruft entsprechende Zeichenfolgennamen für angegebenen Eigenschaftenbezeichner.

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

[in] Anzahl der Eigenschafts-Ids in `rgpropid`.

 `rgpropid`

[in] Array von Eigenschaften-Ids für die Namen die abzurufenden (`PROPID` ist in WTypes.h als definiert eine `ULONG`).

 `rglpwstrName`

[in, out] Ein Array von Eigenschaftennamen für die angegebene Eigenschaft-Ids. Das Array müssen nicht vorab zugewiesen ist, um die angeforderte Anzahl der Namen von aufzunehmen und muss in der Lage, enthalten mindestens `cpropid``BSTR` Zeichenfolgen.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls einen Fehlercode zurück.

## <a name="remarks"></a>Hinweise
 Die zurückgegebenen Eigenschaftennamen müssen freigegeben werden (durch Aufrufen der `SysFreeString` Funktion) Wenn sie nicht mehr benötigt.

## <a name="see-also"></a>Siehe auch
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)