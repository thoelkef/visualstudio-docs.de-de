---
title: 'Idiaenumdebug:: Skip | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreams::Skip method
ms.assetid: 6ec7753c-d7af-4879-b107-1b3442e0b025
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25fb1cb952c41d412df72ff7c0f0ad90e56ee6c0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744700"
---
# <a name="idiaenumdebugstreamsskip"></a>IDiaEnumDebugStreams::Skip
Überspringt eine angegebene Anzahl von debugstreams in einer enumerationssequenz.

## <a name="syntax"></a>Syntax

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parameter
 `celt`

in Die Anzahl der zu über springenden debugdatenströme in der enumerationssequenz.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` zurückgegeben, wenn keine weiteren zu über springenden Datensätze vorhanden sind.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)