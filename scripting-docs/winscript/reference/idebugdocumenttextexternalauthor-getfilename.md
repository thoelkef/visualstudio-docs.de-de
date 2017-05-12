---
title: "IDebugDocumentTextExternalAuthor::GetFileName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextExternalAuthor.GetFileName
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentTextExternalAuthor::GetFileName"
ms.assetid: 87acdce6-acb2-4936-80dd-d624bb7dbd42
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextExternalAuthor::GetFileName
Gibt den Namen des Dokuments ohne Pfadinformationen zurück.  
  
## Syntax  
  
```  
HRESULT GetFileName(  
   BSTR*  pbstrShortName  
);  
```  
  
#### Parameter  
 `pbstrShortName`  
 \[out\] können Sie die mit Kurznamenformat des Dokuments auf.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode gibt den Namen des Dokuments ohne Pfadinformationen zurück.  Der kurze wird in der Regel in Dialogfeldern verwendet.  
  
## Siehe auch  
 [IDebugDocumentTextExternalAuthor\-Schnittstelle](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)