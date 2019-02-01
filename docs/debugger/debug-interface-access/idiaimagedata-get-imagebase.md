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
ms.openlocfilehash: 238eb138f7e7452e942047d776411d973a689c2a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54931439"
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
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)