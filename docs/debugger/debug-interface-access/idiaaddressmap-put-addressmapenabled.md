---
title: IDiaAddressMap::p ut_addressmapenabled | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5fe5589b667054ee75e3b01743553a2d60bef92
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745067"
---
# <a name="idiaaddressmapput_addressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
Gibt an, ob die Adress Zuordnung zum Übersetzen von Symbol Adressen verwendet werden soll.

## <a name="syntax"></a>Syntax

```C++
HRESULT put_addressMapEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>Parameter
 NewVal

in Legen Sie auf `TRUE` fest, um die Übersetzung von Symbolen zu aktivieren, oder `FALSE`, um zu deaktivieren.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Ausführbare Postprozessoren aktualisieren manchmal die ausführbare Datei. Dia enthält einen Mechanismus, mit dem die Übersetzung von Symbolen in das neue Layout unterstützt wird.

 Beim Laden einer PDB-Datei wird die in der Datei gespeicherte Adress Zuordnung aktiviert. Es gibt jedoch Zeiten, in denen eine Client Anwendung möglicherweise eine eigene Adress Zuordnung bereitstellen muss, indem Sie die [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) -Methode aufrufen. Wenn die `set_addressMap`-Methode erfolgreich ist, muss die Client Anwendung die `put_addressMapEnabled`-Methode mit dem `NewVal`-Parameter `TRUE` aufrufen, um die Verwendung dieser Adress Zuordnung zu aktivieren.

 Der aktuelle Zustand der aktivierten Adress Zuordnung kann mit einem Aufruf der [IDiaAddressMap:: get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md) -Methode abgerufen werden.

## <a name="see-also"></a>Siehe auch
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)