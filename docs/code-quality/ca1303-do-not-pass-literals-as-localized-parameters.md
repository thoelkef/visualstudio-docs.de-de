---
title: "CA1303: Literale nicht als lokalisierte Parameter &#252;bergeben | Microsoft Docs"
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
  - "Do not pass literals as localized parameters"
  - "DoNotPassLiteralsAsLocalizedParameters"
  - "CA1303"
helpviewer_keywords: 
  - "CA1303"
  - "DoNotPassLiteralsAsLocalizedParameters"
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1303: Literale nicht als lokalisierte Parameter &#252;bergeben
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotPassLiteralsAsLocalizedParameters|  
|CheckId|CA1303|  
|Kategorie \(Category\)|Microsoft.Globalization|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine Methode übergibt ein Zeichenfolgenliteral als Parameter an einen Konstruktor oder eine Methode in der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Klassenbibliothek, und diese Zeichenfolge sollte lokalisierbar sein.  
  
 Diese Warnung wird ausgelöst, wenn eine Literalzeichenfolge als Wert an einen Parameter oder eine Eigenschaft übergeben wird und mindestens einer der folgenden Fälle wahr ist:  
  
-   Das <xref:System.ComponentModel.LocalizableAttribute>\-Attribut des Parameters oder der Eigenschaft ist auf "true" festgelegt.  
  
-   Der Parameter oder Eigenschaftenname enthält "Text", "Meldung" oder "Beschriftung".  
  
-   Der Name des Zeichenfolgenparameters, der an eine Console.Write\-Methode oder eine Console.WriteLine\-Methode übergeben wird, ist entweder "Wert" oder "Format".  
  
## Regelbeschreibung  
 Zeichenfolgenliterale, die in Quellcode eingebettet werden, sind schwierig zu lokalisieren.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie das Zeichenfolgenliteral durch eine Zeichenfolge, die durch eine Instanz der <xref:System.Resources.ResourceManager>\-Klasse abgerufen wird.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn die Codebibliothek nicht lokalisiert wird oder wenn die Zeichenfolge dem Endbenutzer bzw. einem Entwickler nicht über die Codebibliothek zur Verfügung gestellt wird.  
  
 Die Benutzer können Störungen für Methoden beseitigen, an die keine lokalisierten Zeichenfolgen übergeben werden sollten, indem sie den Parameter oder die Eigenschaft umbenennen oder indem sie diese Elemente als bedingt kennzeichnen.  
  
## Beispiel  
 Das folgende Beispiel zeigt eine Methode, die eine Ausnahme auslöst, wenn eines ihrer beiden Argumente außerhalb des Bereichs liegt.  Beim ersten Argument wird an den Ausnahmekonstruktor eine Literalzeichenfolge übergeben, die gegen diese Regel verstößt.  Beim zweiten Argument wird an den Konstruktor ordnungsgemäß eine durch <xref:System.Resources.ResourceManager> abgerufene Zeichenfolge übergeben.  
  
 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
 [!code-cs[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]  
  
## Siehe auch  
 [Ressourcen in Desktop\-Apps](../Topic/Resources%20in%20Desktop%20Apps.md)