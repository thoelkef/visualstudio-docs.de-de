---
title: "IDebugDocumentTextExternalAuthor::NotifyChanged | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextExternalAuthor.NotifyChanged
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentTextExternalAuthor::NotifyChanged"
ms.assetid: f0de7984-3a15-49e2-bd29-f768f34d2a4d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextExternalAuthor::NotifyChanged
Benachrichtigt den Host, dass die Dokumentenquelle geändert hat.  
  
## Syntax  
  
```  
HRESULT NotifyChanged();  
```  
  
#### Parameter  
 Diese Methode verwendet keine Parameter.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode wird von einem externen Editor aufgerufen, nachdem ein dateibasiertes Debuggerdokument geändert und gespeichert wurde, um den Host zu benachrichtigen, dass die Dokumentenquelle geändert hat.  Der Host aktualisiert dann das Dokument von der Quelldatei.  
  
## Siehe auch  
 [IDebugDocumentTextExternalAuthor\-Schnittstelle](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)