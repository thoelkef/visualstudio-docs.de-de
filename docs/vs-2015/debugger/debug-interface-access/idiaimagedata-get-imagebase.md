---
title: 'Idiaimagedata:: Get_imagebase | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 278ea226c9531cdf16cc7660bb4eba67860430a4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523531"
---
# <a name="idiaimagedatagetimagebase"></a>IDiaImageData::get_imageBase
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiaimagedata:: Get_imagebase](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaimagedata-get-imagebase).  
  
Ruft die Speicheradresse, in dem das Abbild basieren soll.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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



