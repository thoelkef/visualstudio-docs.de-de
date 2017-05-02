---
title: "IDebugDocumentContext::GetDocument | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentContext.GetDocument
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentContext::GetDocument"
ms.assetid: 32db2fea-4938-4644-b39a-8fae05960d1d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentContext::GetDocument
Gibt das Dokument zurück, das diesen Kontext enthält.  
  
## Syntax  
  
```  
HRESULT GetDocument(  
   IDebugDocument**  ppsd  
);  
```  
  
#### Parameter  
 `ppsd`  
 \[out\] Das Dokument, das diesen Kontext enthält.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Die `GetDocument`\-Methode gibt das Dokument zurück, das diesen Kontext enthält.  
  
## Siehe auch  
 [IDebugDocumentContext\-Schnittstelle](../../winscript/reference/idebugdocumentcontext-interface.md)