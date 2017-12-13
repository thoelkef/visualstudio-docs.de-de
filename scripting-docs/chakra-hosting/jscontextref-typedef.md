---
title: JsContextRef-TypeDef | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8586bfcc-bb24-430d-a6f2-1a3b3e34ec2e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec1300717b59c3b901665b39ca0102988e83e853
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="jscontextref-typedef"></a>JsContextRef-TypeDef
Ein Verweis auf einen Skriptkontext.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef JsRef JsContextRef;  
```  
  
## <a name="remarks"></a>Hinweise  
 Jeder Skriptkontext enthält ein eigenes globales Objekt, das sich vom globalen Objekt in anderen Skriptkontexten unterscheidet.  
  
 Viele Chakra-Hosting-APIs erfordern einen "aktiven" Skriptkontext, der mit `JsSetCurrentContext` festgelegt werden kann. Bei Chakra-Hosting-APIs, die einen aktuellen Kontext erfordern, wird in der Dokumentation explizit darauf hingewiesen.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)