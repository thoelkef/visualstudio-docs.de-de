---
title: JsProjectionCallback-TypeDef | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 32f22d37-e57e-4196-b6cd-a3fc75bd0632
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 80d1c64f04f44a8560c25935fba2a48905a73260
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568250"
---
# <a name="jsprojectioncallback-typedef"></a>JsProjectionCallback Typedef
Der aufzurufende JsRT-Rückruf mit an `JsProjectionEnqueueCallback` übergebenem Kontext im richtigen Thread.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef void (CALLBACK *JsProjectionCallback)(  
  _In_ JsProjectionCallbackContext jsContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `jsContext`  
 Erfordert das Aufrufen von `JsSetProjectionEnqueueCallback` , um Rückrufe zu empfangen.  
  
## <a name="remarks"></a>Hinweise  
 Diese API wird nur im Edge-Modus unterstützt.  
  
## <a name="requirements"></a>Anforderungen  
 jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)