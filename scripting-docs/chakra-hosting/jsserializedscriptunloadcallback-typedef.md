---
title: JsSerializedScriptUnloadCallback-Typdef | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d18c392-cca0-411e-9f2b-0d788b16161a
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f485d31367f189231d354c653c8e58cc8656eb9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="jsserializedscriptunloadcallback-typedef"></a>JsSerializedScriptUnloadCallback-Typdef
Wird von der Laufzeit aufgerufen, wenn sie mit allen Ressourcen fertig ist, die sich auf die Skriptausführung beziehen.     Der Aufrufer muss die Quelle (sofern geladen), den Bytecode und den Kontext zu diesem Zeitpunkt freigeben.  
  
## <a name="syntax"></a>Syntax  
  
```  
 typedef void (CALLBACK * JsSerializedScriptUnloadCallback)(  
  _In_ JsSourceContext sourceContext  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `sourceContext`  
 Der an `JsParseSerializedScriptWithCallback` oder `JsRunSerializedScriptWithCallback`übergebene Kontext.  
  
## <a name="remarks"></a>Hinweise  
  
> [!WARNING]
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)