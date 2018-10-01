---
title: 'Idiaenumsegments:: Item | Microsoft-Dokumentation'
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
- IDiaEnumSegments::Item method
ms.assetid: ee44dd55-39a0-4b7b-97ff-2e1226eeb2bd
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb635e9d78ffce143b23ee7d93540f41af745a25
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523026"
---
# <a name="idiaenumsegmentsitem"></a>IDiaEnumSegments::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [idiaenumsegments:: Item](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumsegments-item).  
  
Ruft ein Segment mithilfe eines Indexes ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Item (   
   DWORD         index,  
   IDiaSegment** segment  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 Index  
 [in] Der Index der [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) Objekt abgerufen werden sollen. Der Index befindet sich im Bereich von 0 bis `count`-1 und, in dem `count` wird zurückgegeben, durch die [idiaenumsegments:: Get_count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md) Methode.  
  
 Segment  
 [out] Gibt eine [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) Objekt, das das gewünschte Segment darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)



