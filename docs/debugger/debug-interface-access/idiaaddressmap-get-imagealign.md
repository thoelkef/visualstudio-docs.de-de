---
title: 'IDiaAddressMap:: get_imageAlign | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_imageAlign method
ms.assetid: f1ba8071-669c-4cf7-9ac0-02f26d99f366
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa5394580a9b0db4600a7f1e67aa8bd7f7703542
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745087"
---
# <a name="idiaaddressmapget_imagealign"></a>IDiaAddressMap::get_imageAlign
Ruft die aktuelle Bild Ausrichtung ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_imageAlign ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt den Bild Ausrichtungs Wert aus der ausführbaren Datei zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Abhängig von der Art und Weise, wie das Image geladen und erstellt wurde, werden Bilder an bestimmten Speichergrenzen ausgerichtet. Die Ausrichtung erfolgt in der Regel auf 1, 2, 4, 8, 16, 32 oder 64 Byte-Begrenzungen. Die Bild Ausrichtung kann mit einem Aufruf der [IDiaAddressMap::p ut_imagealign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md) -Methode festgelegt werden.

## <a name="see-also"></a>Siehe auch
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)