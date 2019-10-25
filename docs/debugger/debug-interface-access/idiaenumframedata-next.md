---
title: 'IDiaEnumFrameData:: Next | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Next method
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fe478e503ed6e16ee570f309f91434c658ebd27
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744598"
---
# <a name="idiaenumframedatanext"></a>IDiaEnumFrameData::Next
Ruft eine angegebene Anzahl von Frame-Datenelementen in der enumerationssequenz ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT Next ( 
   ULONG           celt,
   IDiaFrameData** rgelt,
   ULONG*          pceltFetched
);
```

#### <a name="parameters"></a>Parameter
 celt

in Die Anzahl der Frame Datenelemente im Enumerator, die abgerufen werden sollen.

 rgelt

vorgenommen Ein Array von [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) -Objekten, die mit den angeforderten Frame Datenelementen aufgefüllt werden sollen.

 pceltFetched

vorgenommen Gibt die Anzahl der Frame Datenelemente im abgerufenen Enumerator zurück.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn keine weiteren Datensätze vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)