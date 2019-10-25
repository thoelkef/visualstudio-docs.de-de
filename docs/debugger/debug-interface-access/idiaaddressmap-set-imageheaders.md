---
title: 'IDiaAddressMap:: set_imageHeaders | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef17e1073c67ede75d075b18773129c287349c0d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745015"
---
# <a name="idiaaddressmapset_imageheaders"></a>IDiaAddressMap::set_imageHeaders
Legt Bild Header fest, um die relative virtuelle Adressübersetzung zu aktivieren.

## <a name="syntax"></a>Syntax

```C++
HRESULT set_imageHeaders ( 
   DWORD cbData,
   BYTE  data[],
   BOOL  originalHeaders
);
```

#### <a name="parameters"></a>Parameter
 cbData

in Anzahl von Bytes von Header Daten. Muss `n*sizeof(IMAGE_SECTION_HEADER)` sein, wobei `n` die Anzahl der Abschnitts Header in der ausführbaren Datei ist.

 data[]

in Ein Array von `IMAGE_SECTION_HEADER` Strukturen, die als Bild Header verwendet werden sollen.

 originalHeaders

in Legen Sie fest, `FALSE` wenn die Bild Header aus dem neuen Bild stammen, `TRUE`, wenn Sie das ursprüngliche Bild vor einem Upgrade widerspiegeln. In der Regel wird dies auf `TRUE` nur in Kombination mit Aufrufen der [IDiaAddressMap:: set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) -Methode festgelegt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Die `IMAGE_SECTION_HEADER` Struktur wird in "Winnt. h" deklariert und stellt das Bild Abschnitts Header Format der ausführbaren Datei dar.

 Relative virtuelle Adress Berechnungen richten sich nach den `IMAGE_SECTION_HEADER` Werten. In der Regel ruft der Dia diese aus der Programm Datenbankdatei (. pdb) ab. Wenn diese Werte fehlen, kann die Dia keine relativen virtuellen Adressen berechnen, und die [IDiaAddressMap:: get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) -Methode gibt `FALSE` zurück. Der Client muss dann die [IDiaAddressMap::p ut_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) -Methode aufzurufen, um die relativen virtuellen Adress Berechnungen zu aktivieren, nachdem die fehlenden Bild Header aus dem Image selbst bereitgestellt wurden.

## <a name="see-also"></a>Siehe auch
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)
- [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)
- [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)