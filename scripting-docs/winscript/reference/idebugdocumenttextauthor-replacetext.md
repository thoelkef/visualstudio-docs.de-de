---
title: "IDebugDocumentTextAuthor::ReplaceText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextAuthor.ReplaceText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentTextAuthor::ReplaceText"
ms.assetid: f89304e6-5be0-45a5-947d-2c59c3c0a05e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextAuthor::ReplaceText
Ersetzt Text im Dokument.  
  
## Syntax  
  
```  
HRESULT ReplaceText(  
   ULONG    cCharacterPosition,  
   ULONG    cNumToReplace,  
   OLECHAR  pcharText[]  
);  
```  
  
#### Parameter  
 `cCharacterPosition`  
 \[in\] starten Sie Speicherort des Zeichenbereichs, um zu ersetzen.  
  
 `cNumToReplace`  
 \[in\] Zahl Zeichen zu ersetzen.  
  
 `pcharText[]`  
 \[in\] Ein Puffer, der die neuen Zeichen enthält, um die alten Zeichen zu ersetzen.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode ersetzt Text im Dokument.  
  
## Siehe auch  
 [IDebugDocumentTextAuthor\-Schnittstelle](../../winscript/reference/idebugdocumenttextauthor-interface.md)