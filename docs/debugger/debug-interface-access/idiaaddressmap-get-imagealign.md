---
title: 'Idiaaddressmap:: Get_imagealign | Microsoft-Dokumentation'
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
ms.openlocfilehash: 3fb51f810d5c97ecf1cb0a6ea0b41dc7481252ba
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56605561"
---
# <a name="idiaaddressmapgetimagealign"></a>IDiaAddressMap::get_imageAlign
Ruft die Ausrichtung für das aktuelle ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_imageAlign ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt den Ausrichtungswert der Images aus der ausführbaren Datei zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Anmerkungen
 Images sind auf bestimmten Arbeitsspeichergrenzen abhängig, wie das Bild geladen, und erstellt wurde, ausgerichtet. Die Ausrichtung ist in der Regel auf 1, 2, 4, 8, 16, 32 oder 64-Byte-Begrenzungen. Die Ausrichtung des kann festgelegt werden, durch einen Aufruf der [idiaaddressmap:: Put_imagealign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md) Methode.

## <a name="see-also"></a>Siehe auch
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)