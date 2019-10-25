---
title: IDiaAddressMap::p ut_imagealign | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b1a6bf037dc87d84fab21622571158fb0682f60
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745046"
---
# <a name="idiaaddressmapput_imagealign"></a>IDiaAddressMap::put_imageAlign
Legt die Bild Ausrichtung fest.

## <a name="syntax"></a>Syntax

```C++
HRESULT put_imageAlign ( 
   DWORD NewVal
);
```

#### <a name="parameters"></a>Parameter
 NewVal

in Der neue Bild Ausrichtungs Wert für die ausführbare Datei.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Bilder (geladene ausführbare Dateien) werden an den angegebenen Speichergrenzen ausgerichtet. Diese Ausrichtung kann von der aktuellen Systemarchitektur und den Optionen Kompilierungs-und Linkzeit beeinflusst werden. Die Bild Ausrichtung erfolgt immer über Byte-Begrenzungen. Die folgenden Bild Ausrichtungs Werte sind gültig: 1, 2, 4, 8, 16, 32 und 64 Byte-Begrenzungen.

 Die aktuelle Bild Ausrichtung kann mit einem Aufruf der [IDiaAddressMap:: get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) -Methode abgerufen werden.

> [!NOTE]
> Das Bild wird bereits von dem Zeitpunkt geladen, zu dem diese Methode aufgerufen werden kann. Die `put_imageAlign`-Methode wird normalerweise verwendet, wenn das Image verschoben oder geändert wurde und eine neue Ausrichtung erforderlich ist.

## <a name="see-also"></a>Siehe auch
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)