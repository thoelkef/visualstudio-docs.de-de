---
title: 'IDiaImageData:: get_imageBase | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4a8ed3f52a6e4709aa9553b0d7cc906069c9bcd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202571"
---
# <a name="idiaimagedataget_imagebase"></a>IDiaImageData::get_imageBase
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft den Speicherort ab, an dem das Image basieren soll.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_imageBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Gibt den vorgeschlagenen Bild Basiswert zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Aufgrund von Image Basis Konflikten wird ein Abbild möglicherweise automatisch auf einen nicht verwendeten Speicherort zurückgesetzt, wenn es geladen wird. Diese Methode gibt den Basis Hinweis (vorgeschlagene Speicheradresse) zurück, der zum Zeitpunkt der Kompilierung im Modul gespeichert wurde.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)
