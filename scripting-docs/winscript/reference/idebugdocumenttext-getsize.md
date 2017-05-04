---
title: "IDebugDocumentText::GetSize | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetSize
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetSize"
ms.assetid: 9da53856-613a-44b2-a84c-99454a2a1548
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetSize
Gibt die Anzahl der Zeilen und die Anzahl der Zeichen im Dokument zurück.  
  
## Syntax  
  
```  
HRESULT GetSize(  
   ULONG*  pcNumLines,  
   ULONG*  pcNumChars  
);  
```  
  
#### Parameter  
 `pcNumLines`  
 \[out\] Anzahl von Zeilen im Dokument.  Wenn dieser Parameter NULL ist, gibt die Methode keinen Wert zurück.  
  
 `pcNumChars`  
 \[out\] Anzahl von Zeichen im Dokument.  Wenn dieser Parameter NULL ist, gibt die Methode keinen Wert zurück.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode gibt die Anzahl der Zeilen und die Anzahl der Zeichen im Dokument zurück.  
  
## Siehe auch  
 [IDebugDocumentText\-Schnittstelle](../../winscript/reference/idebugdocumenttext-interface.md)