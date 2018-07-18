---
title: JsNativeFunction-TypeDef | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 56ef6cdf-4ca9-4f7c-b953-e661addb1a8e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33cf475dd6a17434ea132647b7d8bde833f0de9e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568080"
---
# <a name="jsnativefunction-typedef"></a>JsNativeFunction-TypeDef
Ein Funktionsrückruf.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef _Ret_maybenull_ JsValueRef (CALLBACK * JsNativeFunction)(  
   _In_ JsValueRef callee,  
   _In_ bool isConstructCall,  
   _In_ JsValueRef *arguments,  
   _In_ unsigned short argumentCount  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 Aufgerufener  
 Ein `Function`-Objekt, das die aufgerufene Funktion darstellt.  
  
 isConstructCall  
 Gibt an, ob dies ein regulärer Aufruf oder ein "neuer" Aufruf ist.  
  
 arguments  
 Die Argumente für den Aufruf.  
  
 argumentCount  
 Die Anzahl der Argumente.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Das Ergebnis des Aufrufs, falls vorhanden.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)