---
title: JsNumberToInt-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 8b9256d6-76ac-4c74-a97c-fbb16c13f5f5
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f24acb837fdf46694aa2370e2ccf1fe3c926ce19
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568430"
---
# <a name="jsnumbertoint-function"></a>JsNumberToInt-Funktion
Ruft den `int`-Wert eines Zahlenwerts ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
STDAPI_(JsErrorCode) JsNumberToInt(  
      _In_ JsValueRef value,  
      _Out_ int *intValue  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `value`  
 Der Zahlenwert, der in einen `int`-Wert konvertiert werden soll.  
  
 `intValue`  
 Der `int`-Wert.  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="remarks"></a>Hinweise  
 Diese Funktion ruft den Wert eines Zahlenwerts ab und konvertiert ihn in einen `int`-Wert. Sie schlägt mit `JsErrorInvalidArgument` fehl, wenn der Typ des Werts nicht "Zahl" ist.  
  
 Erfordert einen Active Script-Kontext.  
  
 Diese API wird nur im Edge-Modus unterstützt.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)