---
title: JsRef-TypeDef | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 6aafc39f-6b9c-457f-8bf0-48831bffe9b8
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9d4c478a45f53e83dfa59fdde21cfa4c988c92e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="jsref-typedef"></a>JsRef-TypeDef
Ein Verweis auf ein Objekt, dessen Besitzer der Chakra-Garbage-Collector ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef void *JsRef;  
```  
  
## <a name="remarks"></a>Hinweise  
 Eine Chakra-Laufzeit überwacht automatisch JsRef-Verweise, sofern sie in lokalen Variablen oder in Parametern gespeichert sind (d. h im Stapel). Das Speichern eines JsRef an einem anderen Ort als im Stapel erfordert das Aufrufen von JsAddRef und JsRelease, um die Lebensdauer des Objekts zu verwalten; andernfalls kann der Garbage Collector das Objekt freigeben, während es noch verwendet wird.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)