---
title: 'Idiaenumsegments:: Next | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Next method
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 965e226d4d3cfef563ee8237b96734e4d620ae42
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009738"
---
# <a name="idiaenumsegmentsnext"></a>IDiaEnumSegments::Next
Ruft eine angegebene Anzahl von Segmenten in der Enumerationsfolge ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT Next (   
   ULONG         celt,   
   IDiaSegment** rgelt,  
   ULONG*        pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 celt  
 [in] Die Anzahl der Segmente im Enumerator abgerufen werden sollen.  
  
 rgelt  
 [out] Ein Array, das mit den gewünschten gefüllt werden soll, im [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) Objekte, die die Segmente darstellen.  
  
 pceltFetched  
 [out] Gibt die Anzahl der Segmente in der abgerufenen Enumerator zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` Wenn keine weiteren Segmente mehr vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)