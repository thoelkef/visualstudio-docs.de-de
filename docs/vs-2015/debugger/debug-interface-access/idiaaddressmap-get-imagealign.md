---
title: 'Idiaaddressmap:: Get_imagealign | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaAddressMap::get_imageAlign method
ms.assetid: f1ba8071-669c-4cf7-9ac0-02f26d99f366
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33a4eb0ac41c90aafa694f080745ad6c54bd71f6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940059"
---
# <a name="idiaaddressmapgetimagealign"></a>IDiaAddressMap::get_imageAlign
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die Ausrichtung für das aktuelle ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_imageAlign (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt den Ausrichtungswert der Images aus der ausführbaren Datei zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Images sind auf bestimmten Arbeitsspeichergrenzen abhängig, wie das Bild geladen, und erstellt wurde, ausgerichtet. Die Ausrichtung ist in der Regel auf 1, 2, 4, 8, 16, 32 oder 64-Byte-Begrenzungen. Die Ausrichtung des kann festgelegt werden, durch einen Aufruf der [idiaaddressmap:: Put_imagealign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)



