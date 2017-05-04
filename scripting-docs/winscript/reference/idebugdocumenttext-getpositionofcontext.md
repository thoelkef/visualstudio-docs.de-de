---
title: "IDebugDocumentText::GetPositionOfContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetPositionOfContext
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetPositionOfContext"
ms.assetid: 90fec730-c3fb-45fb-92ef-05ecc90dca38
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetPositionOfContext
Gibt den Zeichenpositionsbereich entsprechend einem Dokumentenkontext zurück.  
  
## Syntax  
  
```  
HRESULT GetPositionOfContext(  
   IDebugDocumentContext*  psc,  
   ULONG*                  pcCharacterPosition,  
   ULONG*                  cNumChars  
);  
```  
  
#### Parameter  
 `psc`  
 \[in\] Das Dokumentenkontextobjekt.  
  
 `pcCharacterPosition`  
 \[out\] Startposition des Zeichenpositionsbereichs.  
  
 `cNumChars`  
 \[out\] Anzahl von Zeichen im Bereich.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Der Dokumentenkontext, der dieser Methode bereitgestellt wird, muss mit diesem Dokument zugeordnet werden.  
  
## Siehe auch  
 [IDebugDocumentText\-Schnittstelle](../../winscript/reference/idebugdocumenttext-interface.md)