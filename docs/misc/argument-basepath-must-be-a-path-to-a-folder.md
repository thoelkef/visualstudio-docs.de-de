---
title: "Das BasePath-Argument muss ein Pfad zu einem Ordner sein. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b180ce60-ad57-41a6-a313-491d86d84cc7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das BasePath-Argument muss ein Pfad zu einem Ordner sein.
Das `BasePath`\-Argument muss aus einen Pfad zu einem Ordner bestehen. Möglicherweise analysieren Sie eine Zeichenfolge nicht ordnungsgemäß und stellen einen Wert bereit, der nicht als gültiger Pfad erkannt wird.  
  
### So beheben Sie diesen Fehler  
  
-   Überprüfen Sie den für `BasePath` bereitgestellten Wert, um sicherzustellen, dass es sich um einen gültigen Pfad zu einem Ordner handelt.  
  
## Siehe auch  
 <xref:System.CodeDom.Compiler.TempFileCollection.BasePath%2A>   
 <xref:System.Resources.ResXResourceWriter.BasePath%2A>   
 <xref:System.Resources.ResXResourceReader.BasePath%2A>   
 [Gewusst wie: Analysieren von Dateipfaden](../Topic/How%20to:%20Parse%20File%20Paths%20in%20Visual%20Basic.md)