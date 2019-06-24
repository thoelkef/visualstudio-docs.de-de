---
title: 'Idiaimagedata:: Get_imagebase | Microsoft-Dokumentation'
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
ms.openlocfilehash: de8c333391530cd86c6fc66a8e6c36ce8cfecd5f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829061"
---
# <a name="idiaimagedatagetimagebase"></a>IDiaImageData::get_imageBase
Ruft die Speicheradresse, in dem das Abbild basieren soll.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_imageBase ( 
   ULONGLONG* pRetVal
);
```

#### <a name="parameters"></a>Parameter
 `pRetVal`

[out] Gibt den Basiswert der vorgeschlagenen Image zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Aufgrund von Image-Basis-Konflikten kann ein Bild automatisch auf einen nicht verwendeten Speicherbereich ein REBASE ausgeführt werden, wenn es geladen wird. Diese Methode gibt den Basis-Hinweis (empfohlene Speicherort), der zum Zeitpunkt der Kompilierung im Modul gespeichert wurden.

## <a name="see-also"></a>Siehe auch
- [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)