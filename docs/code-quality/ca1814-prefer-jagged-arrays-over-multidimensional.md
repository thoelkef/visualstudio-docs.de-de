---
title: "CA1814: Verzweigte Arrays mehrdimensionalen Arrays vorziehen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PreferJaggedArraysOverMultidimensional"
  - "CA1814"
helpviewer_keywords: 
  - "CA1814"
  - "PreferJaggedArraysOverMultidimensional"
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1814: Verzweigte Arrays mehrdimensionalen Arrays vorziehen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PreferJaggedArraysOverMultidimensional|  
|CheckId|CA1814|  
|Kategorie \(Category\)|Microsoft.Performance|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein Member ist als mehrdimensionales Array deklariert.  
  
## Regelbeschreibung  
 Ein verzweigtes Array ist ein Array, dessen Elemente wiederum Arrays sind.  Die Arrays, die die Elemente bilden, können unterschiedliche Größen haben, was bei einigen Gruppen von Daten dazu führt, dass weniger Speicherplatz vergeudet wird.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu korrigieren, ändern Sie das mehrdimensionale Array in ein verzweigtes Array.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel, wenn das mehrdimensionale Array nicht zu viel Platz beansprucht.  
  
## Beispiel  
 Im folgenden Beispiel werden Deklarationen für verzweigte und mehrdimensionale Arrays veranschaulicht.  
  
 [!code-vb[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/VisualBasic/ca1814-prefer-jagged-arrays-over-multidimensional_1.vb)]
 [!code-cs[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/CSharp/ca1814-prefer-jagged-arrays-over-multidimensional_1.cs)]