---
title: 'Idiaenuminjetedsources:: Item | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Item method
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 91be2f4f437cfeed30b0741d10bf719ba0ed2b71
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744500"
---
# <a name="idiaenuminjectedsourcesitem"></a>IDiaEnumInjectedSources::Item
Ruft eine eingefügte Quelle mithilfe eines Indexes ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT Item ( 
   DWORD                index,
   IDiaInjectedSource** injectedSource
);
```

#### <a name="parameters"></a>Parameter
 Index

in Der Index des abzurufenden [idiainjetedsource](../../debugger/debug-interface-access/idiainjectedsource.md) -Objekts. Der Index liegt zwischen 0 und `count`-1, wobei `count` von der [idiaenuminjetedsources:: get_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md) -Methode zurückgegeben wird.

 injectedSource

vorgenommen Gibt ein [idiainjetedsource](../../debugger/debug-interface-access/idiainjectedsource.md) -Objekt zurück, das die eingefügte Quelle darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)