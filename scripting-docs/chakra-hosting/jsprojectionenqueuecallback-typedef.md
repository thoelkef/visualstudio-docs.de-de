---
title: JsProjectionEnqueueCallback-TypeDef| Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 19c1cefb-a7be-4196-b780-9fe6adf35ba5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bda4a3a80edac38ab2c3885c2256cdf9d03eb8c1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568310"
---
# <a name="jsprojectionenqueuecallback-typedef"></a>JsProjectionEnqueueCallback Typedef
Der Rückruf der Anwendung, der von JsRT aufgerufen wird, wenn eine projizierte API in einem anderen als dem ursprünglichen Thread abgeschlossen wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef void (CALLBACK *JsProjectionEnqueueCallback)(  
  _In_ JsProjectionCallback jsCallback,  
  _In_ JsProjectionCallbackContext jsContext,  
  _In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `jsCallback`  
 Der Rückruf, der für den ursprünglichen Thread aufgerufen wird.  
  
 `jsContext`  
 Der Anwendungskontext.  
  
 `callbackState`  
 Der JsRT-Kontext, der an `jsCallback`übergeben werden muss.  
  
## <a name="remarks"></a>Hinweise  
 Erfordert den Aufruf von JsSetProjectionEnqueueCallback, um Rückrufe empfangen zu können.  
  
 Diese API wird nur im Edge-Modus unterstützt.  
  
## <a name="requirements"></a>Anforderungen  
 jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)