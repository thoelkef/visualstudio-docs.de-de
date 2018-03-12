---
title: 'Idiaimagedata:: Get_imagebase | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 5e3730e7bc543d0b7bdea18e162dfe83e1d803bb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idiaimagedatagetimagebase"></a>IDiaImageData::get_imageBase
Ruft die Speicheradresse, auf dem das Image basieren soll.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_imageBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt den vorgeschlagene Image-Basis-Wert.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Kann aufgrund von Image-Basis-Konflikten kann ein Abbild automatisch auf eine nicht verwendete Speicheradresse zurückgesetzt werden, wenn es geladen wird. Diese Methode gibt die Basis-Hinweis (vorgeschlagenen Speicheradresse), der im Modul zum Zeitpunkt der Kompilierung gespeichert wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)