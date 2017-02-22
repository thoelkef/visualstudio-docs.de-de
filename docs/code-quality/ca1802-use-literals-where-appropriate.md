---
title: "CA1802: Nach M&#246;glichkeit Literale verwenden | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseLiteralsWhereAppropriate"
  - "CA1802"
helpviewer_keywords: 
  - "UseLiteralsWhereAppropriate"
  - "CA1802"
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1802: Nach M&#246;glichkeit Literale verwenden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseLiteralsWhereAppropriate|  
|CheckId|CA1802|  
|Kategorie \(Category\)|Microsoft.Performance|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Feld wird als `static` und `readonly` deklariert \(`Shared` und `ReadOnly` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) und mit einem Wert initialisiert, der zur Kompilierungszeit berechnet werden kann.  
  
## Regelbeschreibung  
 Der Wert eines `static` `readonly`\-Felds wird zur Laufzeit berechnet, wenn der statische Konstruktor für den deklarierenden Typ aufgerufen wird.  Wenn das `static` `readonly`\-Feld zum Zeitpunkt des Deklarierens initialisiert wird und kein statischer Konstruktor explizit deklariert wird, gibt der Compiler einen statischen Konstruktor zum Initialisieren des Felds aus.  
  
 Der Wert eines `const`\-Felds wird zur Kompilierungszeit berechnet und in den Metadaten gespeichert. Dadurch wird beim Vergleich mit einem `static` `readonly`\-Feld die Laufzeitleistung gesteigert.  
  
 Da der dem verwendeten Feld zugewiesene Wert zur Kompilierungszeit berechnet werden kann, ändern Sie die Deklaration in ein `const`\-Feld, sodass der Wert statt zur Laufzeit zur Kompilierungszeit berechnet wird.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie den `static`\-Modifizierer und den `readonly`\-Modifizierer durch den `const`\-Modifizierer.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, bzw. die Regel kann deaktiviert werden, wenn das Leistungsverhalten nicht von Belang ist.  
  
## Beispiel  
 Das folgende Beispiel zeigt einen Typ, `UseReadOnly`, der gegen die Regel verstößt, und einen Typ `UseConstant`, der der Regel entspricht.  
  
 [!code-vb[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/VisualBasic/ca1802-use-literals-where-appropriate_1.vb)]
 [!code-cs[FxCop.Performance.UseLiterals#1](../code-quality/codesnippet/CSharp/ca1802-use-literals-where-appropriate_1.cs)]