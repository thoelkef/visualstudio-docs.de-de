---
title: JsPromiseContinuationCallback-TypeDef | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 51a3fd02-9668-4cf7-bb0b-e1fd03b2528f
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 762391cb66e5298bd70beb3238720d3717554ae0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568600"
---
# <a name="jspromisecontinuationcallback-typedef"></a>JsPromiseContinuationCallback-Typedef
Ein Zusagefortsetzungsrückruf.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef void (CALLBACK *JsPromiseContinuationCallback)(  
  _In_ JsValueRef task,  
  _In_opt_ void *callbackState  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `task`  
  `callbackState`  
  
## <a name="remarks"></a>Hinweise  
 Der Host kann einen Zusagefortsetzungsrückruf in `JsSetPromiseContinuationCallback`angeben. Wenn ein Skript eine Aufgabe erstellt, die zu einem späteren Zeitpunkt ausgeführt wird, wird der Zusagefortsetzungsrückruf mit der Aufgabe aufgerufen, und die Aufgabe sollte in eine FIFO-Warteschlange verschoben und ausgeführt werden, wenn die Ausführung des aktuellen Skripts abgeschlossen ist.  
  
 Diese API wird nur im Edge-Modus unterstützt.  
  
## <a name="requirements"></a>Anforderungen  
 jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)