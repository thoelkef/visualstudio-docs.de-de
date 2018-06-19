---
title: JsThreadServiceCallback-TypeDef | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: dbe67be5-418a-4f66-8b68-b38078a6d140
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c4b7ea4d0d5eaba17269a1777cdf96b5a2a5cda3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568770"
---
# <a name="jsthreadservicecallback-typedef"></a>JsThreadServiceCallback-TypeDef
Ein Threaddienstrückruf.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef bool (CALLBACK *JsThreadServiceCallback)(  
   _In_ JsBackgroundWorkItemCallback callback,  
   _In_opt_ void *callbackData  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 callback  
 Der Rückruf für die Hintergrundaufgabe.  
  
 callbackData  
 Das an den Rückruf übergebene Datenargument.  
  
## <a name="remarks"></a>Hinweise  
 Der Host kann einen Hintergrundthreaddienst angeben, wenn er "JsCreateRuntime" aufruft. Sofern angegeben, werden Hintergrundaufgaben mit diesem Rückruf an den Host übergeben. Der Host soll die Ausführung der Hintergrundaufgaben sofort beginnen und TRUE oder FALSE zurückgeben, und die Laufzeit verarbeitet das Arbeitselement im Thread.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)