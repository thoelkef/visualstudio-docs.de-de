---
title: 'IDiaImageData:: get_imageBase | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7887fea30b04f4ebb6605169c58551122eccf73d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743439"
---
# <a name="idiaimagedataget_imagebase"></a>IDiaImageData::get_imageBase
Ruft den Speicherort ab, an dem das Image basieren soll.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_imageBase ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

vorgenommen Gibt den vorgeschlagenen Bild Basiswert zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Aufgrund von Image Basis Konflikten wird ein Abbild möglicherweise automatisch auf einen nicht verwendeten Speicherort zurückgesetzt, wenn es geladen wird. Diese Methode gibt den Basis Hinweis (vorgeschlagene Speicheradresse) zurück, der zum Zeitpunkt der Kompilierung im Modul gespeichert wurde.

## <a name="see-also"></a>Siehe auch
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)