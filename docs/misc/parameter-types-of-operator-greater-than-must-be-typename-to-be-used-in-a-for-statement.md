---
title: "Parametertypen von &#39;&lt;Operator&gt;&#39; m&#252;ssen &#39;&lt;Typname&gt;&#39; sein, damit sie in einer For-Anweisung verwendet werden k&#246;nnen. | Microsoft Docs"
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
  - "BC33040"
  - "vbc33040"
helpviewer_keywords: 
  - "BC33040"
ms.assetid: bffbb812-0d69-47e4-96c5-01882722ccdb
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Parametertypen von &#39;&lt;Operator&gt;&#39; m&#252;ssen &#39;&lt;Typname&gt;&#39; sein, damit sie in einer For-Anweisung verwendet werden k&#246;nnen.
Eine `For`\-Schleife gibt eine Indikatorvariable eines Typs an, der den `>=`\- oder `<=`\-Operator nicht mit Parametern des eigenen Typs definiert.  
  
 Die Indikatorvariable muss einen Typ aufweisen, der die Operatoren „größer\-oder\-gleich“ \(`>=`\) und „kleiner\-oder\-gleich“ \(`<=`\) unterstützt, die ihren enthaltenen Typ vergleichen. Dies bedeutet, dass beide Operanden den Typ der Indikatorvariablen aufweisen müssen.  
  
 Wenn Sie für die Indikatorvariable einen numerischen Datentyp verwenden, werden die Operatoren `>=` und `<=` für den enthaltenen Typ unterstützt. Wenn Sie eine benutzerdefinierte Klasse oder Struktur verwenden, müssen Sie beide Operatoren mit Operanden vom Typ der Klasse oder Struktur definieren.  
  
 **Fehler\-ID:** BC33040  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass der Datentyp der Indikatorvariablen richtig geschrieben ist.  
  
2.  Wenn Sie für die Indikatorvariable eine benutzerdefinierte Klasse oder Struktur verwenden, definieren Sie die Operatoren `>=` und `<=`, die diese Klasse oder Struktur vergleichen.  
  
## Siehe auch  
 [For...Next\-Anweisung](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [Operator Procedures](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator Statement](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)