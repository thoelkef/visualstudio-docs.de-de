---
title: "Der Attributkonstruktor hat einen ByRef-Parameter vom Typ &lt;Typname&gt;. Zum Anwenden des Attributs k&#246;nnen keine Konstruktoren mit byref-Parametern verwendet werden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc36006"
  - "vbc36006"
helpviewer_keywords: 
  - "BC36006"
ms.assetid: 4c4e991f-3839-4196-bcfb-eb8464aa55e5
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Attributkonstruktor hat einen ByRef-Parameter vom Typ &lt;Typname&gt;. Zum Anwenden des Attributs k&#246;nnen keine Konstruktoren mit byref-Parametern verwendet werden.
Auf ein Programmierelement wurde ein Attribut unter Verwendung eines Attributkonstruktors mit einem `ByRef`\-Parameter angewendet.  
  
 Attribute werden zur Kompilierzeit angewendet, und der Compiler benötigt konkrete Werte für die Übergabe an den Attributkonstruktor. Ein `ByRef`\-Parameter nimmt einen Zeiger auf einen Wert an, der zur Kompilierzeit nicht ausgewertet werden kann.  
  
 Sie können einen Attributkonstruktor definieren, der einen `ByRef`\-Parameter annimmt, und diesen für Zwecke wie z. B. das Erben verwenden. Wenn Sie das Attribut jedoch anwenden, müssen Sie einen Konstruktor verwenden, der keine `ByRef` Parameter annimmt.  
  
 **Fehler\-ID:** BC36006  
  
### So beheben Sie diesen Fehler  
  
-   Wenden Sie das Attribut mit einem Konstruktor an, der keine `ByRef`\-Parameter annimmt, oder wenden Sie das Attribut nicht an.  
  
## Siehe auch  
 [NICHT IM BUILD: Übersicht über Attribute in Visual Basic](http://msdn.microsoft.com/de-de/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [NICHT IM BUILD: Anwendung von Attributen](http://msdn.microsoft.com/de-de/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [ByRef](/dotnet/visual-basic/language-reference/modifiers/byref)