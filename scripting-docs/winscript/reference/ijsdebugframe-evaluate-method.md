---
title: "IJsDebugFrame::Evaluate-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.Evaluate
apilocation: jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::Evaluate-Methode
Werten Sie einen Ausdruck im Kontext dieses Stapelrahmens aus.  
  
## Syntax  
  
```  
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### Parameter  
 `pExpressionText`  
 \[in\] Der auszuwertende Ausdruck.  
  
 `ppDebugProperty`  
 \[out\] Objekt, das den Eigenschaftenbrowser darstellt.  
  
 `pError`  
 \[out\] Die Fehlermeldung, wenn ein Fehler auftritt.  
  
## Rückgabewert  
  
## Hinweise  
 Gibt Folgendes zurück: "S\_OK": Auswertung folgt, "\*ppDebugProperty" enthält Auswertungsergebnis.  "S\_FALSE": Auswertung löst einen Fehler aus \(oder der Auswertungsvorgang wird nicht unterstützt\), "\*pError" enthält die Fehlermeldung.  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [IJsDebugFrame\-Schnittstelle](../../winscript/reference/ijsdebugframe-interface.md)