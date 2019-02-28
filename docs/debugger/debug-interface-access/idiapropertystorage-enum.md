---
title: IDiaPropertyStorage::Enum | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::Enum
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e39693f63ea706ecdfa30a9ce0202444f51d4f57
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616104"
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
Ruft einen Enumerator für Eigenschaften in dieser Gruppe ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT Enum ( 
   IEnumSTATPROPSTG** ppenum
);
```

#### <a name="parameters"></a>Parameter
 `ppenum`

[out] Gibt eine `IEnumSTATPROPSTG` -Objekt (im Namespace Microsoft.VisualStudio.OLE.Interop), die eine Enumeration von Eigenschaften darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls einen Fehlercode zurück.

## <a name="see-also"></a>Siehe auch
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)