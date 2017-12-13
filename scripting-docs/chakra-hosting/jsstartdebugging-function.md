---
title: JsStartDebugging-Funktion | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsStartDebugging
helpviewer_keywords: JsStartDebugging function
ms.assetid: c48ba02d-6d47-466f-a970-02f087d525f3
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd9b7e3deb407d1a1e9d16db38e17c85ccc8c797
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="jsstartdebugging-function"></a>JsStartDebugging-Funktion
Startet das Debuggen im aktuellen Kontext.  
  
## <a name="syntax"></a>Syntax  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsStartDebugging();  
  
// Legacy mode signature  
STDAPI_(JsErrorCode)  JsStartDebugging(  
   _In_ IDebugApplication *debugApplication  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `debugApplication`  
 Die Debuganwendung, die zum Debuggen verwendet werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 Der Code `JsNoError` , wenn der Vorgang erfolgreich war, andernfalls ein Fehlercode.  
  
## <a name="remarks"></a>Hinweise  
 Der Host muss sicherstellen, dass `CoInitializeEx` mindestens einmal mit `COINIT_MULTITHREADED` oder `COINIT_APARTMENTTHREADED` aufgerufen wird, bevor diese API verwendet wird.  
  
 Der `debugApplication`-Parameter wird im Edgemodus nicht unterstützt. Weitere Informationen zur Verwendung dieser API im Edgemodus finden Sie unter [Ansteuern des Edgemodus im Vergleich zu. Legacy-Moduls](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md).  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** jsrt.h  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz (JavaScript-Laufzeit)](../chakra-hosting/reference-javascript-runtime.md)