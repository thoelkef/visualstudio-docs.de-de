---
title: 'Idiaenumdebugstreams:: Skip | Microsoft-Dokumentation'
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
ms.openlocfilehash: 90bf6b41400143d7a6703db24c031cb3ed31de2c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56609695"
---
# <a name="idiaenumdebugstreamsskip"></a>IDiaEnumDebugStreams::Skip
Überspringt eine angegebene Anzahl von Debug-Datenströme in einer Enumerationsfolge.

## <a name="syntax"></a>Syntax

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parameter
 `celt`

[in] Die Anzahl der Debug-Streams in der Enumerationsfolge übersprungen werden soll.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` es sind keine weitere Datensätze zu überspringen.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)