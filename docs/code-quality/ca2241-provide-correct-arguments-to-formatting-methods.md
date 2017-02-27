---
title: "CA2241: Geeignete Argumente f&#252;r Formatierungsmethoden angeben | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2241"
  - "Provide correct arguments to formatting methods"
  - "ProvideCorrectArgumentsToFormattingMethods"
helpviewer_keywords: 
  - "CA2241"
  - "ProvideCorrectArgumentsToFormattingMethods"
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# CA2241: Geeignete Argumente f&#252;r Formatierungsmethoden angeben
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ProvideCorrectArgumentsToFormattingMethods|  
|CheckId|CA2241|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Das `format`\-Zeichenfolgenargument, das an eine Methode wie <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> oder <xref:System.String.Format%2A?displayProperty=fullName> übergeben wurde, enthält kein Formatelement, das den einzelnen Objektargumenten entspricht, oder umgekehrt.  
  
## Regelbeschreibung  
 Die Argumente für Methoden wie <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> und <xref:System.String.Format%2A> bestehen aus einer Formatzeichenfolge gefolgt von mehreren <xref:System.Object?displayProperty=fullName>\-Instanzen.  Die Formatzeichenfolge besteht aus Text und eingebetteten Formatelementen der Form {Index\[,Ausrichtung\]\[:formatZeichenfolge\]}. "der Indizes ist eine nullbasierte ganze Zahl, die angibt, welche der Objekte zum Format.  Wenn es für ein Objekt in der Formatzeichenfolge keinen entsprechenden Index gibt, wird das Objekt ignoriert.  Wenn das durch "Index" angegebene Objekt nicht existiert, wird zur Laufzeit eine <xref:System.FormatException?displayProperty=fullName> ausgelöst.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, geben Sie für jedes Objektargument ein Formatelement an, und geben Sie für jedes Formatelement ein Objektargument an.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel werden zwei Verstöße gegen diese Regel veranschaulicht.  
  
 [!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
 [!code-cs[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]