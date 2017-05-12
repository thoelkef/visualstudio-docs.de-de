---
title: "IDebugDocumentText::GetLineOfPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetLineOfPosition
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetLineOfPosition"
ms.assetid: fe8d4802-ea16-49ca-8973-89dcaf6c915b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetLineOfPosition
Gibt die Zeilennummer und optional den Zeichenoffset innerhalb der Zeile zurück, die der angegebenen Zeichenposition entspricht.  
  
## Syntax  
  
```  
HRESULT GetLineOfPosition(  
   ULONG   cCharacterPosition,  
   ULONG*  pcLineNumber,  
   ULONG*  pcCharacterOffsetInLine  
);  
```  
  
#### Parameter  
 `cCharacterPosition`  
 \[in\] Startposition des Zeichenpositionsbereichs.  
  
 `pcLineNumber`  
 \[out\] Die Zeilennummer des Bereichs.  
  
 `pcCharacterOffsetInLine`  
 \[in, out\] der Zeichenoffset des Bereichs innerhalb der Zeile `pcLineNumber`.  Wenn dieser Parameter `NULL` ist, gibt die Methode keinen Wert zurück.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode gibt die Zeilennummer und optional den Zeichenoffset innerhalb der Zeile zurück, die der angegebenen Zeichenposition entspricht.  
  
## Siehe auch  
 [IDebugDocumentText\-Schnittstelle](../../winscript/reference/idebugdocumenttext-interface.md)