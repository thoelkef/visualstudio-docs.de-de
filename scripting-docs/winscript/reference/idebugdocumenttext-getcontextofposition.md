---
title: "IDebugDocumentText::GetContextOfPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetContextOfPosition
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetContextOfPosition"
ms.assetid: 86560853-d9b1-499a-a1b5-ea06aa1f1f5c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetContextOfPosition
Erstellt ein Dokumentenkontextobjekt entsprechend dem angegebenen Zeichenpositionsbereich.  
  
## Syntax  
  
```  
HRESULT GetContextOfPosition(  
   ULONG                    cCharacterPosition,  
   ULONG                    cNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### Parameter  
 `cCharacterPosition`  
 \[in\] Startposition des Zeichenpositionsbereichs.  
  
 `cNumChars`  
 \[in\] Anzahl von Zeichen im Bereich.  
  
 `ppsc`  
 \[out\] Das Dokumentenkontextobjekt gemäß dem angegebenen Zeichenpositionsbereich.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode erstellt ein Dokumentenkontextobjekt entsprechend dem angegebenen Zeichenpositionsbereich.  
  
## Siehe auch  
 [IDebugDocumentText\-Schnittstelle](../../winscript/reference/idebugdocumenttext-interface.md)