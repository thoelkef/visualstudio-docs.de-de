---
title: 'Idiaenumdebug bugstreamdata:: Item | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Item method
ms.assetid: 761e61a5-44a6-4d5d-a98e-c2e9b89d2343
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e221516198d186dd08c353123ce4236f0be1383c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744818"
---
# <a name="idiaenumdebugstreamdataitem"></a>IDiaEnumDebugStreamData::Item
Ruft den angegebenen Datensatz ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT Item ( 
   DWORD  index,
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Parameter
 Index

in Der Index des abzurufenden Datensatzes. Der Index liegt zwischen 0 und `count`-1, wobei `count` von [idiaenumdebug:: get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)zurückgegeben wird.

 cbData

in Größe des Daten Puffers in Bytes.

 pcbData

vorgenommen Gibt die Anzahl der zurückgegebenen Bytes zurück. Wenn `data` `NULL` ist, enthält `pcbData` die Gesamtanzahl der Daten bytes, die im angegebenen Datensatz verfügbar sind.

 data[]

vorgenommen Ein Puffer, der mit den Daten des Debug-Datensatzes aufgefüllt wird.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben. Gibt `E_INVALIDARG` für ungültige Parameter und zurück, wenn der `index` Parameter außerhalb des gültigen Bereichs liegt.

## <a name="see-also"></a>Siehe auch
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
- [IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)
- [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)
- [IDiaEnumDebugStreamData::get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)
- [IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)