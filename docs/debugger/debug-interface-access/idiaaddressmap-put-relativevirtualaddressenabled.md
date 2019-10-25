---
title: IDiaAddressMap::put_relativeVirtualAddressEnabled | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_relativeVirtualAddressEnabled method
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d733a51bd599b85dcc6d1121b8d21e1a687a351
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745042"
---
# <a name="idiaaddressmapput_relativevirtualaddressenabled"></a>IDiaAddressMap::put_relativeVirtualAddressEnabled
Ermöglicht dem Client, die Berechnung und Verwendung von relativen virtuellen Adressen (RVA) zu aktivieren oder zu deaktivieren.

## <a name="syntax"></a>Syntax

```C++
HRESULT put_relativeVirtualAddressEnabled ( 
   BOOL NewVal
);
```

#### <a name="parameters"></a>Parameter
 NewVal

in Legen Sie fest, um `TRUE` zu aktivieren oder zu deaktivieren `FALSE`.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Adressen für Debug-Objekte, die von Dia-Schnittstellen und relativ zur Image Basis der ausführbaren Datei beschrieben werden, können als relative virtuelle Adressen abgerufen werden.

 Die Verwendung von RVAs wird aktiviert, wenn Segmente anfänglich aus einer PDB-Datei geladen werden. Um den aktuellen Status der Verwendung von RVAs abzurufen, müssen Sie die [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) -Methode abrufen.

 Die `put_relativeVirtualAddress`-Methode muss aufgerufen werden, um RVAs zu aktivieren, nachdem ein erfolgreicher Aufruf der [IDiaAddressMap:: set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) -Methode neue Bild Header erstellt hat.

## <a name="see-also"></a>Siehe auch
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)