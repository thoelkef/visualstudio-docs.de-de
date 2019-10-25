---
title: 'Idiaenumsectioncontrisb:: Skip | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Skip method
ms.assetid: 7471a178-5134-41b2-80a6-51ff96abe916
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb371d841c10b64895400f66bf73159f27d68ec1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744265"
---
# <a name="idiaenumsectioncontribsskip"></a>IDiaEnumSectionContribs::Skip
Überspringt eine angegebene Anzahl von Abschnitts Beiträgen in einer enumerationssequenz.

## <a name="syntax"></a>Syntax

```C++
HRESULT Skip( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parameter
 `celt`

in Die Anzahl der Abschnitts Beiträge in der zu über springenden enumerationssequenz.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` zurückgegeben, wenn keine weiteren Abschnitts Beiträge zum Überspringen vorhanden sind.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)