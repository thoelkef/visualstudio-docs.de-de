---
title: JsSetProjectionEnqueueCallback-Funktion | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c751ccef-20d2-4d41-9568-1c54adf47cdf
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8abdc575c5066ade4a700a0c88e09e3476a65366
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="jssetprojectionenqueuecallback-function"></a>JsSetProjectionEnqueueCallback-Funktion
Legt den Rückruf fest, der verwendet werden soll, um einen Projektionsabschluss zurück im vom Aufrufer benötigten Thread aufzurufen.  
  
## <a name="syntax"></a>Syntax  
  
```  
STDAPI_(JsErrorCode) JsSetProjectionEnqueueCallback(  
   _In_ JsProjectionEnqueueCallback projectionEnqueueCallback,  
   _In_opt_ void *projectionEnqueueContext);  
  
```  
  
#### <a name="parameters"></a>Parameter  
 `projectionEnqueueContext`  
 Der Rückruf, der jedes Mal aufgerufen wird, wenn der Abschluss einer Projektion in einem Hintergrundthread auftritt.  
  
 `callbackState`  
 Der Anwendungskontext, der `projectionEnqueueContext` bereitgestellt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Code `JsNoError` , wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Erfordert einen Active Script-Kontext.  
  
 Der Aufruf sollte aus einem anderen COM-Apartment oder einem anderen Thread in derselben MTA stammen.  
  
 Diese API wird nur im Edge-Modus unterstützt.  
  
> [!CAUTION]
>  PInvoke wird derzeit für diese API nicht unterstützt.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)