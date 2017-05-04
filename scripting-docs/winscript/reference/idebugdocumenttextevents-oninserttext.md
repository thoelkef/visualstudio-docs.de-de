---
title: "IDebugDocumentTextEvents::onInsertText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextEvents.onInsertText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentTextEvents::onInsertText"
ms.assetid: 775881de-497a-47a9-86ab-823d77745a72
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextEvents::onInsertText
Gibt an, dass neuer Text zum Dokument hinzugefügt wurde.  
  
## Syntax  
  
```  
HRESULT onInsertText(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToInsert  
);  
```  
  
#### Parameter  
 `cCharacterPosition`  
 \[in\] Die Zeichenposition, in der der neue Text eingefügt wurde.  
  
 `cNumToInsert`  
 \[in\] Die Anzahl von Zeichen, die eingefügt wurden.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode wird in der Regel von einem Host, der nach und nach Inhalt lädt, wie ein Webbrowser bezeichnet.  
  
## Siehe auch  
 [IDebugDocumentTextEvents\-Schnittstelle](../../winscript/reference/idebugdocumenttextevents-interface.md)   
 [IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)