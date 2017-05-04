---
title: "IDebugDocumentHelper::GetDebugApplicationNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.GetDebugApplicationNode
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::GetDebugApplicationNode"
ms.assetid: ecd18803-beb4-4ac2-9702-cc9e8a12c395
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::GetDebugApplicationNode
Gibt den Debug\- Anwendungsknoten entsprechend diesem Dokument zurück.  
  
## Syntax  
  
```  
HRESULT GetDebugApplicationNode(  
   IDebugApplicationNode**  ppdan  
);  
```  
  
#### Parameter  
 `ppdan`  
 \[out\] Der Debug\- Anwendungsknoten entsprechend diesem Dokument.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Geben Sie den Debug\- Anwendungsknoten entsprechend diesem Dokument zurück.  
  
## Siehe auch  
 [IDebugDocumentHelper\-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)