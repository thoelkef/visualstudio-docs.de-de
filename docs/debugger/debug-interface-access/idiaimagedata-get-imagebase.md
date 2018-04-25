---
title: 'Idiaimagedata:: Get_imagebase | Microsoft Docs'
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
ms.openlocfilehash: 9cd7cb16a4f6a6a629102eafbc212e4b2fff0f00
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
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