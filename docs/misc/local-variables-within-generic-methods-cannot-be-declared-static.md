---
title: "Lokale Variablen innerhalb generischer Methoden k&#246;nnen nicht als &quot;Static&quot; deklariert werden | Microsoft Docs"
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
  - "vbc32068"
  - "bc32068"
helpviewer_keywords: 
  - "BC32068"
ms.assetid: cb5df484-76f9-4092-9d19-f26ddcf1c035
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Lokale Variablen innerhalb generischer Methoden k&#246;nnen nicht als &quot;Static&quot; deklariert werden
In der Deklaration einer lokalen Variablen in einer generischen Prozedur wird `Static` angegeben.  
  
 Visual Basic und .NET Framework unterstützen derzeit keine Kombination von statischen Variablen und generischen Prozeduren.  
  
 **Fehler\-ID:** BC32068  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das `Static`\-Schlüsselwort aus der Variablendeklaration.  
  
## Siehe auch  
 [Static](/dotnet/visual-basic/language-reference/modifiers/static)   
 [NOTINBUILD: Gewusst wie: Erhöhen der Lebensdauer einer Variablen](http://msdn.microsoft.com/de-de/04e7c56c-1db0-4fe5-a678-859a39ec654b)   
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)