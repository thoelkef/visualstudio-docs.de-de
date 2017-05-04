---
title: "IJsDebugBreakPoint::GetDocumentPosition-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebugBreakPoint.GetDocumentPosition
apilocation: jscript9diag.dll
ms.assetid: 886df8ba-a59a-48a7-87f2-3b669e71528f
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugBreakPoint::GetDocumentPosition-Methode
Gibt die Position der Anweisung zurück, wo der Haltepunkt gebunden wurde.  
  
## Syntax  
  
```  
HRESULT GetDocumentPosition(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### Parameter  
 `pDocumentId`  
 \[out\] Eindeutige ID für ein Quelldokument \(Zeiger auf "IDebugDocumentText"\).  
  
 `pCharacterOffset`  
 \[out\] Das nullbasierte Zeichenoffset vom Anfang des Skripts.  
  
 `pStatementCharCount`  
 \[out\] Die Länge der aktuellen Anweisung, die am "\*pCharacterOffset" beginnt, in Zeichen.  
  
## Rückgabewert  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [IJsDebugBreakPoint\-Schnittstelle](../../winscript/reference/ijsdebugbreakpoint-interface.md)