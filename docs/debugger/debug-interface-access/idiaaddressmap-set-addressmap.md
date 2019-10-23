---
title: 'IDiaAddressMap:: set_addressMap | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8414788af44d78943088b78b2d3e42a5a8d8c50b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745030"
---
# <a name="idiaaddressmapset_addressmap"></a>IDiaAddressMap::set_addressMap
Stellt eine Adress Zuordnung zur Unterstützung von Bild layoutübersetzungen bereit.

## <a name="syntax"></a>Syntax

```C++
HRESULT set_addressMap ( 
   DWORD                     cbData,
   struct DiaAddressMapEntry data[],
   BOOL                      imagetoSymbols
);
```

#### <a name="parameters"></a>Parameter
 `cbData`

in Die Anzahl der Elemente im `data`-Parameter.

 `data[]`

in Ein Array von [DiaAddressMapEntry-Struktur](../../debugger/debug-interface-access/diaaddressmapentry.md) Strukturen, die die Übersetzungs Zuordnung definieren.

 `imagetoSymbols`

[in] `TRUE`, wenn der `data` Parameter eine Zuordnung vom neuen Bild Layout zum ursprünglichen Layout definiert (wie von den Debugsymbolen beschrieben). `FALSE`, wenn `data` eine Zuordnung zum neuen Bild Layout ist, das aus dem ursprünglichen Layout entnommen wurde.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 In der Regel ruft der Dia Adress Übersetzungs Zuordnungen aus der Programm Datenbankdatei (. pdb) ab. Wenn diese Werte fehlen, wird die [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) -Methode zweimal aufgerufen, wenn der `imagetoSymbols`-Parameter auf `TRUE` und der `imagetoSymbols`-Parameter auf `FALSE` festgelegt ist. Adress Zuordnungs Übersetzungen können nicht mithilfe der [IDiaAddressMap::p ut_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) -Methode aktiviert werden, es sei denn, beide Übersetzungs Karten werden bereitgestellt.

## <a name="see-also"></a>Siehe auch
- [DiaAddressMapEntry Structure](../../debugger/debug-interface-access/diaaddressmapentry.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)