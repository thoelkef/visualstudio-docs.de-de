---
title: "IDebugDocumentProvider::GetDocument | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentProvider.GetDocument
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentProvider::GetDocument"
ms.assetid: da67dab0-778a-4dab-8ca3-055ee7a4f141
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentProvider::GetDocument
Veranlasst das Dokument instanziiert werden, wenn es nicht bereits vorhanden ist.  
  
## Syntax  
  
```  
HRESULT GetDocument(  
   IDebugDocument**  ppssd  
);  
```  
  
#### Parameter  
 `ppssd`  
 \[out\] Die Debug\- Dokument entsprechend dem Dokument.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode wird das Dokument instanziiert werden, wenn sie nicht bereits vorhanden ist.  
  
## Siehe auch  
 [IDebugDocumentProvider\-Schnittstelle](../../winscript/reference/idebugdocumentprovider-interface.md)