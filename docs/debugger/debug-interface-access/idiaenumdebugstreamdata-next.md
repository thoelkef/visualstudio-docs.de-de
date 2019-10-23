---
title: 'Idiaenumdebug bugstreamdata:: Next | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Next method
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: acdab0a565613194c67aa85484316a235c91dbf6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744794"
---
# <a name="idiaenumdebugstreamdatanext"></a>IDiaEnumDebugStreamData::Next
Ruft eine angegebene Anzahl von Datensätzen in der enumerationssequenz ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT Next ( 
   ULONG  celt,
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[],
   ULONG* pceltFetched
);
```

#### <a name="parameters"></a>Parameter
 celt

in Die Anzahl der Datensätze, die abgerufen werden sollen.

 cbData

in Größe des Daten Puffers in Bytes.

 pcbData

vorgenommen Gibt die Anzahl der zurückgegebenen Bytes zurück. Wenn `data` NULL ist, enthält `pcbData` die Gesamtanzahl der Daten bytes, die für alle angeforderten Datensätze verfügbar sind.

 data[]

vorgenommen Ein Puffer, der mit den Daten des Debug-Datensatzes aufgefüllt werden soll.

 pceltFetched

[in, out] Gibt die Anzahl der Datensätze in `data` zurück.

## <a name="return-value"></a>Rückgabewert
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` zurück, wenn keine weiteren Datensätze vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)