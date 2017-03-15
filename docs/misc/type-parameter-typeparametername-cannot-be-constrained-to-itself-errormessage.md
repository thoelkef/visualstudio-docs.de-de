---
title: "Typparameter &lt;Typparametername&gt; kann nicht auf sich selbst beschr&#228;nkt werden: &lt;Fehlermeldung&gt;. | Microsoft Docs"
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
  - "bc32113"
  - "vbc32113"
helpviewer_keywords: 
  - "BC32113"
ms.assetid: a74128ae-11d0-46bf-8c0b-c7a2bf881d17
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Typparameter &lt;Typparametername&gt; kann nicht auf sich selbst beschr&#228;nkt werden: &lt;Fehlermeldung&gt;.
Eine Einschränkungsliste für einen Typparameter enthält den Typparameter selbst.  
  
 Eine Einschränkungsliste für einen Typparameter kann eine beliebige Anzahl von Schnittstellen und höchstens eine Klasse angegeben. Ein für diesen Typparameter angegebenes Typargument muss jede angegebene Schnittstelle implementieren und von der angegebenen Klasse erben. Wenn der Compiler auf eine Einschränkungsliste trifft, benötigt er bereits definierte Schnittstellen und Klassen. Ein Typparameter wird erst dann als definierter Typ betrachtet, wenn er durch ein geeignetes Typargument ersetzt wird, das vom Code bereitgestellt wird, der den generische Typ erstellt.  
  
 **Fehler\-ID:** BC32113  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die Schreibweise des Typparameters und der Einschränkungen in seiner Einschränkungsliste.  
  
2.  Wenn keine Rechtschreibfehler vorhanden sind, entfernen Sie den Namen des Typparameters aus seiner Einschränkungsliste. Er kann nicht auf sich selbst beschränkt werden.  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)