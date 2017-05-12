---
title: "IDebugDocumentHelper::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.Attach
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::Attach"
ms.assetid: 834f23a9-716d-44df-b23c-d1bf6da60e79
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::Attach
Fügt dieses Dokument der Dokumentstruktur hinzu.  
  
## Syntax  
  
```  
HRESULT Attach(  
   IDebugDocumentHelper*  pddhParent  
);  
```  
  
#### Parameter  
 `pddhParent`  
 \[in\] Die Dokumentstruktur, in der dieses Dokument hinzugefügt wird.  Kann NULL sein.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode fügt dieses Dokument der Dokumentstruktur, mit `pddhParent` als übergeordnetes Element hinzu.  Wenn `pddhParent``NULL` ist, ist dieses Dokument das Dokument der obersten Ebene.  
  
## Siehe auch  
 [IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)   
 [IDebugDocumentHelper\-Schnittstelle](../../winscript/reference/idebugdocumenthelper-interface.md)