---
title: 'Idiasegment:: Get_read | Microsoft-Dokumentation'
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
- IDiaSegment::get_read method
ms.assetid: aafbc86d-352c-4e1a-911a-1472d2d59212
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 800f080b6475640c5b359d2f5b9de5d577f59a46
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922535"
---
# <a name="idiasegmentgetread"></a>IDiaSegment::get_read
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ein Flag, das angibt, ob das Segment gelesen werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_read (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt `TRUE` , wenn das Segment gelesen werden kann; andernfalls `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)



