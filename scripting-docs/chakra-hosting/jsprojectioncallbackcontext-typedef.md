---
title: JsProjectionCallbackContext-TypeDef | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 50c705c5-664f-4a1a-92f6-4882fc718ab1
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7548dc14ab4b3dddc1633a1ba948aba564d8438a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568420"
---
# <a name="jsprojectioncallbackcontext-typedef"></a>JsProjectionCallbackContext Typedef
Der von JsRT an den Anwendungsrückruf (JsProjectionEnqueueCallback) übergebene Kontext, der anschließend von der Anwendung im korrekten Thread im angegebenen Rückruf (`JsProjectionCallback`) zurück an JsRT übergeben wird.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef void *JsProjectionCallbackContext;  
```  
  
## <a name="remarks"></a>Hinweise  
 Erfordert das Aufrufen von `JsSetProjectionEnqueueCallback` , um Rückrufe zu empfangen.  
  
 Diese API wird nur im Edge-Modus unterstützt.  
  
## <a name="requirements"></a>Anforderungen  
 jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)