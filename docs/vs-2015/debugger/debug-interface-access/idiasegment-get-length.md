---
title: 'Idiasegment:: Get_length | Microsoft-Dokumentation'
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
- IDiaSegment::get_length method
ms.assetid: 5d92e394-649b-49f2-bce7-12dd9d666d85
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62babd2a6db28ff524fba017111e89757b52f9a7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521695"
---
# <a name="idiasegmentgetlength"></a>IDiaSegment::get_length
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiasegment:: Get_length](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasegment-get-length).  
  
Ruft die Anzahl der Bytes im Segment ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_ length (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt die Anzahl der Bytes im Segment.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)



