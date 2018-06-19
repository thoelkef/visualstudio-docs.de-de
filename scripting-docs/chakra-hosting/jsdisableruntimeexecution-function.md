---
title: JsDisableRuntimeExecution-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsDisableRuntimeExecution
helpviewer_keywords:
- JsDisableRuntimeExecution function
ms.assetid: 4bd4670a-a9da-4f8c-b3fd-1fd366d915c3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f44545f7c81344a2d22f0083087f77ac8074278c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568270"
---
# <a name="jsdisableruntimeexecution-function"></a>JsDisableRuntimeExecution-Funktion
Hält die Skriptausführung an und beendet alle ausgeführten Skripts in einer Laufzeit.  
  
## <a name="syntax"></a>Syntax  
  
```  
STDAPI_(JsErrorCode) JsDisableRuntimeExecution(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `runtime`  
 Die anzuhaltende Laufzeit.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Code `JsNoError` , wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Aufrufe an eine angehaltene Laufzeit schlagen fehl, bis `JsEnableRuntimeExecution` aufgerufen wird.  
  
 Diese API muss nicht in dem Thread aufgerufen werden, in dem die Laufzeit aktiv ist. Wenn die Laufzeit in einen angehaltenen Zustand versetzt wird, werden ausgeführte Skripts möglicherweise nicht sofort angehalten. Aktive Skripts wird so schnell wie möglich mit einer "Nicht abfangbar"-Ausnahme beendet.  
  
 Das Anhalten der Ausführung in einer Laufzeit, die bereits angehalten ist, ist nicht möglich.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)