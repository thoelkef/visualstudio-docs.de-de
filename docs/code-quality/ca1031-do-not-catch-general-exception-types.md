---
title: "CA1031: Allgemeine Ausnahmetypen nicht auffangen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1031"
  - "DoNotCatchGeneralExceptionTypes"
helpviewer_keywords: 
  - "CA1031"
  - "DoNotCatchGeneralExceptionTypes"
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 20
---
# CA1031: Allgemeine Ausnahmetypen nicht auffangen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotCatchGeneralExceptionTypes|  
|CheckId|CA1031|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Allgemeine Ausnahmen, z. B. <xref:System.Exception?displayProperty=fullName> oder <xref:System.SystemException?displayProperty=fullName>, werden in einer `catch`\-Anweisung oder mit einer allgemeinen catch\-Klausel abgefangen, z. B. `catch()`.  
  
## Regelbeschreibung  
 Allgemeine Ausnahmen sollten nicht abgefangen werden.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fangen Sie eine spezifischere Ausnahme ab oder lösen die allgemeine Ausnahme in der letzten Anweisung des `catch`\-Blocks erneut aus.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  Durch das Abfangen allgemeiner Ausnahmetypen können Laufzeitprobleme vor dem Bibliotheksbenutzer verborgen werden und das Debuggen kann schwieriger werden.  
  
> [!NOTE]
>  Ab [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)], stellt die Common Language Runtime \(CLR\) nicht mehr beschädigte Zustandsausnahmen zu, die im Betriebssystem und in verwaltetem Code, beispielsweise Zugriffsverletzungen in [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] auftreten, von verwaltetem Code behandelt werden.  Wenn Sie eine Anwendung in [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] oder höheren Versionen kompilieren und Behandlung von beschädigten Zustandsausnahmen beibehalten möchten, können Sie das <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>\-Attribut auf die Methode anwenden, die die beschädigte Zustandsausnahme behandelt.  
  
## Beispiel  
 Im folgenden Beispiel werden ein Typ, der gegen diese Regel verstößt, und ein Typ veranschaulicht, in dem der `catch`\-Block korrekt implementiert wurde.  
  
 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
 [!code-cs[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]  
  
## Verwandte Regeln  
 [CA2200: Erneut ausführen, um Stapeldetails beizubehalten](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)