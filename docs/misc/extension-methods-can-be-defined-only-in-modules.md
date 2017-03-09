---
title: "Erweiterungsmethoden k&#246;nnen nur in Modulen definiert werden. | Microsoft Docs"
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
  - "vbc36551"
  - "bc36551"
helpviewer_keywords: 
  - "BC36551"
ms.assetid: c832d523-5bf6-4baf-b91c-bd26d94453ed
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Erweiterungsmethoden k&#246;nnen nur in Modulen definiert werden.
Dieser Fehler tritt auf, wenn eine Erweiterungsmethode außerhalb eines Moduls definiert wurde. In Visual Basic müssen alle Erweiterungsmethoden innerhalb von Standardmodulen definiert werden.  
  
 **Fehler\-ID:** BC36551  
  
### So beheben Sie diesen Fehler  
  
-   Platzieren Sie die Erweiterungsmethode in einem Modul.  
  
## Beispiel  
 Im folgenden Beispiel wird die `String`\-Klasse durch Hinzufügen einer `Print`\-Methode erweitert.  
  
```  
Imports StringUtility Imports System.Runtime.CompilerServices Namespace StringUtility <Extension()> _ Module StringExtensions <Extension()> _ Public Sub Print (ByVal str As String) Console.WriteLine(str) End Sub End Module End Namespace  
```  
  
## Siehe auch  
 [NICHT IM BUILD: Anwendung von Attributen](http://msdn.microsoft.com/de-de/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Erweiterungsmethoden](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Module \<keyword\>](../Topic/Module%20%3Ckeyword%3E%20\(Visual%20Basic\).md)   
 [Module Statement](/dotnet/visual-basic/language-reference/statements/module-statement)