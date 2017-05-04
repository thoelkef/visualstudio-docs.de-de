---
title: "IJsDebugFrame::GetDocumentPositionWithId-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetDocumentPositionWithId
apilocation: jscript9diag.dll
ms.assetid: 48f8eb26-8ae4-4d5c-bd94-796023b03bcb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::GetDocumentPositionWithId-Methode
Gibt die aktuelle Position dieses Stapelrahmens innerhalb des Dokuments auf Benutzerebene zurück.  
  
## Syntax  
  
```  
HRESULT GetDocumentPositionWithId(  
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
 [IJsDebugFrame\-Schnittstelle](../../winscript/reference/ijsdebugframe-interface.md)