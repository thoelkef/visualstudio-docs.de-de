---
title: 'IDiaAddressMap:: get_addressMapEnabled | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b518cf3728279ea8db267d01867fa66ceae35b21
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745182"
---
# <a name="idiaaddressmapget_addressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
Gibt an, ob eine Adress Zuordnung für eine bestimmte Sitzung eingerichtet wurde.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_addressMapEnabled ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 pRetVal

vorgenommen Gibt `TRUE` zurück, wenn die Adress Zuordnung aktiviert ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Ausführbare Postprozessoren aktualisieren manchmal die ausführbare Datei. Dia enthält einen Mechanismus, mit dem die Übersetzung von Symbolen in das neue Layout unterstützt wird.

 Client Anwendungen können die Adress Zuordnung für eine bestimmte Sitzung festlegen, indem Sie die [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md) -Schnittstelle von der [IDiaSession](../../debugger/debug-interface-access/idiasession.md) -Schnittstelle abrufen und die [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) -Methode aufrufen, gefolgt von einem Aufruf des [ IDiaAddressMap::p ut_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md) -Methode. Die `get_addressMapEnabled`-Methode gibt die Ergebnisse zurück, die die `put_addressMapEnabled`-Methode aufrufen.

## <a name="see-also"></a>Siehe auch
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)