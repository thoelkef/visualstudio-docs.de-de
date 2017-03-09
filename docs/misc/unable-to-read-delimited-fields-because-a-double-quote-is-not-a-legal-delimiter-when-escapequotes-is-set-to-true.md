---
title: "Fehler beim Lesen von Feldern mit Trennzeichen. Doppelte Anf&#252;hrungszeichen sind kein zul&#228;ssiges Trennzeichen, wenn „EscapeQuotes“ auf „True“ festgelegt ist. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrTextFieldParser_IllegalDelimiter"
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Fehler beim Lesen von Feldern mit Trennzeichen. Doppelte Anf&#252;hrungszeichen sind kein zul&#228;ssiges Trennzeichen, wenn „EscapeQuotes“ auf „True“ festgelegt ist.
Der `TextFieldParser` kann nicht aus der Datei lesen, weil ein Anführungszeichen \("\) als Trennzeichen angegeben wurde und `EscapeQuotes` auf `True` festgelegt ist.  
  
### So beheben Sie diesen Fehler  
  
-   Legen Sie `EscapeQuotes` auf `False` fest.  
  
## Siehe auch  
 [TextFieldParser.SetDelimiters\-Methode](http://msdn.microsoft.com/de-de/21fa40ec-5866-4d0e-9fd9-c708a190dcc9)   
 [TextFieldParser.Delimiters\-Eigenschaft](http://msdn.microsoft.com/de-de/4eb18f4d-3011-40a9-b668-be93eed0444f)   
 [How to: Read From Comma\-Delimited Text Files](../Topic/How%20to:%20Read%20From%20Comma-Delimited%20Text%20Files%20in%20Visual%20Basic.md)   
 [TextFieldParser Object](/dotnet/visual-basic/language-reference/objects/textfieldparser-object)