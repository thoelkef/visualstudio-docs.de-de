---
title: JsSerializeScript-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- jsrt/JsSerializeScript
helpviewer_keywords:
- JsSerializeScript function
ms.assetid: ca42c194-e1c1-407d-b542-b9d494e3ac4e
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 92bc6c1de0f2cd43dfe9566413fb64188fd5a382
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24568870"
---
# <a name="jsserializescript-function"></a>JsSerializeScript-Funktion
Serialisiert ein analysiertes Skript in einen Puffer, der wiederverwendet werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
STDAPI_(JsErrorCode) JsSerializeScript(  
   _In_z_ const wchar_t *script,  
   _Out_writes_to_opt_(*bufferSize,  
   *bufferSize) BYTE *buffer,  
   _Inout_ unsigned long *bufferSize  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `script`  
 Das zu serialisierende Skript.  
  
 `buffer`  
 Der Puffer für das serialisierte Skript. Kann NULL sein.  
  
 `bufferSize`  
 Beim Eintritt ist dies die Größe des Puffers in Byte; beim Austritt ist dies die Größe des Puffers in Byte, die nötig ist, um das serialisierte Skript aufzunehmen.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Code `JsNoError` , wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 `JsSerializeScript` analysiert ein Skript und speichert dann das analysierte Formular des Skripts in einem laufzeitunabhängigen Format. Das serialisierte Skript kann anschließend in jeder Laufzeit deserialisiert werden, ohne dass das Skript erneut analysiert werden muss.  
  
 Erfordert einen Active Script-Kontext.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)