---
title: 'Idiainjectedsource:: Get_objectfilename | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_objectFilename method
ms.assetid: 7c42847a-f0df-443a-a9fe-c495c1271ea8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4bf9b325354bd95678969e5d1db4c13370d6d8b3
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56611047"
---
# <a name="idiainjectedsourcegetobjectfilename"></a>IDiaInjectedSource::get_objectFilename
Ruft ab, der Name der Objektdatei, unter dem die Quelle kompiliert wurde.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_objectFilename ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt zurück, der Name der Objektdatei, unter dem die Quelle kompiliert wurde.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)