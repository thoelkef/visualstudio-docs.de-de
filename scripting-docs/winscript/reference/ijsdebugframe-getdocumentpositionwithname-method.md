---
title: "IJsDebugFrame::GetDocumentPositionWithName-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetDocumentPositionWithName
apilocation: jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::GetDocumentPositionWithName-Methode
Gibt die aktuelle Position dieses Stapelrahmens innerhalb des Dokuments auf Benutzerebene zurück.  
  
## Syntax  
  
```  
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### Parameter  
 `pDocumentName`  
 \[out\] Für statische Skripts, eine zu dokumentieren URL.  Für dynamische Skripts wird ein Name, der den Typ des Skripts enthält \(beispielsweise Auswertungscode, Funktionscode, usw.\) zurückgegeben.  
  
 `pLine`  
 \[out\] 1\-basierende Zeilenposition innerhalb des Dokuments.  
  
 `pColumn`  
 \[out\] 1\-basierende Zeilenposition innerhalb des Dokuments.  
  
## Rückgabewert  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [IJsDebugFrame\-Schnittstelle](../../winscript/reference/ijsdebugframe-interface.md)