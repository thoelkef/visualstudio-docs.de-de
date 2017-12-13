---
title: JsIdle-Funktion | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsIdle
helpviewer_keywords: JsIdle function
ms.assetid: 372d1c62-8e19-4886-aa33-364cabc09bba
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ddffd4f37c0e10985a2dbca26558d8a94b21b2f7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="jsidle-function"></a>JsIdle-Funktion
Weist die Laufzeit an, jegliche notwendige Leerlaufverarbeitung auszuführen.  
  
## <a name="syntax"></a>Syntax  
  
```  
STDAPI_(JsErrorCode) JsIdle(  
   _Out_opt_ unsigned int *nextIdleTick  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `nextIdleTick`  
 Der nächste Systemtick, bei dem mehr Leerlaufaufgaben anfallen. Kann NULL sein. Gibt die maximale Anzahl von Ticks zurück, wenn keine Leerlaufaufgaben anstehen.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Code `JsNoError` , wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Wenn die Leerlaufverarbeitung für die aktuelle Laufzeit aktiviert wurde, wird die aktuelle Laufzeit durch Aufrufen von `JsIdle` informiert, dass der Host im Leerlauf ist und dass die Laufzeit Arbeitsspeicher-Bereinigungsaufgaben ausführen kann.  
  
 `JsIdle` kann auch die Anzahl von Ticks zurückgeben, nach der wieder mehr Leerlaufaufgaben für die Laufzeit anstehen. Das Aufrufen von `JsIdle`, bevor diese Anzahl von Ticks verstrichen ist, hat keine Auswirkungen.  
  
 Erfordert einen Active Script-Kontext.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)