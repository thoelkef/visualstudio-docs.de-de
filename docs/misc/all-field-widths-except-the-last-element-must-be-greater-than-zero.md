---
title: "Alle Feldbreiten (au&#223;er beim letzten Element) m&#252;ssen gr&#246;&#223;er als 0 (null) sein. | Microsoft Docs"
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
  - "vbrTextFieldParser_FieldWidthsMustPositive"
ms.assetid: 41d8c661-a749-4c89-be56-905c6e7c3c9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Alle Feldbreiten (au&#223;er beim letzten Element) m&#252;ssen gr&#246;&#223;er als 0 (null) sein.
Alle Feldbreiten \(außer beim letzten Element\) müssen größer als 0 \(null\) sein. Ein Feld mit einer Breite unter oder gleich 0 \(null\) im letzten Element bedeutet, dass die Länge des letzten Felds variabel ist.  
  
 Der Vorgang ist fehlgeschlagen, da die Feldbreite eines anderen Elements, das nicht das letzte Element ist, auf 0 \(null\) oder kleiner festgelegt ist. Eine Feldbreite, die kleiner oder gleich 0 \(null\) ist, kann als letztes Element verwendet werden, um anzugeben, dass dass die Länge des letzten Felds variabel ist. Sie kann jedoch nicht als ein anderes Element verwendet werden.  
  
### So beheben Sie diesen Fehler  
  
-   Legen Sie die Feldbreite auf die richtige Länge fest.  
  
## Siehe auch  
 [TextFieldParser.SetFieldWidths\-Methode](http://msdn.microsoft.com/de-de/958fed9f-e0f3-4fc5-83b4-386156bdf036)   
 [TextFieldParser.FieldWidths\-Eigenschaft](http://msdn.microsoft.com/de-de/c6985360-60c6-494e-89e7-43b6b73f2597)   
 [How to: Read From Fixed\-width Text Files](../Topic/How%20to:%20Read%20From%20Fixed-width%20Text%20Files%20in%20Visual%20Basic.md)   
 [TextFieldParser Object](/dotnet/visual-basic/language-reference/objects/textfieldparser-object)