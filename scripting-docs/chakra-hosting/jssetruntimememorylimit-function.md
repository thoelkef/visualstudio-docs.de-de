---
title: JsSetRuntimeMemoryLimit-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsSetRuntimeMemoryLimit
helpviewer_keywords:
- JsSetRuntimeMemoryLimit function
ms.assetid: 74feb31f-19f6-43e3-b117-0694c59ac593
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 587eb369e6971c7527177624ccf5baf839246cf9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568970"
---
# <a name="jssetruntimememorylimit-function"></a>JsSetRuntimeMemoryLimit-Funktion
Legt das aktuelle Arbeitsspeicherlimit für eine Laufzeit fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
STDAPI_(JsErrorCode) JsSetRuntimeMemoryLimit(  
   _In_ JsRuntimeHandle runtime,  
   _In_ size_t memoryLimit  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `runtime`  
 Die Laufzeit, deren Arbeitsspeicherlimit festgelegt werden soll.  
  
 `memoryLimit`  
 Das neue Laufzeit-Arbeitsspeicherlimit in Bytes oder –1 für kein Arbeitsspeicherlimit.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Code `JsNoError` , wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Ein Arbeitsspeicherlimit führt dazu, dass jeder Vorgang, der das Limit überschreitet, mit einem Fehler aufgrund von ungenügendem Arbeitsspeicher fehlschlägt. Das Festlegen des Arbeitsspeicherlimits einer Laufzeit auf –1 bedeutet, dass die Laufzeit kein Arbeitsspeicherlimit aufweist. Neue Laufzeiten weisen standardmäßig keine Arbeitsspeicherlimits auf. Wenn das neue Arbeitsspeicherlimit über der aktuellen Auslastung liegt, wird der Aufruf erfolgreich ausgeführt, und alle zukünftigen Speicherbelegungen in dieser Laufzeit schlagen fehl, bis die Speicherauslastung der Laufzeit wieder unter dem Limit liegt.  
  
 Das Arbeitsspeicherlimit einer Laufzeit kann immer festgelegt werden, unabhängig davon, ob die Laufzeit in einem anderen Thread aktiv ist.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)