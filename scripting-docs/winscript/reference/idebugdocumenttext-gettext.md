---
title: "IDebugDocumentText::GetText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentText.GetText
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentText::GetText"
ms.assetid: 3c940a30-6c0f-4deb-aa4d-21a0bdef8461
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText::GetText
Ruft die Zeichen und\/oder die Zeichenattribute ab, die einem Zeichenpositionsbereich zugeordnet werden.  
  
## Syntax  
  
```  
HRESULT GetText(  
   ULONG              cCharacterPosition,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### Parameter  
 `cCharacterPosition`  
 \[in\] Startposition des Zeichenpositionsbereichs.  
  
 `pcharText`  
 \[in, out\] a\-Zeichentextpuffer.  Der Puffer muss groß genug sein, `cMaxChars` Zeichen enthält.  Wenn dieser Parameter NULL ist, gibt die Methode keine Zeichen zurück.  
  
 `pstaTextAttr`  
 \[in, out\] a\-Zeichenattributpuffer.  Der Puffer muss groß genug sein, `cMaxChars` Zeichen enthält.  Wenn dieser Parameter NULL ist, gibt die Methode nicht Attribute zurück.  
  
 `pcNumChars`  
 \[out\] in, die Anzahl der Zeichen\/Attributen zurückgegeben.  Dieser Parameter muss auf\) festgelegt werden, bevor diese Methode aufruft.  
  
 `cMaxChars`  
 \[in\] Anzahl von Zeichen im Zeichenpositionsbereich.  Gibt auch die maximale Anzahl von Zeichen an, um zurückzukehren.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode ruft die Zeichen ab und\/oder reichen die Zeichenattribute, die einer Zeichenposition zugeordnet werden.  Der Zeichenpositionsbereich wird von einer Zeichenposition und von mehreren Zeichen angegeben.  
  
## Siehe auch  
 [IDebugDocumentText\-Schnittstelle](../../winscript/reference/idebugdocumenttext-interface.md)   
 [SOURCE\_TEXT\_ATTR\-Enumeration](../../winscript/reference/source-text-attr-enumeration.md)