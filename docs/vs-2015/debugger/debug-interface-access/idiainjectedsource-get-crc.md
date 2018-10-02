---
title: 'Idiainjectedsource:: Get_crc | Microsoft-Dokumentation'
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
- IDiaInjectedSource::get_crc method
ms.assetid: 2ecdda93-950e-40d6-b79b-4ae3c55b6cfc
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c77d5ea682e714ed65cc1512b7e6eac477eacfce
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514314"
---
# <a name="idiainjectedsourcegetcrc"></a>IDiaInjectedSource::get_crc
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiainjectedsource:: Get_crc](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiainjectedsource-get-crc).  
  
Ruft ab eine zyklische redundanzprüfung (CRC), der aus die Bytes des Quellcodes berechnet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_crc (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt das CRC berechnet die Bytes des Quellcodes.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)



