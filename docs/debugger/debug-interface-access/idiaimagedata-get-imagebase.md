---
title: 'Idiaimagedata:: Get_imagebase | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e0037ef4bbbfc499d23e517e0fb3522b8f042c7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822976"
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