---
title: JsGetAndClearException-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsGetAndClearException
helpviewer_keywords:
- JsGetAndClearException function
ms.assetid: 6aec8a88-41ee-47f6-b5f4-32f3cae6bb7b
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e7e4f89bac59aa776762586ab20fa831b5c24bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568110"
---
# <a name="jsgetandclearexception-function"></a>JsGetAndClearException-Funktion
Gibt die Ausnahme zurück, durch die die Laufzeit des aktuellen Kontexts in den Ausnahmezustand versetzt wurde, und setzt den Ausnahmezustand für diese Laufzeit zurück.  
  
## <a name="syntax"></a>Syntax  
  
```  
STDAPI_(JsErrorCode) JsGetAndClearException(  
   _Out_ JsValueRef *exception  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `exception`  
 Die Ausnahme für die Laufzeit des aktuellen Kontexts.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Code `JsNoError` , wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Wenn die Laufzeit des aktuellen Kontexts keinen Ausnahmezustand aufweist, gibt diese API `JsErrorInvalidArgument` zurück. Wenn die Laufzeit deaktiviert ist, wird eine Ausnahme zurückgegeben, die angibt, dass das Skript beendet wurde. Die Ausnahme wird jedoch nicht gelöscht (die Ausnahme wird gelöscht, wenn die Laufzeit mit `JsEnableRuntimeExecution` wieder aktiviert wird).  
  
 Erfordert einen Active Script-Kontext.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)