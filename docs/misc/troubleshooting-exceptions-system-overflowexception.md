---
title: "Problembehandlung bei Ausnahmen: System.OverflowException | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "OverflowException-Klasse"
ms.assetid: bd380db7-5d05-4d7f-be5b-e654fdadf14c
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.OverflowException
Eine <xref:System.OverflowException>\-Ausnahme wird ausgelöst, wenn ein arithmetischer, ein Umwandlungs\- oder ein Konvertierungsvorgang in einem aktivierten Kontext zu einem Überlauf führt. Ein Überlauf tritt auf, wenn bei einer Operation ein Wert entsteht, der zu groß für den Zieltyp ist, unendlich entspricht oder keine Zahl ist \(Not a Number, NaN\).  
  
## Tipps  
 **Beim Umwandeln aus einer Zahl muss der Wert eine Zahl sein, die kleiner als unendlich ist.**  
 Ein Quellwert darf nicht unendlich sein, und er muss eine gültige Zahl sein.  
  
 **Dividieren Sie nicht durch 0.**  
 Diese Ausnahme wird normalerweise ausgelöst, wenn eine Division durch 0 durchgeführt wird.  
  
## Hinweise  
 In Sprachen, die einen Überlauf erkennen, wird beim Auftreten eines Überlaufs die Ausnahme <xref:System.OverflowException> ausgelöst. Zum Beispiel wird in C\# das `checked`\-Schlüsselwort verwendet, um Überlaufbedingungen zu erkennen. Eine <xref:System.OverflowException>\-Ausnahme tritt nur in einem aktivierten Kontext auf.  
  
 Bei einem Ergebnis aus einer arithmetischen Operation mit ganzzahligen Typen oder Dezimaltypen oder aus einer Konvertierung, das einen Wert außerhalb des Zieltypbereichs ergibt:  
  
-   In einem aktivierten Kontext tritt ein Kompilierungsfehler auf, wenn die Operation ein konstanter Ausdruck ist. Andernfalls wird, wenn die Operation zur Laufzeit ausgeführt wird, eine <xref:System.OverflowException>\-Ausnahme ausgelöst.  
  
-   In einem nicht aktivierten Kontext wird das Ergebnis gekürzt, indem alle höherwertigen Bits verworfen werden, die nicht in den Zieltyp passen.  
  
 Informationen zu den Wertbereichen von Datentypen finden Sie unter [Data Types](/dotnet/visual-basic/language-reference/data-types/data-type-summary), [Tabelle ganzzahliger Typen](/dotnet/csharp/language-reference/keywords/integral-types-table) oder [Tabelle für Gleitkommatypen](/dotnet/csharp/language-reference/keywords/floating-point-types-table).  
  
## Siehe auch  
 <xref:System.OverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)