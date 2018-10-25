---
title: 'Idiaenumsegments:: Item | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Item method
ms.assetid: ee44dd55-39a0-4b7b-97ff-2e1226eeb2bd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 19d42e8bb2cdf950043b6a60a0db82706cf582ac
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896405"
---
# <a name="idiaenumsegmentsitem"></a>IDiaEnumSegments::Item
Ruft ein Segment mithilfe eines Indexes ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
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