---
title: "IDebugDocumentTextEvents::onUpdateDocumentAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextEvents.onUpdateDocumentAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentTextEvents::onUpdateDocumentAttributes"
ms.assetid: 48fa909c-14c2-4ca4-af86-a5809c72dd39
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextEvents::onUpdateDocumentAttributes
Gibt an, dass die Dokumentenattribute geändert haben.  
  
## Syntax  
  
```  
HRESULT onUpdateDocumentAttributes(  
   TEXT_DOC_ATTR  textdocattr  
);  
```  
  
#### Parameter  
 `textdocattr`  
 \[in\] Die Attribute des neuen Dokuments.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode gibt an, dass die Dokumentenattribute geändert haben.  
  
## Siehe auch  
 [IDebugDocumentTextEvents\-Schnittstelle](../../winscript/reference/idebugdocumenttextevents-interface.md)   
 [TEXT\_DOC\_ATTR\-Konstanten](../../winscript/reference/text-doc-attr-constants.md)