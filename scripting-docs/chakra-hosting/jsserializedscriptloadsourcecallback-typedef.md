---
title: JsSerializedScriptLoadSourceCallback-TypeDef | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9406c488-76ac-49e5-b305-39751f3412ea
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ff3bc206cf3779023a13166f30e8f4f719e7ebe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="jsserializedscriptloadsourcecallback-typedef"></a>JsSerializedScriptLoadSourceCallback-Typedef
Von der Laufzeit zum Laden des Quellcodes des serialisierten Skripts aufgerufen.     Der Aufrufer muss den Skriptpuffer bis `JsSerializedScriptUnloadCallback`gültig halten.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef bool (CALLBACK * JsSerializedScriptLoadSourceCallback)(  
  _In_ JsSourceContextsourceContext,  
  _Outptr_result_z_ const wchar_t** scriptBuffer  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `sourceContext`  
 Der an `JsParseSerializedScriptWithCallback` oder `JsRunSerializedScriptWithCallback`übergebene Kontext.  
  
 `scriptBuffer`  
 Das zurückgegebene Skript.  
  
## <a name="remarks"></a>Hinweise  
  
> [!WARNING]
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)