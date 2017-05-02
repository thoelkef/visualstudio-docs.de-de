---
title: "IDebugDocumentTextEvents::onUpdateTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentTextEvents.onUpdateTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentTextEvents::onUpdateTextAttributes"
ms.assetid: 24a6d409-3137-4a7a-ac24-0955c109902f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextEvents::onUpdateTextAttributes
Gibt an, dass die Textattribute, die mit dem zugrunde liegenden Zeichenpositionsbereich zugeordnet werden, geändert wurden.  
  
## Syntax  
  
```  
HRESULT onUpdateTextAttributes(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToUpdate  
);  
```  
  
#### Parameter  
 `cCharacterPosition`  
 \[in\] Die Zeichenposition des ersten Zeichens, dass die Attribute geändert haben.  
  
 `cNumToUpdate`  
 \[in\] Die Anzahl von Zeichen im Bereich.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode gibt an, dass die Textattribute, die mit dem zugrunde liegenden Zeichenpositionsbereich zugeordnet werden, geändert wurden.  
  
## Siehe auch  
 [IDebugDocumentTextEvents\-Schnittstelle](../../winscript/reference/idebugdocumenttextevents-interface.md)